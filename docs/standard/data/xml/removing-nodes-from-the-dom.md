---
title: Odebrání uzlů z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be592466627e6ee7b23c608e0defe786548907ad
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878356"
---
# <a name="removing-nodes-from-the-dom"></a>Odebrání uzlů z modelu DOM
Chcete-li odebrat uzel z XML Document Object Model (DOM), použijte <xref:System.Xml.XmlNode.RemoveChild%2A> metoda odebrání určitého uzlu. Při odebírání uzlu metodu odebere podstrom, které patří k uzlu odebírá; To znamená pokud není uzel typu list.  
  
 Chcete-li odebrat více uzlů z modelu DOM, použijte <xref:System.Xml.XmlNode.RemoveAll%2A> metoda odebrat všechny podřízené prvky a atributy, pokud je k dispozici pro aktuální uzel.  
  
 Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap>, můžete odebrat uzel pomocí <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metoda.  
  
 Chcete-li odebrat atributy, naleznete v tématu [odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
