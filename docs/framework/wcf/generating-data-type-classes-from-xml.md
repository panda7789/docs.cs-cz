---
title: Generování tříd datových typů z XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: bf5596211e78842153b7406273626a7fa3c3aeea
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990278"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="c2451-102">Generování tříd datových typů z XML</span><span class="sxs-lookup"><span data-stu-id="c2451-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="c2451-103">.NET Framework 4,5 obsahuje novou funkci pro generování tříd datových typů z XML.</span><span class="sxs-lookup"><span data-stu-id="c2451-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="c2451-104">Toto téma popisuje, jak automaticky generovat datové typy pro informační kanál RSS blogu .NET.</span><span class="sxs-lookup"><span data-stu-id="c2451-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="c2451-105">Získání XML z informačního kanálu RSS blogu .NET</span><span class="sxs-lookup"><span data-stu-id="c2451-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="c2451-106">V Internet Exploreru přejděte do [informačního kanálu RSS blogu .NET](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="c2451-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="c2451-107">Klikněte pravým tlačítkem na stránku a vyberte **Zobrazit zdroj**.</span><span class="sxs-lookup"><span data-stu-id="c2451-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="c2451-108">Zkopírujte text informačního kanálu stisknutím **kombinace kláves CTRL + a** , vyberte veškerý text a **stiskněte kombinaci kláves CTRL + C** ke zkopírování.</span><span class="sxs-lookup"><span data-stu-id="c2451-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="c2451-109">Vytváření datových typů</span><span class="sxs-lookup"><span data-stu-id="c2451-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="c2451-110">Otevřete soubor kódu, kde bude použit proxy server.</span><span class="sxs-lookup"><span data-stu-id="c2451-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="c2451-111">Tento soubor by měl být součástí projektu .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="c2451-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="c2451-112">Umístěte kurzor do umístění v souboru mimo všechny existující třídy.</span><span class="sxs-lookup"><span data-stu-id="c2451-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="c2451-113">Vyberte **Upravit**, **Vložit speciální**a **Vložit XML jako třídy**.</span><span class="sxs-lookup"><span data-stu-id="c2451-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="c2451-114">Třídy s `link`názvem ,,ajsou`rss`vytvořeny pomocínezbytnýchčlenůpropřístupkprvkůmvinformačnímkanáluRSS.`rssChannel` `rssChannelImage` `rssChannelItem` `rssChannelItemGuid`</span><span class="sxs-lookup"><span data-stu-id="c2451-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="c2451-115">Použití vygenerovaných tříd</span><span class="sxs-lookup"><span data-stu-id="c2451-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="c2451-116">Po vygenerování tříd je lze použít v kódu, podobně jako jakékoli jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="c2451-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="c2451-117">Následující příklad kódu vrátí novou instanci `rssChannelImage` třídy.</span><span class="sxs-lookup"><span data-stu-id="c2451-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
