---
title: Dynamické aktualizace pro NodeLists a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f56ba8711988f2f7d743dc4ff7b69272e2642a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934469"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dynamické aktualizace pro NodeLists a NamedNodeMaps
Vzhledem k tomu, **XmlNodeList** a **XmlNamedNodeMap** obsahují sadu uzlů, ale dokument XML je načten do paměti a je upravována, World Wide Web Consortium (W3C) uvádí, že tyto objekty která obsahují sadu uzlů musí být dynamické. To znamená pokud se změní podkladové dokument, pak data v těchto dvou objektů by měl změnit také. Proto pokud máte **XmlNodeList** , která obsahuje všechny podřízené prvky prvku konkrétní (například prvek X) a pak přidejte další prvek, Q, element v dokumentu v rámci elementu X. **XmlNodeList** musí být také tento nový prvek Q přidat do své kolekce. Totéž platí v opačném pořadí. Pokud uzel se přidá do **XmlNodeList**, je také aktualizovat zdrojový dokument.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
