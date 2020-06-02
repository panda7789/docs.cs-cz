---
title: Dynamické aktualizace pro NodeLists a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 0199f24e9ef8dd28f91976edd50f78399dc893ef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292082"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dynamické aktualizace pro NodeLists a NamedNodeMaps
Vzhledem k tomu, že **XmlNodeList** a **XmlNamedNodeMap** obsahují sadu uzlů, ale dokument XML je načten do paměti a je upravován, konsorcium World Wide Web (W3C) uvádí, že tyto objekty, které obsahují sady uzlů, musí být dynamické. To znamená, že pokud se změní podkladové dokumenty, data v těchto dvou objektech by se měla změnit také. Proto pokud máte **XmlNodeList** , který obsahuje všechny podřízené prvky určitého prvku (například element X), pak přidáte další prvek, element Q, do dokumentu pod prvkem x. **XmlNodeList** by měl také mít přidán nový element Q do své kolekce. Totéž platí v obráceném pořadí. Pokud se do **XmlNodeList**přidá uzel, bude aktualizován i příslušný dokument.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
