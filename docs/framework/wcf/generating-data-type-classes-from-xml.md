---
title: Generování tříd datových typů z XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: c1b5dfda8aa5370dbc202ab90c75ab5677970467
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59309339"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="619e8-102">Generování tříd datových typů z XML</span><span class="sxs-lookup"><span data-stu-id="619e8-102">Generating Data Type Classes from XML</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="619e8-103">obsahuje novou funkci pro generování tříd datových typů z XML.</span><span class="sxs-lookup"><span data-stu-id="619e8-103">includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="619e8-104">Toto téma popisuje, jak automaticky vygenerovat datové typy pro informačního kanálu RSS blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="619e8-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="619e8-105">Získání XML z RSS blogu .NET informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="619e8-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="619e8-106">V Internet Exploreru přejděte [informačního kanálu RSS blogu .NET](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="619e8-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="619e8-107">Klikněte pravým tlačítkem na stránku a vybrat **zobrazit zdroj**.</span><span class="sxs-lookup"><span data-stu-id="619e8-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="619e8-108">Kopírovat text z informačního kanálu stisknutím kombinace kláves **Ctrl + A** k výběru veškerého textu a **Ctrl + C** ke kopírování.</span><span class="sxs-lookup"><span data-stu-id="619e8-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="619e8-109">Vytvoření datových typů</span><span class="sxs-lookup"><span data-stu-id="619e8-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="619e8-110">Otevřete soubor kódu, kde se má používat proxy server.</span><span class="sxs-lookup"><span data-stu-id="619e8-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="619e8-111">Tento soubor by měl být součástí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="619e8-111">This file should be part of a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] project.</span></span>  
  
2. <span data-ttu-id="619e8-112">Umístěte kurzor na místo v souboru mimo všechny existující třídy.</span><span class="sxs-lookup"><span data-stu-id="619e8-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="619e8-113">Vyberte **upravit**, **Vložit jinak**, **vložit XML jako třídy**.</span><span class="sxs-lookup"><span data-stu-id="619e8-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="619e8-114">Tříd pojmenovanou `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` a `rssChannelItemGuid` se vytvářejí s členy potřebné pro přístup k prvkům v informačním kanálu RSS.</span><span class="sxs-lookup"><span data-stu-id="619e8-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="619e8-115">Pomocí vygenerovaných tříd</span><span class="sxs-lookup"><span data-stu-id="619e8-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="619e8-116">Po vygenerování třídy lze použít v kódu, stejně jako jakékoli jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="619e8-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="619e8-117">Následující příklad kódu vrací novou instanci třídy `rssChannelImage` třídy.</span><span class="sxs-lookup"><span data-stu-id="619e8-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
