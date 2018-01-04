---
title: "Atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f86abb7da5509a80cceede0f1092a75cef4d8da
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na
<xref:System.Xml.XPath.XPathNavigator> Třída poskytuje dvě sady metod navigace, v nalezen první sady, [uzlu nastavit navigační pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) tématu, se používají k přejděte *uzlu sady* v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu. Druhé sadě, popsané v tomto tématu slouží k přejděte *uzly atribut a obor názvů* v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.  
  
## <a name="attribute-node-navigation"></a>Atribut uzlu navigace  
 Atributy jsou vlastnosti elementu, ne podřízených objektů daného elementu. Tento rozdíl je důležité, z důvodu metody <xref:System.Xml.XPath.XPathNavigator> třída používaná k přejděte na stejné úrovni, nadřazené a podřízené uzly.  
  
 Například <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody nepoužívají se k přejděte z prvku, atributu nebo mezi atributy. Místo toho atributy mají odlišné metody navigace.  
  
 Následující způsoby atribut navigace <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Element po aktuálním uzlu můžete použít <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> vlastnosti chcete zobrazit, pokud jsou všechny atributy přidružené k tomuto prvku. Jakmile se ví, že element má atributy, existuje více metod pro přístup k atributům. Chcete-li načíst jeden atribut z elementu, použijte <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metoda. Přesunout <xref:System.Xml.XPath.XPathNavigator> na konkrétní atribut, pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> metoda. Můžete také iterovat přes každý atribut elementu pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> metoda, za nímž následuje několik volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> metoda.  
  
> [!NOTE]
>  Když <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn do atribut nebo obor názvů uzlu, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody vždy vrátí `false`, a nemají vliv na pozici <xref:System.Xml.XPath.XPathNavigator>. Výjimky jsou <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, a <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> metody.  
  
## <a name="namespace-node-navigation"></a>Namespace uzlu navigace  
 Každý prvek má přidruženou sadu uzlů obor názvů, jeden pro každou jedinečných názvů předponu, která je vázána na identifikátor URI v oboru pro daný element oboru názvů (včetně předpona XML vázána `http://www.w3.org/XML/1998/namespace` názvů, který je implicitně deklarován v každé dokumentu XML) a jeden pro výchozí obor názvů, pokud je v oboru pro daný element. Element je nadřazená každé z těchto názvů uzlů; uzel oboru názvů však není podřízených objektů svého nadřízeného elementu.  
  
 Stejně jako u atributů, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody nepoužívají z elementu přejděte k uzlu oboru názvů, nebo mezi uzly oboru názvů. Místo toho obor názvů uzly mají odlišné metody navigace.  
  
 Toto jsou obor názvů metody navigace <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 V oboru pro libovolný element v dokumentu XML není vždy alespoň jeden uzel oboru názvů. Toto je uzel oboru názvů s předponou `xml` a identifikátor URI oboru názvů `http://www.w3.org/XML/1998/namespace`. Chcete-li získat identifikátor URI v oboru uvedeny konkrétní předpony oboru názvů, použijte <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> metoda. Přesunout <xref:System.Xml.XPath.XPathNavigator> objekt pro konkrétní obor názvů uzlu, použijte <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> metoda. Každý uzel oboru názvů v oboru pro daný element můžete také iteraci pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metoda následuje několik volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metoda.  
  
> [!NOTE]
>  Když <xref:System.Xml.XPath.XPathNavigator> objekt je umístěn do atribut nebo obor názvů uzlu, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody vždy vrátí `false`, a nemají vliv na pozici <xref:System.Xml.XPath.XPathNavigator>. Výjimky jsou <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, a <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> metody.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>XPathNamespaceScope – výčet  
 Při přechodu uzly oboru názvů <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> nelze volat metody s <xref:System.Xml.XPath.XPathNamespaceScope> parametr. Tyto metody chovat jinak než jejich protějšky volána bez parametrů. <xref:System.Xml.XPath.XPathNamespaceScope> Výčet má hodnoty <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, nebo <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 Následující příklady ukazují, co jsou obory názvů vrácený <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody v různých oborech v dokumentu XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Pořadí obor názvů (obor názvů <xref:System.Xml.XPath.XPathNavigator> je umístěn na po volání <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metoda následuje řadu volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metoda) je následující.  
  
-   Když umístěný na `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Když umístěný na `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Když umístěný na `root`:`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Třída vrací uzly oboru názvů v pořadí zpětné dokumentu. Proto <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> v podstatě přejde na poslední uzel oboru názvů v aktuálním oboru.  
  
 Následující příklady ukazují, co jsou obory názvů vrácený <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody s <xref:System.Xml.XPath.XPathNamespaceScope> výčtu zadané pro různé obory v dokumentu XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Když umístěný na `child2`, pořadí obor názvů (obor názvů <xref:System.Xml.XPath.XPathNavigator> je umístěn na po volání <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metoda následuje řady volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metoda) je následující.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`, a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, a `xmlns="http://www.contoso.com"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator> Třída vrací uzly oboru názvů v pořadí zpětné dokumentu. Proto <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> v podstatě přejde na poslední uzel oboru názvů v aktuálním oboru.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Navigace v sadě uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Extrahování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
