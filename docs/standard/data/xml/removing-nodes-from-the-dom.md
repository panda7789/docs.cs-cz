---
title: Odebrání uzlů z modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: a34b92abc59215c3cb2b94afd88e2e30405b4e9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710307"
---
# <a name="removing-nodes-from-the-dom"></a>Odebrání uzlů z modelu DOM
Chcete-li odebrat uzel z XML model DOM (Document Object Model) (DOM), použijte <xref:System.Xml.XmlNode.RemoveChild%2A> metodu pro odebrání konkrétního uzlu. Když odeberete uzel, metoda odstraní podstrom patřící k odebíranému uzlu. To znamená, že pokud se nejedná o uzel typu list.  
  
 Chcete-li odebrat více uzlů z modelu DOM, <xref:System.Xml.XmlNode.RemoveAll%2A> použijte metodu k odebrání všech podřízených objektů a atributů (Pokud je k dispozici) aktuálního uzlu.  
  
 Pokud pracujete s <xref:System.Xml.XmlNamedNodeMap>, můžete uzel odebrat pomocí <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> metody.  
  
 Chcete-li odebrat atributy, přečtěte si téma [Odebrání atributů z uzlu elementu v modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
