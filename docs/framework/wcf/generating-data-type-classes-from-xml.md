---
title: Generování tříd datových typů z XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 977b12b5c61c196a4f033361d37785e4ed0af73a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975857"
---
# <a name="generating-data-type-classes-from-xml"></a>Generování tříd datových typů z XML
.NET Framework 4,5 obsahuje novou funkci pro generování tříd datových typů z XML. Toto téma popisuje, jak automaticky generovat datové typy pro informační kanál RSS blogu .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Získání XML z informačního kanálu RSS blogu .NET  
  
1. V Internet Exploreru přejděte do [informačního kanálu RSS blogu .NET](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Klikněte pravým tlačítkem na stránku a vyberte **Zobrazit zdroj**.  
  
3. Zkopírujte text informačního kanálu stisknutím **kombinace kláves CTRL + a** , vyberte veškerý text a **stiskněte kombinaci kláves CTRL + C** ke zkopírování.  
  
### <a name="creating-the-data-types"></a>Vytváření datových typů  
  
1. Otevřete soubor kódu, kde bude použit proxy server. Tento soubor by měl být součástí projektu .NET Framework 4,5.  
  
2. Umístěte kurzor do umístění v souboru mimo všechny existující třídy.  
  
3. Vyberte **Upravit**, **Vložit speciální**a **Vložit XML jako třídy**.  
  
4. Třídy s názvem `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` a `rssChannelItemGuid` jsou vytvořeny s potřebnými členy pro přístup k prvkům v informačním kanálu RSS.  
  
### <a name="using-the-generated-classes"></a>Použití vygenerovaných tříd  
  
1. Po vygenerování tříd je lze použít v kódu, podobně jako jakékoli jiné třídy. Následující příklad kódu vrátí novou instanci třídy `rssChannelImage`.  
  
    ```csharp
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
