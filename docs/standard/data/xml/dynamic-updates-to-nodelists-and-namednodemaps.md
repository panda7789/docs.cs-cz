---
title: Dynamické aktualizace NodeLists a NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1de133d0208f1b86ad3240cdc00d8016af0a160c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568963"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dynamické aktualizace NodeLists a NamedNodeMaps
Protože **XmlNodeList** a **XmlNamedNodeMap** obsahují sadu uzlů, ještě v dokumentu XML je načten do paměti a tento proces je upravována, stavů World Wide Web Consortium (W3C), které tyto objekty obsahující sadu uzlů musí být dynamické. To znamená pokud se změní zdrojový dokument, pak data v těchto dvou objektů měli změnit také. Proto pokud máte **XmlNodeList** obsahující všechny podřízené elementy určitý element (například element X) a pak přidejte další elementu, element Q, v dokumentu v části element X. **XmlNodeList** by měly mít také tohoto nového elementu Q jeho kolekce přidat. Platí to pozpátku. Pokud uzel je přidán do **XmlNodeList**, se rovněž aktualizuje zdrojový dokument.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
