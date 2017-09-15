---
title: Tables Concepts
order: 1
topic_order: 2
tutorial_title: Tables
first_published: "September 2014"
wcag_success_criteria:
  - 1.3.1
type: intro
editors:
  - Eric Eggert: "https://www.w3.org/People/yatil/"
  - Shadi Abou-Zahra: "https://www.w3.org/People/shadi/"
contributors:
  - Anna Belle Leiserson
  - Shawn Lawton Henry: https://www.w3.org/People/Shawn/
  - Sharron Rush
  - the Web Content Accessibility Guidelines Working Group (<a href="https://www.w3.org/WAI/GL/">WCAG WG</a>)
  - the Education and Outreach Working Group (<a href="https://www.w3.org/WAI/EO/">EOWG</a>)
support: Developed with support from the <a href="https://www.w3.org/WAI/ACT/">WAI-ACT project</a>, co-funded by the <strong>European Commission <abbr title="Information Society Technologies">IST</abbr> Programme</strong>.
---

Data tables are used to organize data with a logical relationship in grids. Accessible tables need HTML markup that indicates header cells and data cells and defines their relationship. Assistive technologies use this information to provide context to users.

Header cells must be marked up with `<th>`, and data cells with `<td>` to make tables accessible. For more complex tables, explicit associations may be needed using `scope`, `id`, and `headers` attributes.

This tutorial shows you how to apply appropriate structural markup to tables. It includes the following pages:

-   **[Tables with one header![](img-simple.png)](one-header.html)** for rows or columns: For tables with content that is easy to distinguish, mark up header cells with `<th>` and data cells with `<td>` elements.

-   **[Tables with two headers![](img-multidir.png)](two-headers.html)** have a simple row header and a simple column header: For tables with unclear header directions, define the direction of each header by setting the `scope` attribute to `col` or `row`.

-   **[Tables with irregular headers![](img-irreg.png)](irregular.html)** have header cells that span multiple columns and/or rows: For these tables, define column and row groups and set the range of the header cells using the `colgroup` and `rowgroup` values of the scope attribute.

-   **[Tables with multi-level headers![](img-multi.png)](multi-level.html)**  have multiple header cells associated per data cell:  For tables that are so complex that header cells can’t be associated in a strictly horizontal or vertical way, use `id` and `headers` attributes to associate header and data cells explicitly.

-   **[Caption & Summary![](img-caption.png)](caption-summary.html):** A caption identifies the overall topic of a table and is useful in most situations. A summary provides orientation or navigation hints in complex tables.
{:.withicons.nobullets}

Some document formats other than HTML, such as PDF, provide similar mechanisms to markup table structures. Word processing applications may also provide mechanisms to markup tables. Tables markup is often lost when converting from one format to another, though some programs may provide functionality to assist converting table markup.

Many web authoring tools and content management systems (CMS) provide functions to define header cells during table creation without having to edit the code manually.

{::nomarkdown}
<%= notes_start %>
{:/nomarkdown}

**Notes:** This tutorial provides guidance for creating tables used to display data in a grid. This tutorial does not apply to tables used for layout. As a general rule, tables aren't meant to be used for layout purposes. Instead, a best practice is to use Cascading Style Sheets (CSS) for visual presentation.

{::nomarkdown}
<%= notes_end %>
{:/nomarkdown}

## Why is this important?

Tables without structural markup to differentiate and properly link between header and data cells, create accessibility barriers. Relying on visual cues alone is not sufficient to create an accessible table. With structural markup, headers and data cells can be programmatically determined by software, which means that:

-   **People using screen readers** can have the row and column headers read aloud as they navigate through the table. Screen readers speak one cell at a time and reference the associated header cells, so the reader doesn’t lose context.

-    **Some people use alternative ways to render the data**, for example by using custom stylesheets to display header cells more prominently. Techniques like this enable them to change text size and colors and display the information as lists rather than grids. The table code needs to be properly structured to allow alternative renderings.
