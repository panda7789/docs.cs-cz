---
title: Odebrání atributů z uzlu elementu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: bb18e712d5ed2cd06c7ae0e867b19ca8a9ad2513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710346"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Odebrání atributů z uzlu elementu v modelu DOM
Existuje mnoho způsobů, jak odebrat atributy. Jednou z postupů je odebrat je z kolekce atributů. K tomu je potřeba provést následující kroky:  
  
1. Získat kolekci atributů z elementu pomocí `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2. Odeberte atribut z kolekce atributů pomocí jedné ze tří metod:  
  
    - Pro odebrání konkrétního atributu použijte <xref:System.Xml.XmlAttributeCollection.Remove%2A>.  
  
    - Použijte <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> k odebrání všech atributů z kolekce a ponechání elementu bez atributů.  
  
    - Pomocí <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> můžete odebrat atribut z kolekce atributů pomocí jeho čísla indexu.  
  
 Následující metody odstraňují atributy z uzlu element.  
  
- Pro odebrání kolekce atributů použijte <xref:System.Xml.XmlElement.RemoveAllAttributes%2A>.  
  
- Pomocí <xref:System.Xml.XmlElement.RemoveAttribute%2A> odebrat jeden atribut podle názvu z kolekce.  
  
- Použijte <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> k odebrání jednoho atributu podle čísla indexu z kolekce.  
  
 Jednou z možností je získat element, získat atribut z kolekce atributů a přímo odebrat uzel atributu. Chcete-li získat atribut z kolekce atributů, můžete použít název, `XmlAttribute attr = attrs["attr_name"];`, index `XmlAttribute attr = attrs[0];`nebo plně kvalifikovaný název s oborem názvů `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Bez ohledu na metodu použitou k odebrání atributů existují zvláštní omezení na odebrání atributů, které jsou definovány jako výchozí atributy v definici typu dokumentu (DTD). Výchozí atributy nelze odebrat, pokud není odebrán element, ke kterému patří. Pro prvky, které mají deklarované výchozí atributy, jsou vždy přítomny výchozí atributy. Odebrání výchozího atributu z <xref:System.Xml.XmlAttributeCollection> nebo z <xref:System.Xml.XmlElement> vede k nahrazení nahrazujícího atributu vloženého do <xref:System.Xml.XmlAttributeCollection> elementu, inicializovaného na výchozí hodnotu, která byla deklarována. Pokud máte element definovaný jako `<book att1="1" att2="2" att3="3"></book>`, pak máte `book` element se třemi výchozími atributy deklarovanými. Implementace XML model DOM (Document Object Model) (DOM) zaručuje, že pokud tento `book` prvek existuje, má tyto tři výchozí atributy `att1`, `att2`a `att3`.  
  
 Při volání s <xref:System.Xml.XmlAttribute>metoda <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> nastaví hodnotu atributu na String. Empty, protože atribut nesmí existovat bez hodnoty.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
