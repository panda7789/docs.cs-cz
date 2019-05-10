---
title: Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f2be5881a7f663b13dd13ffc0e0faf88afd7efc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647963"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje dvě sady navigačních metod, najít první sady v [uzlu nastavení navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) tématu, se používají pro navigaci *sad uzlů* v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu. Druhá sada popsané v tomto tématu slouží k navigaci *uzly atributu a oboru názvů* v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.  
  
## <a name="attribute-node-navigation"></a>Atribut uzlu navigace  
 Atributy jsou vlastnosti elementu, nejsou podřízené objekty daného elementu. Tento rozdíl je důležitý, protože metody <xref:System.Xml.XPath.XPathNavigator> Třída použitá pro navigaci na stejné úrovni, nadřazenými a podřízenými uzly.  
  
 Například <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody nepoužívají přejít z elementu, atributu nebo mezi atributy. Místo toho atributy mají různé metody navigace.  
  
 Níže jsou atribut metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Pokud aktuální uzel je element, můžete použít <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> vlastnosti chcete zobrazit, pokud jsou všechny atributy přidružené k elementu. Poté, co je známo, že element má atributy, existuje několik metod pro přístup k atributům. Chcete-li načíst z elementu jeden atribut, použijte <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metody. Přesunout <xref:System.Xml.XPath.XPathNavigator> konkrétní atribut, použijte <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> metody. Jednotlivé atributy elementu mohou také iteraci pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> metoda, za nímž následuje několik volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> metody.  
  
> [!NOTE]
>  Když <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn na uzlu atribut nebo obor názvů <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody vždy vrátí `false`, a nemají žádný vliv na umístění <xref:System.Xml.XPath.XPathNavigator>. Výjimky jsou <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, a <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> metody.  
  
## <a name="namespace-node-navigation"></a>Namespace uzlu navigace  
 Každý prvek má přidruženy uzly oboru názvů, jeden pro každý jedinečných názvů předponu, která je vázána na obor názvů identifikátoru URI v oboru pro daný element (včetně předpona XML je vázán na `http://www.w3.org/XML/1998/namespace` obor názvů, který je implicitně deklarován ve všech dokumentech XML) a jeden pro výchozí obor názvů, pokud je v oboru pro daný element. Element je nadřazená každé z těchto názvů uzlů; uzel oboru názvů však není podřízených objektů svého nadřízeného elementu.  
  
 Stejně jako u atributů, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody nepoužívají přejít z elementu uzel oboru názvů, nebo mezi uzly oboru názvů. Místo toho uzly oboru názvů mají různé metody navigace.  
  
 Níže jsou obor názvů navigačních metod <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Je vždy alespoň jeden uzel oboru názvů v oboru pro libovolný prvek v dokumentu XML. Toto je uzel oboru názvů s předponou `xml` a identifikátor URI oboru názvů `http://www.w3.org/XML/1998/namespace`. Chcete-li získat identifikátor URI v oboru uvedeny konkrétní předpony oboru názvů, použijte <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> metody. Přesunout <xref:System.Xml.XPath.XPathNavigator> objekt pro konkrétní obor názvů uzlu, použijte <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> metody. Každý uzel oboru názvů v oboru pro daný element můžete také iteraci pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metoda a více volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody.  
  
> [!NOTE]
>  Když <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn na uzlu atribut nebo obor názvů <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody vždy vrátí `false`, a nemají žádný vliv na umístění <xref:System.Xml.XPath.XPathNavigator>. Výjimky jsou <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, a <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> metody.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Výčet XPathNamespaceScope  
 Při navigaci uzly oboru názvů <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody lze volat pomocí <xref:System.Xml.XPath.XPathNamespaceScope> parametru. Tyto metody chovat jinak než jejich protějšky zavolán bez parametrů. <xref:System.Xml.XPath.XPathNamespaceScope> Výčet má hodnoty <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, nebo <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 Následující příklady ukazují, co jsou obory názvů vrácené <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody v různých oborech v dokumentu XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Pořadí obor názvů (obor názvů <xref:System.Xml.XPath.XPathNavigator> je umístěn na po volání <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metoda následovaný sérii volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metoda) vypadá takto.  
  
- Když umístíte na `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Když umístíte na `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Když umístíte na `root`: `xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Třídy vrátí uzly oboru názvů v pořadí reverzní dokumentů. Proto <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> v podstatě přejde na poslední uzel oboru názvů v aktuálním oboru.  
  
 Následující příklady ukazují, co jsou obory názvů vrácené <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody s <xref:System.Xml.XPath.XPathNamespaceScope> výčet zadané v různých oborech v dokumentu XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Při umístění na `child2`, pořadí obor názvů (obor názvů <xref:System.Xml.XPath.XPathNavigator> je umístěn na po volání <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metoda následovaný sérii volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> – metoda) je následující.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`, a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, a `xmlns="http://www.contoso.com"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Třídy vrátí uzly oboru názvů v pořadí reverzní dokumentů. Proto <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> v podstatě přejde na poslední uzel oboru názvů v aktuálním oboru.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Navigace v sadě uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Extrahování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
