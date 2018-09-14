---
title: Odkazy na entity jsou rozšířené a Nezachované
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a55aa71ff3976241b96dd12baef06a9a13ef9dd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519023"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Odkazy na entity jsou rozšířené a Nezachované
Pokud odkaz na entitu je rozbalen a nahrazuje představuje, **XmlEntityReference** uzlu není vytvořena. Místo toho je analyzován entity prohlášení a uzlů vytvořené z obsahu v deklaraci zkopírují místo hodnoty **XmlEntityReference**. Proto v `&publisher;` například `&publisher;` neukládají, ale místo toho **XmlText** uzel je vytvořen.  
  
 ![rozbalení stromovou strukturu](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Stromovou strukturu pro odkazy na entity, které jsou rozbaleny  
  
 Znakové entity, jako `B` nebo `<` nejsou zachovány. Místo toho jsou vždy rozbalený a reprezentovány jako uzly text.  
  
 Chcete-li zachovat **XmlEntityReference** uzly a uzly podřízeného odkazu entity k němu připojená, nastavte **EntityHandling příslušným** příznak **ExpandCharEntities**. V opačném případě ponechte **EntityHandling příslušným** příznak na výchozí, což je **ExpandEntities**. V takovém případě neuvidíte uzly odkaz na entitu v modelu DOM. Uzly jsou nahrazené uzly, které jsou kopie uzly podřízené entity prohlášení.  
  
 Jedním efektem straně není zachování odkazy na entity je, že když je dokument uložen a předávají do jiné aplikace, přijímající aplikace neví, že uzly byly vytvořeny podle odkazu na entitu. Ale když jsou zachovány odkazy na entity, přijímající aplikace uvidí odkazu na entitu a přečte podřízené uzly. Je zřejmé, že podřízené uzly představují informace, které se v deklaraci entity. V modelu DOM teoreticky má například následující strukturu, pokud jsou zachovány odkazy na entity.  
  
 Třída XmlElement: vydavatele  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Microsoft Press  
  
 Pokud jsou odkazy na entity rozbaleny v modelu DOM, což je výchozí metodou, má strukturu tohoto typu stromu:  
  
 Třída XmlElement: vydavatele  
  
 XmlText: Microsoft Press  
  
 Všimněte si, že uzel odkazu entity je pryč a přijímající aplikace nelze zjistit, zda **XmlText** uzlu, který obsahuje "Microsoft Press" byl vytvořen z deklarace entity.  
  
 Pokud používáte čtečku entity, nejde přeložit **zatížení** metoda vyvolá výjimku, pokud se setká s odkazu na entitu.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
