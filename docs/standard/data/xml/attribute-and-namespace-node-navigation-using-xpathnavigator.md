---
title: Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4188896fb36d8535f86b245c3b1942f5a058da9b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936836"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator
<xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> [](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) Třída poskytuje dvě sady navigačních metod, první sada, která je nalezena v uzlu nastavení navigace pomocí XPathNavigator, slouží k navigaci v uzlech v objektu nebo. <xref:System.Xml.XPath.XPathNavigator> Druhá sada popsaná v tomto tématu se používá k procházení *uzlů atributu a oboru názvů* v <xref:System.Xml.XPath.XPathDocument> objektu nebo <xref:System.Xml.XmlDocument> .  
  
## <a name="attribute-node-navigation"></a>Navigace v uzlu atributu  
 Atributy jsou vlastnosti prvku, nikoli podřízené položky elementu. Toto rozlišení je důležité z důvodu metod <xref:System.Xml.XPath.XPathNavigator> třídy, které slouží k procházení uzlů na stejné úrovni, nadřazených a podřízených uzlů.  
  
 Například <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> metody a <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> nejsou použity k přechodu z prvku na atribut nebo mezi atributy. Namísto toho atributy mají odlišné metody navigace.  
  
 Níže jsou uvedené metody <xref:System.Xml.XPath.XPathNavigator> navigace atributů třídy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Pokud je aktuální uzel prvkem, můžete použít <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> vlastnost k zobrazení, zda jsou k elementu přidruženy žádné atributy. Jakmile je známo, že element má atributy, existuje více metod pro přístup k atributům. Chcete-li načíst jediný atribut z prvku, použijte <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metodu. Chcete-li <xref:System.Xml.XPath.XPathNavigator> přesunout do konkrétního atributu, <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> použijte metodu. Můžete také iterovat přes každý atribut elementu pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> metody, následováno více volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> metody.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> `false` <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> Když je <xref:System.Xml.XPath.XPathNavigator> objekt umístěn na uzlu atributu nebo oboru názvů, metody<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ,,,, a vždy vracejí, a nemají žádný vliv na pozici <xref:System.Xml.XPath.XPathNavigator>. Výjimkou jsou <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>metody, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>a. <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>  
  
## <a name="namespace-node-navigation"></a>Navigace v uzlu oboru názvů  
 Každý prvek má přidruženou sadu uzlů oboru názvů, jeden pro každou jedinečnou předponu oboru názvů, která je svázána s identifikátorem URI oboru názvů v oboru pro element (včetně `http://www.w3.org/XML/1998/namespace` předpony XML vázané na obor názvů, který je implicitně deklarován v každém dokumentu XML) a jeden pro výchozí obor názvů, pokud je jeden v oboru pro element. Element je nadřazená každé z těchto názvů uzlů; uzel oboru názvů však není podřízených objektů svého nadřízeného elementu.  
  
 Stejně jako u atributů <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> nejsou metody a <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> použity k přechodu z prvku na uzel oboru názvů nebo mezi uzly oboru názvů. Místo toho uzly oboru názvů mají odlišné metody navigace.  
  
 Níže jsou uvedené metody <xref:System.Xml.XPath.XPathNavigator> pro navigaci oboru názvů třídy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 V oboru je vždy alespoň jeden uzel oboru názvů pro libovolný prvek v dokumentu XML. Toto je uzel oboru názvů s předponou `xml` a identifikátorem `http://www.w3.org/XML/1998/namespace`URI oboru názvů. Chcete-li načíst identifikátor URI oboru názvů v oboru daného konkrétní předpony <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> , použijte metodu. Chcete-li <xref:System.Xml.XPath.XPathNavigator> přesunout objekt do konkrétního uzlu oboru názvů, <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> použijte metodu. Můžete také iterovat přes každý uzel oboru názvů v oboru pro element pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, za kterou následuje více volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> `false` <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> Když je <xref:System.Xml.XPath.XPathNavigator> objekt umístěn na uzlu atributu nebo oboru názvů, metody<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> ,,,, a vždy vracejí, a nemají žádný vliv na pozici <xref:System.Xml.XPath.XPathNavigator>. Výjimkou jsou <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>metody, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>a. <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Výčet XPathNamespaceScope  
 Při navigaci v <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> uzlech oboru názvů <xref:System.Xml.XPath.XPathNamespaceScope> lze metody volat pomocí parametru. Tyto metody se chovají jinak než jejich protějšky, které jsou volány bez parametrů. Výčet obsahuje <xref:System.Xml.XPath.XPathNamespaceScope.All>hodnoty ,<xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>nebo .<xref:System.Xml.XPath.XPathNamespaceScope.Local> <xref:System.Xml.XPath.XPathNamespaceScope>  
  
 Následující příklady znázorňují, jaké obory názvů jsou <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> vráceny <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metodami a v různých oborech v dokumentu XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekvence oboru názvů (obor názvů, <xref:System.Xml.XPath.XPathNavigator> na kterém je umístěn po <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> volání metody následované <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> řadou volání metody), je následující.  
  
- Při umístění na `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`a. `xmlns:xml="http://www.w3.org/XML/1998/namespace"`  
  
- Při umístění na `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`a. `xmlns:xml="http://www.w3.org/XML/1998/namespace"`  
  
- Při umístění na `root`:`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> Třída vrátí uzly oboru názvů v pořadí obráceného dokumentu. Proto se v podstatě přesune na poslední uzel oboru názvů v aktuálním oboru. <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
 Následující příklady znázorňují, jaké obory názvů jsou <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> vráceny <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metodami a <xref:System.Xml.XPath.XPathNamespaceScope> s výčtem určeným v různých oborech v dokumentu XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Když je umístěn `child2`na, sekvence oboru názvů (obor názvů <xref:System.Xml.XPath.XPathNavigator> , na kterém je <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> umístěn po volání metody <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> následované řadou volání metody), je následující.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, ,`xmlns:b="http://www.contoso.com/b"` ,`xmlns:xml="http://www.w3.org/XML/1998/namespace"`a. `xmlns:a="http://www.contoso.com/a"` `xmlns="http://www.contoso.com"`  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"` ,`xmlns=""`, ,`xmlns:a="http://www.contoso.com/a"`a. `xmlns:b="http://www.contoso.com/b"` `xmlns="http://www.contoso.com"`  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> Třída vrátí uzly oboru názvů v pořadí obráceného dokumentu. Proto se v podstatě přesune na poslední uzel oboru názvů v aktuálním oboru. <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Navigace v sadě uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Extrahování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML silného typu pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
