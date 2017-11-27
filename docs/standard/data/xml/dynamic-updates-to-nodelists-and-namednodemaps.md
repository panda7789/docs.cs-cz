---
title: "Dynamické aktualizace NodeLists a NamedNodeMaps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 459d746ff278ac4affa0318c1fad0aeb6a73e560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dynamické aktualizace NodeLists a NamedNodeMaps
Protože **XmlNodeList** a **XmlNamedNodeMap** obsahují sadu uzlů, ještě v dokumentu XML je načten do paměti a tento proces je upravována, stavů World Wide Web Consortium (W3C), které tyto objekty obsahující sadu uzlů musí být dynamické. To znamená pokud se změní zdrojový dokument, pak data v těchto dvou objektů měli změnit také. Proto pokud máte **XmlNodeList** obsahující všechny podřízené elementy určitý element (například element X) a pak přidejte další elementu, element Q, v dokumentu v části element X. **XmlNodeList** by měly mít také tohoto nového elementu Q jeho kolekce přidat. Platí to pozpátku. Pokud uzel je přidán do **XmlNodeList**, se rovněž aktualizuje zdrojový dokument.  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
