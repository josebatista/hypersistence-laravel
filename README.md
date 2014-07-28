Hypersistence2.0
================

PHP Object Orented persistence framework.

-----------------------------------------

Use doc comment tags for mapping classes with database.

<h3>Example:</h3>

<pre>
<?php
/**
 * @table(person)
 */
class Person extends Hypersistence{
    
    /**
     * @primaryKey
     * @column(person_id)
     */
    private $id;
    
    /**
     * Use empty column when the column has the same name that var.
     * @column()
     */
    private $name;
    
    /**
     * When you have a Many to One relationship use tags as below.
     * You can use 'lazy' or 'eager'.
     * @manyToOne(lazy)
     * @column(city_id)
     * @itemClass(City)
     */
    private $city;
    
    /**
     * When you have a One to Many relationship use tags as below.
     * You can use 'lazy' or 'eager'.
     * @oneToMany(lazy)
     * @joinColumn(person_id)
     * @itemClass(Book)
     */
    private $books;
    
    /**
     * When you have a Many to Many relationship use tags as below.
     * You can use 'lazy' or 'eager'.
     * @manyToMany(lazy)
     * @joinColumn(person_id)
     * @inverseJoinColumn(course_id)
     * @itemClass(Course)
     * @joinTable(person_has_course)
     */
    private $courses;
    

    public function getId(){
        return $this->id;
    }
    
    public function setId($id){
        $this->id = $id;
    }
    
    public function getName(){
        return $this->name;
    }
    
    public function setName($name){
        $this->name = $name;
    }
    
    public function getCity(){
        return $this->city;
    }
    
    public function setCity($city){
        $this->city = $city;
    }
    
    public function getBooks(){
        return $this->books;
    }
    
    public function getCourses(){
        return $this->courses;
    }
}
?>
</pre>


<h3>Usage Example</h3>

<pre>
<?php
$p = new Person();
$p->setId(1);
$p->load();

echo $p->getName();
?>
</pre>
