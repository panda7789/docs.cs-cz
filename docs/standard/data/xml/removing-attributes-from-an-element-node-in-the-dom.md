---
title: Odebrání atributů z uzlu elementu v modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 758ce84390c9ba47e3eb56e1feb293a4cf0408a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Odebrání atributů z uzlu elementu v modelu DOM
Existuje mnoho způsobů, jak odebrat atributy. Jednoho technika je odebrat z kolekce atributů. K tomu jsou prováděny následovně:  
  
1.  Získání kolekce atributů z elementu pomocí `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2.  Odeberte atribut z kolekce atributů pomocí jedné ze tří metod:  
  
    -   Použití <xref:System.Xml.XmlAttributeCollection.Remove%2A> odebrat určitým atributem.  
  
    -   Použití <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> odebrat všechny atributy z kolekce a nechte žádné atributy elementu.  
  
    -   Použití <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> pomocí jeho indexové číslo odstranit atribut z kolekce atributů.  
  
 Následující metody odebrat z uzlu element atributy.  
  
-   Použití <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> odebrat kolekce atributů.  
  
-   Použití <xref:System.Xml.XmlElement.RemoveAttribute%2A> odebrat jeden atribut podle názvu z kolekce.  
  
-   Použití <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> možnost odebrání jeden atribut číslo indexu z kolekce.  
  
 Jeden další možností je získat element, získat atribut z kolekce atributů a odebrat uzel atribut přímo. Pokud chcete atribut z kolekce atributů, můžete použít název, `XmlAttribute attr = attrs["attr_name"];`, index `XmlAttribute attr = attrs[0];`, nebo plně kvalifikovaný název s oborem názvů `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Bez ohledu na to, v případě metody slouží k odebírání atributy jsou speciální omezení odebrání atributů, které jsou definovány jako výchozí atributy v definici typu dokumentu (DTD). Výchozí atributy nelze odebrat, pokud je odebrán element, ke které patří. Výchozí atributy jsou vždy k dispozici pro prvky, které mají výchozí atributy deklarován. Odebrání výchozí atribut z <xref:System.Xml.XmlAttributeCollection> nebo z <xref:System.Xml.XmlElement> výsledky v atributu nahrazení vloženy do <xref:System.Xml.XmlAttributeCollection> elementu, inicializovat na výchozí hodnotu, která byla definována. Pokud máte element definovaný jako `<book att1="1" att2="2" att3="3"></book>`, pak máte `book` deklarovaný element s tři výchozí atributy. Implementace XML modelu DOM (Document Object) zaručuje, že stejně dlouho jako to `book` element existuje, obsahuje tyto tři výchozí atributy `att1`, `att2`, a `att3`.  
  
 Při volání s <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> metoda nastaví na hodnotu atributu String.Empty, protože atribut nemůže existovat bez hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
