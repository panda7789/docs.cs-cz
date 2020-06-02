---
title: Odebrání atributů z uzlu elementu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: 0ac8528d52ef09aab99c76aea9378c0188fa66d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292017"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Odebrání atributů z uzlu elementu v modelu DOM
Existuje mnoho způsobů, jak odebrat atributy. Jednou z postupů je odebrat je z kolekce atributů. K tomu je potřeba provést následující kroky:  
  
1. Získat kolekci atributů z elementu pomocí `XmlAttributeCollection attrs = elem.Attributes;` .  
  
2. Odeberte atribut z kolekce atributů pomocí jedné ze tří metod:  
  
    - Slouží <xref:System.Xml.XmlAttributeCollection.Remove%2A> k odebrání konkrétního atributu.  
  
    - Použijte <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> k odebrání všech atributů z kolekce a ponechání elementu bez atributů.  
  
    - Použijte <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> k odebrání atributu z kolekce atributů pomocí jeho čísla indexu.  
  
 Následující metody odstraňují atributy z uzlu element.  
  
- Použijte <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> k odebrání kolekce atributů.  
  
- Použijte <xref:System.Xml.XmlElement.RemoveAttribute%2A> k odebrání jednoho atributu podle názvu z kolekce.  
  
- Použijte <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> k odebrání jednoho atributu podle čísla indexu z kolekce.  
  
 Jednou z možností je získat element, získat atribut z kolekce atributů a přímo odebrat uzel atributu. Chcete-li získat atribut z kolekce atributů, můžete použít název, `XmlAttribute attr = attrs["attr_name"];` , index `XmlAttribute attr = attrs[0];` nebo plnou kvalifikaci názvu s oborem názvů `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]` .  
  
 Bez ohledu na metodu použitou k odebrání atributů existují zvláštní omezení na odebrání atributů, které jsou definovány jako výchozí atributy v definici typu dokumentu (DTD). Výchozí atributy nelze odebrat, pokud není odebrán element, ke kterému patří. Pro prvky, které mají deklarované výchozí atributy, jsou vždy přítomny výchozí atributy. Odebrání výchozího atributu z <xref:System.Xml.XmlAttributeCollection> nebo z <xref:System.Xml.XmlElement> výsledků v rámci nahrazujícího atributu vloženého do <xref:System.Xml.XmlAttributeCollection> prvku, inicializovaného na výchozí hodnotu, která byla deklarována. Pokud máte element definovaný jako `<book att1="1" att2="2" att3="3"></book>` , pak máte `book` deklarovaný element se třemi výchozími atributy. Implementace XML model DOM (Document Object Model) (DOM) zaručuje, že pokud tento `book` prvek existuje, má tyto tři výchozí atributy `att1` , `att2` a `att3` .  
  
 Při volání s <xref:System.Xml.XmlAttribute> , <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> Metoda nastaví hodnotu atributu na String. Empty, protože atribut nesmí existovat bez hodnoty.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
