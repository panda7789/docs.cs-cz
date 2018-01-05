---
title: "Vytvoření nové odkazy na Entity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76093fbe7095c2aae7caa69147f6181c292ca734
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="creating-new-entity-references"></a>Vytvoření nové odkazy na Entity
**CreateEntityReference** metoda vytvoří novou **XmlEntityReference** uzlu. XML modelu DOM (Document Object) zjistí, pokud již byl deklarován název entity se na ně odkazovat. Pokud ano, podřízené uzly **XmlEntityReference** uzlu se zkopírují z uzlu deklarace entity. Pokud není k dispozici žádná deklarace entity, který odpovídá, je připojen prázdný textový uzel jako jediným podřízeným entity uzlu odkazu. Protože podřízené uzly **XmlEntityReference** uzlu jsou kopie další uzly, tyto podřízené uzly jsou jen pro čtení a nelze jej změnit.  
  
 Pokud se zkopírují uzlů, může být obor názvů v oboru v místě odkaz na entitu. Tento obor názvů ovlivňuje konfigurace elementu nebo atributu uzlů, která se generuje.  
  
> [!NOTE]
>  Přidá podřízené uzly modelu DOM **EntityReference** pouze při vložení **EntityReference** uzlu v dokumentu. Nově vytvořený **EntityReference** uzly mít žádné podřízené uzly.  
  
 I když **XmlDataDocument** je třída odvozená z **třídou XMLDocument nastavenou na**, **XmlDataDocument** nepodporuje vytvoření odkazy na entity. Důvodem je, že **EntityReference** podřízené objekty jsou jen pro čtení. Podřízené objekty daného **EntityReference** uzlu může zahrnovat více oblastí. V takovém případě součástí řádek přidružené k oblasti, která obsahuje součást **EntityReference** budou jen pro čtení.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
