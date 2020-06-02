---
title: Odkazy na entity jsou rozšířené a nezachované
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
ms.openlocfilehash: 1d26e9a35497bb0d5293e8a5b630bf4356325401
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292043"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Odkazy na entity jsou rozšířené a nezachované
Když se odkaz na entitu rozbalí a nahradí textem, který představuje, uzel **XmlEntityReference** se nevytvoří. Místo toho je deklarace entity analyzována a uzly vytvořené z obsahu v deklaraci jsou kopírovány na místo **XmlEntityReference**. Proto se v `&publisher;` příkladu `&publisher;` neukládá, ale místo toho se vytvoří uzel **XmlText** .  
  
 ![rozbalená stromová struktura](media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Stromová struktura pro odkazy na entity, které jsou rozbaleny  
  
 Znakové entity, jako `B` jsou nebo, nejsou `<` zachovány. Místo toho jsou vždy rozbaleny a jsou reprezentovány jako textové uzly.  
  
 Pro zachování uzlů **XmlEntityReference** a podřízených uzlů odkazovaného odkazu na entitu nastavte příznak **EntityHandling** na **ExpandCharEntities**. V opačném případě ponechte příznak **EntityHandling** ve výchozím nastavení, což je **ExpandEntities**. V takovém případě se v modelu DOM nezobrazí uzly odkazů na entity. Uzly jsou nahrazeny uzly, které jsou kopiemi podřízených uzlů deklarace entity.  
  
 Jedním z vedlejších účinků nezachování odkazů na entity je to, že když se dokument uloží a předává do jiné aplikace, přijímající aplikace neví, že se uzly vygenerovaly odkazem na entitu. Nicméně pokud jsou zachovány odkazy na entity, přijímající aplikace uvidí odkaz na entitu a přečte podřízené uzly. Je zřejmé, že podřízené uzly reprezentují informace, které byly v deklaraci entity. Model DOM má například teoreticky následující strukturu, pokud jsou zachovány odkazy na entity.  
  
 XmlElement: Vydavatel  
  
 XmlEntityReference:`&publisher;`  
  
 XmlText: Microsoft Press  
  
 Pokud jsou odkazy na entity rozbaleny v modelu DOM, což je výchozí metoda, struktura má tento typ stromu:  
  
 XmlElement: Vydavatel  
  
 XmlText: Microsoft Press  
  
 Všimněte si, že uzel odkazu na entitu zmizí a přijímající aplikace nemůže říct, že uzel **XmlText** obsahující "Microsoft Press" byl vytvořen z deklarace entity.  
  
 Použijete-li čtecí modul, který nemůže vyřešit entity, vyvolá metoda **Load** výjimku, pokud nalezne odkaz na entitu.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
