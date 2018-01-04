---
title: "Odkazy na entity jsou rozšířené a není zachovaná."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 00b997865c614756ea5fd9567ded3baa469f4c62
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Odkazy na entity jsou rozšířené a není zachovaná.
Pokud je odkaz na entitu rozšířit a nahradit text reprezentuje, **XmlEntityReference** uzlu není vytvořena. Místo toho je analyzována deklarací entity a uzlů vytvořené z obsahu v deklaraci zkopírují v místě z **XmlEntityReference**. Proto v `&publisher;` například `&publisher;` nebude uložena, ale místo toho **XmlText** uzel je vytvořen.  
  
 ![rozšířit stromovou strukturu](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Stromovou strukturu pro odkazy na entity, které jsou rozšířit  
  
 Znak entity, jako `B` nebo `<` nezachovají. Místo toho jsou vždy rozbalený a reprezentován jako textové uzly.  
  
 Chcete-li zachovat **XmlEntityReference** k němu připojen uzlů a uzly podřízené odkaz na entitu, nastavte **EntityHandling příslušným** příznak, který **ExpandCharEntities**. Jinak ponechejte **EntityHandling příslušným** příznak v výchozí, což je **ExpandEntities**. V takovém případě se nezobrazí uzly odkaz entity v modelu DOM. Uzly jsou nahrazovány uzly, které jsou kopie podřízené uzly deklarace entity.  
  
 Jeden vedlejším účinkem není zachování odkazy na entity je, po uložení dokumentu a k předání jiná aplikace, má přijímající aplikace nebude vědět, že uzly byly vygenerovány odkazu na entitu. Ale když odkazy na entity se zachovají, přijímající aplikace se zobrazí odkaz na entitu a přečte podřízené uzly. Je zřejmé, že podřízené uzly představují informace, které se v deklaraci entity. Například modelu DOM teoreticky má následující strukturu pokud odkazy na entity se zachovají.  
  
 XmlElement: vydavatele  
  
 XmlEntityReference:`&publisher;`  
  
 XmlText: Společnosti Microsoft Press  
  
 Pokud jsou odkazy na entity rozbaleny v modelu DOM, což je výchozí metodou, strukturu má tento typ stromové struktury:  
  
 XmlElement: vydavatele  
  
 XmlText: Společnosti Microsoft Press  
  
 Všimněte si je pryč uzel odkazu entity, a má přijímající aplikace nelze zjistit, který **XmlText** uzlu, který obsahuje "Společnosti Microsoft Press" byl vytvořen z deklarace entity.  
  
 Pokud použijete čtečku entity, nelze přeložit **zatížení** metoda vyvolá výjimku, pokud se setká s odkazu na entitu.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
