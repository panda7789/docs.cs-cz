---
title: Odebrání atributů z uzlu elementu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65fd6d2baae29c72241350e4568faf09b9c71f39
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47114824"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Odebrání atributů z uzlu elementu v modelu DOM
Existuje mnoho způsobů, jak odebrat atributy. Jednou z metod je odebrat z kolekce atributu. K tomuto účelu se provádí následující kroky:  
  
1.  Získat kolekci atributu pomocí elementu `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2.  Odeberte atribut z kolekce atributů pomocí jedné ze tří metod:  
  
    -   Použití <xref:System.Xml.XmlAttributeCollection.Remove%2A> odebrat konkrétní atribut.  
  
    -   Použití <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> odebrat všechny atributy z kolekce a nechte elementu žádné atributy.  
  
    -   Použití <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> odebrat atribut z kolekce atributů pomocí jeho indexové číslo.  
  
 Následující metody odebrání atributů z uzlu elementu.  
  
-   Použití <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> odebrat kolekci atributů.  
  
-   Použití <xref:System.Xml.XmlElement.RemoveAttribute%2A> odebrat jeden atribut podle názvu z kolekce.  
  
-   Použití <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> odebrat jeden atribut číslem indexu z kolekce.  
  
 Jeden další alternativou je načíst prvek, získat atribut z kolekce atributů a odebrat uzel atributu přímo. Pokud chcete získat atribut z kolekce atributů, můžete použít název, `XmlAttribute attr = attrs["attr_name"];`, index `XmlAttribute attr = attrs[0];`, nebo plně kvalifikovaný název s oborem názvů `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Bez ohledu na použitou k odebrání atributů metodu jsou zvláštní omezení týkající se odebrání atributů, které jsou definovány jako výchozí atributy v definici typu dokumentu (DTD). Výchozí atributy nelze odebrat, pokud je odebrán element, do kterých patří. Výchozí atributy jsou vždy k dispozici pro prvky, které mají výchozí atributy deklarované. Odebrání výchozí atribut ze <xref:System.Xml.XmlAttributeCollection> nebo z <xref:System.Xml.XmlElement> výsledky v atributu nahrazení vložen do <xref:System.Xml.XmlAttributeCollection> prvku inicializována na výchozí hodnotu, která byla deklarována. Pokud máte definované jako element `<book att1="1" att2="2" att3="3"></book>`, máte `book` deklarovat element s tři výchozí atributy. Implementace XML Document Object Model (DOM) zaručuje, že pokud je to to `book` existuje element, má tyto tři výchozí atributy `att1`, `att2`, a `att3`.  
  
 Při volání s <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> metoda nastaví hodnotu atributu String.Empty, protože atribut nemůže existovat bez hodnoty.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
