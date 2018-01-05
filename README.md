# vijual

Vijual is a graph layout engine conceptually similar to graphviz. However, it uses different layout algorithms, creating graphs with a different aesthetic. Vijual uses specialized algorithms for optimal rendering of trees, binary trees, directed, and undirected graphs. Also, it has robust abilities for generating attractive ASCII graphs (as well as traditional bitmap graphs) making it well suited for debugging and exploratory programming directly from the Clojure REPL. Vijual is still an alpha-grade project at this time- Expect many improvements and changes to this library in the near future.

## Usage

Via leiningen:

```
[stathissideris/vijual "0.2.0-SNAPSHOT"]
```

### Examples

```clojure
> (draw-tree [[:north-america [:usa [:miami] [:seattle] [:idaho [:boise]]]]
              [:europe [:germany] [:france [:paris] [:lyon] [:cannes]]]])

        +------------+        +--------+
        |   north    |        | europe |
        |  america   |        +----+---+
        +------+-----+             |
               |         +---------+---------+
               +         |                   |
               |    +----+----+          +---+----+
            +--+--+ | germany |          | france |
            | usa | +---------+          +---+----+
            +--+--+                          |
               |                    +--------+---------+
    +----------+----------+         |        |         |
    |          |          |     +---+---+ +--+---+ +---+----+
+---+---+ +----+----+ +---+---+ | paris | | lyon | | cannes |
| miami | | seattle | | idaho | +-------+ +------+ +--------+
+-------+ +---------+ +---+---+
                          |
                          +
                          |
                      +---+---+
                      | boise |
                      +-------+
```


```clojure
> (draw-graph [[:a :b] [:b :c] [:c :d] [:a :d] [:e :f] [:a :f] [:g :e] [:d :e]])

+---+       +---+   +---+
| g |       | d |   |   |
|   |---+ +-|   |---| c |
|   |   | | |   |   |   |
+---+   | | +---+   |   |
        | |   |     |   |
+---+   | |   |     +---+
| f |   | |   |       |
|   |-+ | | +-----+   +-+
|   | | | | |  a  |     |
+---+ +-----|     |-+ +---+
  |     | | |     | | | b |
  |     | | +-----+ +-|   |
  |     | |           |   |
+-----+ | |           +---+
|     | | |
|  e  |-+ |
|     |   |
|     |---+
|     |
+-----+
```

## License

GPLv3
