---
title: Vytváření nových odkazů na entity
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 8c81aae89bbe5979dffdc47a369349bd2b3f2df7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710983"
---
# <a name="creating-new-entity-references"></a>Vytváření nových odkazů na entity
Metoda **CreateEntityReference** vytvoří nový uzel **XmlEntityReference** . Model DOM (Document Object Model) XML (DOM) zjistí, zda již byl deklarován název entity, který je odkazován. Pokud má, podřízené uzly uzlu **XmlEntityReference** se zkopírují z uzlu deklarace entity. Pokud neexistuje žádná deklarace entity, která by odpovídala, je prázdný textový uzel připojen jako jediný podřízený uzel odkazu na entitu. Vzhledem k tomu, že podřízené uzly uzlu **XmlEntityReference** jsou kopiemi jiných uzlů, jsou tyto podřízené uzly určeny jen pro čtení a nelze je upravit.  
  
 Po zkopírování uzlů může existovat obor názvů v oboru v místě odkazu na entitu. Tento obor názvů ovlivňuje konfiguraci všech generovaných uzlů elementu nebo atributů.  
  
> [!NOTE]
> DOM přidá podřízené uzly do objektu **EntityReference** pouze při vložení uzlu **EntityReference** do dokumentu. Nově vytvořené uzly **EntityReference** nemají podřízené uzly.  
  
 I když je **objektu XmlDataDocument** odvozenou třídou **XmlDocument**, **objektu XmlDataDocument** nepodporuje vytváření odkazů na entity. Důvodem je, že podřízené objekty **EntityReference** jsou jen pro čtení. Podřízené položky uzlu **EntityReference** mohou být rozloženy do více než jedné oblasti. V tomto případě bude část řádku přidružená k oblasti, která obsahuje část objektu **EntityReference** , jen pro čtení.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
