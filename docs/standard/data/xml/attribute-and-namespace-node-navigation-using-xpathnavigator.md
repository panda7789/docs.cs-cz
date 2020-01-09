---
title: Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
ms.openlocfilehash: 6809a2a47a9ca25a16a9be75a0a8a8b03f98a21d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711152"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator
Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje dvě sady navigačních metod, první sada, která je nalezena v [uzlu nastavení navigace pomocí třídy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) , slouží k navigaci mezi *uzly* v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument>. Druhá sada popsaná v tomto tématu se používá k procházení *uzlů atributu a oboru názvů* v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument>.  
  
## <a name="attribute-node-navigation"></a>Navigace v uzlu atributu  
 Atributy jsou vlastnosti prvku, nikoli podřízené položky elementu. Toto rozlišení je důležité z důvodu metod <xref:System.Xml.XPath.XPathNavigator> třídy, která se používá pro navigaci uzlů na stejné úrovni, nadřazených a podřízených uzlech.  
  
 Například metody <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> nejsou použity k přechodu z prvku na atribut nebo mezi atributy. Namísto toho atributy mají odlišné metody navigace.  
  
 Níže jsou uvedené metody navigace atributů třídy <xref:System.Xml.XPath.XPathNavigator>.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Pokud je aktuální uzel prvkem, můžete použít vlastnost <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> k zobrazení, zda existují atributy přidružené k elementu. Jakmile je známo, že element má atributy, existuje více metod pro přístup k atributům. Chcete-li načíst jediný atribut z prvku, použijte metodu <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A>. Chcete-li přesunout <xref:System.Xml.XPath.XPathNavigator> do konkrétního atributu, použijte metodu <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>. Můžete také iterovat přes každý atribut elementu pomocí metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>, následovanou více voláními metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>.  
  
> [!NOTE]
> Když je objekt <xref:System.Xml.XPath.XPathNavigator> umístěn na uzlu atributu nebo oboru názvů, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody vždy vracejí `false`a nemají žádný vliv na pozici <xref:System.Xml.XPath.XPathNavigator>. Výjimkou jsou metody <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>a <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>.  
  
## <a name="namespace-node-navigation"></a>Navigace v uzlu oboru názvů  
 Každý prvek má přidruženou sadu uzlů oboru názvů, jeden pro každou jedinečnou předponu oboru názvů, která je svázána s identifikátorem URI oboru názvů v oboru pro element (včetně předpony XML vázané na obor názvů `http://www.w3.org/XML/1998/namespace`, který je implicitně deklarován v každém dokumentu XML) a jeden pro výchozí obor názvů, pokud je jeden v oboru pro element. Element je nadřazená každé z těchto názvů uzlů; uzel oboru názvů však není podřízených objektů svého nadřízeného elementu.  
  
 Stejně jako u atributů nejsou metody <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> použity k přechodu z prvku na uzel oboru názvů nebo mezi uzly oboru názvů. Místo toho uzly oboru názvů mají odlišné metody navigace.  
  
 Níže jsou uvedené metody pro navigaci oboru názvů třídy <xref:System.Xml.XPath.XPathNavigator>.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 V oboru je vždy alespoň jeden uzel oboru názvů pro libovolný prvek v dokumentu XML. Toto je uzel oboru názvů s předponou `xml` a identifikátorem URI oboru názvů `http://www.w3.org/XML/1998/namespace`. Chcete-li načíst identifikátor URI oboru názvů v oboru daného konkrétní předpony, použijte metodu <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A>. Chcete-li přesunout objekt <xref:System.Xml.XPath.XPathNavigator> do konkrétního uzlu oboru názvů, použijte metodu <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>. Můžete také iterovat přes každý uzel oboru názvů v oboru pro element pomocí metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> následované více voláními metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>.  
  
> [!NOTE]
> Když je objekt <xref:System.Xml.XPath.XPathNavigator> umístěn na uzlu atributu nebo oboru názvů, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody vždy vracejí `false`a nemají žádný vliv na pozici <xref:System.Xml.XPath.XPathNavigator>. Výjimkou jsou metody <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>a <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>.  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Výčet XPathNamespaceScope  
 Při navigaci v uzlech oboru názvů <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody lze volat pomocí parametru <xref:System.Xml.XPath.XPathNamespaceScope>. Tyto metody se chovají jinak než jejich protějšky, které jsou volány bez parametrů. Výčet <xref:System.Xml.XPath.XPathNamespaceScope> obsahuje hodnoty <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>nebo <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 Následující příklady znázorňují, jaké obory názvů jsou vráceny <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody v různých oborech v dokumentu XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekvence oboru názvů (obor názvů, na kterou je <xref:System.Xml.XPath.XPathNavigator> umístěn po volání metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> následované řadou volání metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>) je následující.  
  
- Při umístění na `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Při umístění na `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- Při umístění na `root`: `xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> Třída <xref:System.Xml.XPath.XPathNavigator> vrací uzly oboru názvů v obráceném pořadí dokumentů. Proto <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> v podstatě přesune na poslední uzel oboru názvů v aktuálním oboru.  
  
 Následující příklady znázorňují, jaké obory názvů jsou vráceny <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody s výčtem <xref:System.Xml.XPath.XPathNamespaceScope> zadaným v různých oborech v dokumentu XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Pokud je umístěn na `child2`, pořadí oboru názvů (obor názvů, na kterém <xref:System.Xml.XPath.XPathNavigator> umístěn po volání metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> následované řadou volání metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>) je následující.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`a `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`a `xmlns="http://www.contoso.com"`.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> Třída <xref:System.Xml.XPath.XPathNavigator> vrací uzly oboru názvů v obráceném pořadí dokumentů. Proto <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> v podstatě přesune na poslední uzel oboru názvů v aktuálním oboru.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Navigace v sadě uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Extrahování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
