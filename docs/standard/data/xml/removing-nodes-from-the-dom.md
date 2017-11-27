---
title: "Odstranění uzlů z modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0885d53e737153448fabfd394d49bfdc793e0599
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="removing-nodes-from-the-dom"></a>Odstranění uzlů z modelu DOM
Chcete-li odebrat uzel z XML modelu DOM (Document Object), použijte <xref:System.Xml.XmlNode.RemoveChild%2A> metoda odebrat konkrétní uzel. Při odebrání uzlu metoda odebere podstrom, které patří k uzlu odebírána; To znamená pokud není uzlem typu list.  
  
 Pokud chcete odstranit z modelu DOM více uzlů, použijte <xref:System.Xml.XmlNode.RemoveAll%2A> metoda odebrat všechny podřízené objekty a atributy, pokud je k dispozici, aktuální uzel.  
  
 Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap>, můžete odebrat uzel pomocí <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metoda.  
  
 Chcete-li odebrat atributy, přečtěte si téma [odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Viz také  
 [XML Document Object Model (DOM).](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
