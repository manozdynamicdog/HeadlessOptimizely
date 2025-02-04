---
title: "How to Retain Sort Order of Indexed Items in Episerver Find"
datePublished: Mon Feb 03 2025 14:30:59 GMT+0000 (Coordinated Universal Time)
cuid: cm6p5f20q002409lbc4fv1etk
slug: how-to-retain-sort-order-of-indexed-items-in-episerver-find
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/NHIZG5Ul8bA/upload/0b4575ab9a569cc544fd9e0d6174ab5e.jpeg
tags: cms, optimizely, episerver

---

This blog post addresses a common issue encountered when trying to maintain the sort order of items indexed in Episerver Find (now known as Search and Navigation).

**Scenario:**

Imagine you have a page with a content area. Due to specific business requirements, you need to fetch items from the Find index for this content area. However, when these items are indexed in Episerver Find, they lose their original sort order in the results. The challenge is to preserve the original sort order of these items as they appear in the content area.

in below code

```csharp
var parentPage = contentLoader.Get<ParentPageType>(new ContentReference(10), new CultureInfo("en"));

var result = IContentResult<BlockInParentPage> resultsFromFind;

var reportBlocksByReference = result.Items.ToDictionary(x => x.ContentLink);

var orderedBlocks = new List<BlockInParentPage>();

// Iterate over the FilteredItems to maintain the desired order
foreach (var contentRef in parentPage.ReportsArea.FilteredItems)
{
    // Check if the result contains the current content reference
    if (reportBlocksByReference.TryGetValue(contentRef.ContentLink, out var blockInParentPage))
    {
        // Add blockInParentPage to the list to maintain the original order
        orderedBlocks.Add(blockInParentPage);
    }
}

// Return or use orderedBlocks as needed
return orderedBlocks
```

1. **Retrieve Parent Page**: The code starts by using a content loader to fetch a parent page of a specific type (`ParentPageType`) using a content reference ID (`10`) and a specified culture (`en`).
    
2. **Fetch Search Results**: It then retrieves search results from Episerver Find, which are expected to be of type `BlockInParentPage`. These results are stored in a variable named `resultsFromFind`.
    
3. **Create Dictionary**: A dictionary is created from the search results, mapping each block's content link to the block itself. This allows for quick lookup of blocks by their content link.
    
4. **Initialize Ordered List**: An empty list named `orderedBlocks` is initialized to store the blocks in their original order as they appear in the content area.
    
5. **Iterate Over Filtered Items**: The code iterates over the `FilteredItems` collection of the `ReportsArea` in the parent page. This collection represents the items in the content area whose order needs to be preserved.
    
6. **Check for Matches**: For each content reference in the `FilteredItems`, the code checks if the content link exists in the dictionary created earlier. This determines if the block is present in the search results.
    
7. **Add to Ordered List**: If a match is found, the corresponding block is added to the `orderedBlocks` list. This ensures that the blocks are added in the same order as they appear in the content area.
    
8. **Return or Use Ordered List**: Finally, the `orderedBlocks` list, which now contains the blocks in the desired order, can be returned or used as needed to maintain the original sort order.
    

In conclusion, this approach effectively ensures that the items retrieved from the Episerver Find index are returned in the same order as they are arranged in the content area, meeting the business requirement of maintaining the original sort order.