---
title: "Generování tříd datových typů z XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67b9e239c8b60511caf3989c0b3a1a5d6dcc9b26
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="generating-data-type-classes-from-xml"></a>Generování tříd datových typů z XML
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]zahrnuje nové funkce, která negeneruje třídy datového typu XML. Toto téma popisuje, jak automaticky generovat datové typy pro informačního kanálu RSS blogu .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Získání XML z RSS blogu .NET kanálu  
  
1.  V Internet Exploreru přejděte na [informačního kanálu RSS blogu .NET](https://blogs.msdn.microsoft.com/dotnet/feed/).  
  
2.  Pravým tlačítkem myši a vyberte **zobrazit zdroj**.  
  
3.  Zkopírujte text informačního kanálu stisknutím **Ctrl + A** vyberte veškerý text a **Ctrl + C** ke kopírování.  
  
### <a name="creating-the-data-types"></a>Vytvoření datové typy  
  
1.  Otevřete soubor kódu, kde má být použita k proxy serveru. Tento soubor musí být součástí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projektu.  
  
2.  Umístěte kurzor na místo v souboru mimo všech existujících tříd.  
  
3.  Vyberte **upravit**, **Vložit jinak**, **vložit XML jako třídy**.  
  
4.  Třídy názvem `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` a `rssChannelItemGuid` vytvářejí se členy potřebné pro přístup k elementů v informačního kanálu RSS.  
  
### <a name="using-the-generated-classes"></a>Pomocí vygenerované třídy  
  
1.  Jakmile se generují třídy, použitím v kódu jako ostatní třídy. Následující příklad kódu vrátí novou instanci třídy `rssChannelImage` třídy.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
