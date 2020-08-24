# How to code Unit-Testing : Unit Testの実装方法

Unit Test@2020

2020年時点の最新状況を加味して以下の構成を選定。
利用に際しての要点と簡単な実装方法を示す。

Category                | Name
:---                    |:---
Unit-Testing Framework  | [Catch2]
Mocking Library         | [Hippomocks]

[Catch2]:https://github.com/catchorg/Catch2
[Hippomocks]:https://github.com/dascandy/hippomocks


## サンプルを元にした簡単な説明

```cpp:Unit-Test Code
TEST_CASE( "vectors can be sized and resized", "[vector]" )
{
  // initialization block executed for each section
  std::vector<int> v( 5 );
  REQUIRE( v.size() == 5 );
  REQUIRE( v.capacity() >= 5 );
  // end of initialization block

  SECTION( "resizing bigger changes size and capacity" )
  {
    v.resize( 10 );

    REQUIRE( v.size() == 10 );
    REQUIRE( v.capacity() >= 10 );

    // verify that attempting to reserve a smaller capacity changes nothing
    SECTION( "reserving smaller again does not change capacity" )
    {
      v.reserve( 7 );
      REQUIRE( v.capacity() >= 10 );
    }
  }

  SECTION( "resizing smaller changes size but not capacity" )
  {
    v.resize( 0 );

    REQUIRE( v.size() == 0 );
    REQUIRE( v.capacity() >= 5 );
  }
}
```

[JetBrainsのサンプル情報]:https://pleiades.io/help/clion/unit-testing-tutorial.html#catch-framework
[Catch2 write BDD-Style]:http://www.electronvector.com/blog/using-catch-to-write-bdd-style-unit-tests-for-c
