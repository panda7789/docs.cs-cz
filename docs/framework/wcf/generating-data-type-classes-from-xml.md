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
# <a name="generating-data-type-classes-from-xml"></a>Generování tříd datových typů z XML
Rozhraní .NET Framework 4.5 obsahuje novou funkci pro generování tříd datového typu z xml. Toto téma popisuje, jak automaticky generovat datové typy pro informační kanál RSS blogu .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Získání xml z informačního kanálu RSS blogu .NET  
  
1. V aplikaci Internet Explorer přejděte na [informační kanál RSS blogu .NET](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Klepněte pravým tlačítkem myši na stránku a vyberte **zobrazit zdroj**.  
  
3. Zkopírujte text informačního kanálu stisknutím **ctrl+a** a vyberte veškerý text a **zkopírovat ctrl+c.**  
  
### <a name="creating-the-data-types"></a>Vytváření datových typů  
  
1. Otevřete soubor kódu, kde má být použit proxy server. Tento soubor by měl být součástí projektu rozhraní .NET Framework 4.5.  
  
2. Umístěte kurzor na místo v souboru mimo všechny existující třídy.  
  
3. Vyberte **Upravit**, **Vložit jinak**, **Vložit XML jako třídy**.  
  
4. Třídy `link` `rss`s `rssChannel` `rssChannelImage`názvem `rssChannelItem` `rssChannelItemGuid` , , , , a jsou vytvořeny s členy nezbytné pro přístup k prvkům v informačním kanálu RSS.  
  
### <a name="using-the-generated-classes"></a>Použití generovaných tříd  
  
1. Jakmile jsou generovány třídy, mohou být použity v kódu jako všechny ostatní třídy. Následující příklad kódu vrátí novou `rssChannelImage` instanci třídy.  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
