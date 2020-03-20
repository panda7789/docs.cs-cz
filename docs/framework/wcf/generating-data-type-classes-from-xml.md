---
title: Generování tříd datových typů z XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: d66cbd1806b90d21a483d0c470f953ddfb9c4fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184137"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="3de5e-102">Generování tříd datových typů z XML</span><span class="sxs-lookup"><span data-stu-id="3de5e-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="3de5e-103">Rozhraní .NET Framework 4.5 obsahuje novou funkci pro generování tříd datového typu z xml.</span><span class="sxs-lookup"><span data-stu-id="3de5e-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="3de5e-104">Toto téma popisuje, jak automaticky generovat datové typy pro informační kanál RSS blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="3de5e-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="3de5e-105">Získání xml z informačního kanálu RSS blogu .NET</span><span class="sxs-lookup"><span data-stu-id="3de5e-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="3de5e-106">V aplikaci Internet Explorer přejděte na [informační kanál RSS blogu .NET](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="3de5e-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="3de5e-107">Klepněte pravým tlačítkem myši na stránku a vyberte **zobrazit zdroj**.</span><span class="sxs-lookup"><span data-stu-id="3de5e-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="3de5e-108">Zkopírujte text informačního kanálu stisknutím **ctrl+a** a vyberte veškerý text a **zkopírovat ctrl+c.**</span><span class="sxs-lookup"><span data-stu-id="3de5e-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="3de5e-109">Vytváření datových typů</span><span class="sxs-lookup"><span data-stu-id="3de5e-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="3de5e-110">Otevřete soubor kódu, kde má být použit proxy server.</span><span class="sxs-lookup"><span data-stu-id="3de5e-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="3de5e-111">Tento soubor by měl být součástí projektu rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="3de5e-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="3de5e-112">Umístěte kurzor na místo v souboru mimo všechny existující třídy.</span><span class="sxs-lookup"><span data-stu-id="3de5e-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="3de5e-113">Vyberte **Upravit**, **Vložit jinak**, **Vložit XML jako třídy**.</span><span class="sxs-lookup"><span data-stu-id="3de5e-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="3de5e-114">Třídy `link` `rss`s `rssChannel` `rssChannelImage`názvem `rssChannelItem` `rssChannelItemGuid` , , , , a jsou vytvořeny s členy nezbytné pro přístup k prvkům v informačním kanálu RSS.</span><span class="sxs-lookup"><span data-stu-id="3de5e-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="3de5e-115">Použití generovaných tříd</span><span class="sxs-lookup"><span data-stu-id="3de5e-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="3de5e-116">Jakmile jsou generovány třídy, mohou být použity v kódu jako všechny ostatní třídy.</span><span class="sxs-lookup"><span data-stu-id="3de5e-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="3de5e-117">Následující příklad kódu vrátí novou `rssChannelImage` instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="3de5e-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
