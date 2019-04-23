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
# <a name="generating-data-type-classes-from-xml"></a>Generování tříd datových typů z XML
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] obsahuje novou funkci pro generování tříd datových typů z XML. Toto téma popisuje, jak automaticky vygenerovat datové typy pro informačního kanálu RSS blogu .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Získání XML z RSS blogu .NET informačního kanálu  
  
1. V Internet Exploreru přejděte [informačního kanálu RSS blogu .NET](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Klikněte pravým tlačítkem na stránku a vybrat **zobrazit zdroj**.  
  
3. Kopírovat text z informačního kanálu stisknutím kombinace kláves **Ctrl + A** k výběru veškerého textu a **Ctrl + C** ke kopírování.  
  
### <a name="creating-the-data-types"></a>Vytvoření datových typů  
  
1. Otevřete soubor kódu, kde se má používat proxy server. Tento soubor by měl být součástí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projektu.  
  
2. Umístěte kurzor na místo v souboru mimo všechny existující třídy.  
  
3. Vyberte **upravit**, **Vložit jinak**, **vložit XML jako třídy**.  
  
4. Tříd pojmenovanou `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` a `rssChannelItemGuid` se vytvářejí s členy potřebné pro přístup k prvkům v informačním kanálu RSS.  
  
### <a name="using-the-generated-classes"></a>Pomocí vygenerovaných tříd  
  
1. Po vygenerování třídy lze použít v kódu, stejně jako jakékoli jiné třídy. Následující příklad kódu vrací novou instanci třídy `rssChannelImage` třídy.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
