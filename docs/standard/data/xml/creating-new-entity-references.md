---
title: Vytváření nových odkazů na entity
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8d4e9e1e2dfd9882504c935912bcf235608485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965897"
---
# <a name="creating-new-entity-references"></a>Vytváření nových odkazů na entity
Metoda **CreateEntityReference** vytvoří nový uzel **XmlEntityReference** . Model DOM (Document Object Model) XML (DOM) zjistí, zda již byl deklarován název entity, který je odkazován. Pokud má, podřízené uzly uzlu **XmlEntityReference** se zkopírují z uzlu deklarace entity. Pokud neexistuje žádná deklarace entity, která by odpovídala, je prázdný textový uzel připojen jako jediný podřízený uzel odkazu na entitu. Vzhledem k tomu, že podřízené uzly uzlu **XmlEntityReference** jsou kopiemi jiných uzlů, jsou tyto podřízené uzly určeny jen pro čtení a nelze je upravit.  
  
 Po zkopírování uzlů může existovat obor názvů v oboru v místě odkazu na entitu. Tento obor názvů ovlivňuje konfiguraci všech generovaných uzlů elementu nebo atributů.  
  
> [!NOTE]
> DOM přidá podřízené uzly do objektu **EntityReference** pouze při vložení uzlu **EntityReference** do dokumentu. Nově vytvořené uzly **EntityReference** nemají podřízené uzly.  
  
 I když je **objektu XmlDataDocument** odvozenou třídou **XmlDocument**, **objektu XmlDataDocument** nepodporuje vytváření odkazů na entity. Důvodem je, že podřízené objekty **EntityReference** jsou jen pro čtení. Podřízené položky uzlu **EntityReference** mohou být rozloženy do více než jedné oblasti. V tomto případě bude část řádku přidružená k oblasti, která obsahuje část objektu **EntityReference** , jen pro čtení.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
