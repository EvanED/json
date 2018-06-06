# Styled Pretty Printing

The library provides a pretty printer supporting flexible customization of the layout. There are two concepts used by the library:

* A _style_ defines how printed objects are formatted.
* A _stylizer_ determines what style to use, based on the current context being printed.

## Styles -- Uniform Formatting

If you want the entire document to be formatted the same, all you need to do is provide a single `nlohmann::print_style` instance to the `nlohmann::styled_dump` function. There are three “presets” you can use, `print_style::preset_compact()`, `print_style::preset_one_line()`, and `print_style::multiline()`:

    using nlohmann::json;
    using nlohmann::print_style;
    using nlohmann::styled_dump;
    
    json j = {"foo", 1, 2, 3, false, {{"one", 1}}}
        
    styled_dump(std::cout, j, print_style::preset_compact());
    // Result: ["foo",1,2,3,false,{"one":1}]
    
    styled_dump(std::cout, j, print_style::preset_one_line());
    // Result: ["foo", 1, 2, 3, false, {"one": 1}]

    styled_dump(std::cout, j, print_style::multiline());
    // Result (no comment symbols, of course):
    //[
    //    "foo",
    //    1,
    //    2,
    //    3,
    //    false,
    //    {
    //        "one": 1
    //    }
    //]

In addition, 
