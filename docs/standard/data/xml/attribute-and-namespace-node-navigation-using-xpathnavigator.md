---
title: Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
ms.openlocfilehash: 90c8fe7450a6ca853aaea452e30a292dbdcd9d98
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291614"
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Navigace v uzlu oborů názvů a atributů pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Třída poskytuje dvě sady navigačních metod, první sada, která je nalezena v [uzlu nastavení navigace pomocí XPathNavigator](node-set-navigation-using-xpathnavigator.md) , slouží k navigaci v *uzlech* v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo. Druhá sada popsaná v tomto tématu se používá k procházení *uzlů atributu a oboru názvů* v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo.  
  
## <a name="attribute-node-navigation"></a>Navigace v uzlu atributu  
 Atributy jsou vlastnosti prvku, nikoli podřízené položky elementu. Toto rozlišení je důležité z důvodu metod <xref:System.Xml.XPath.XPathNavigator> třídy, které slouží k procházení uzlů na stejné úrovni, nadřazených a podřízených uzlů.  
  
 Například <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody a nejsou použity k přechodu z prvku na atribut nebo mezi atributy. Namísto toho atributy mají odlišné metody navigace.  
  
 Níže jsou uvedené metody navigace atributů <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Pokud je aktuální uzel prvkem, můžete použít <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> vlastnost k zobrazení, zda jsou k elementu přidruženy žádné atributy. Jakmile je známo, že element má atributy, existuje více metod pro přístup k atributům. Chcete-li načíst jediný atribut z prvku, použijte <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> metodu. Chcete-li přesunout <xref:System.Xml.XPath.XPathNavigator> do konkrétního atributu, použijte <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> metodu. Můžete také iterovat přes každý atribut elementu pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> metody, následováno více volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> metody.  
  
> [!NOTE]
> Když <xref:System.Xml.XPath.XPathNavigator> je objekt umístěn na uzlu atributu nebo oboru názvů, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> metody,, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> vždy vracejí a `false` nemají žádný vliv na pozici <xref:System.Xml.XPath.XPathNavigator> . Výjimkou jsou <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> metody, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
## <a name="namespace-node-navigation"></a>Navigace v uzlu oboru názvů  
 Každý prvek má přidruženou sadu uzlů oboru názvů, jeden pro každou jedinečnou předponu oboru názvů, která je svázána s identifikátorem URI oboru názvů v oboru pro element (včetně předpony XML vázané na `http://www.w3.org/XML/1998/namespace` obor názvů, který je implicitně deklarován v každém dokumentu XML) a jeden pro výchozí obor názvů, pokud je jeden v oboru pro element. Element je nadřazená každé z těchto názvů uzlů; uzel oboru názvů však není podřízených objektů svého nadřízeného elementu.  
  
 Stejně jako u atributů nejsou <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> metody a použity k přechodu z prvku na uzel oboru názvů nebo mezi uzly oboru názvů. Místo toho uzly oboru názvů mají odlišné metody navigace.  
  
 Níže jsou uvedené metody pro navigaci oboru názvů <xref:System.Xml.XPath.XPathNavigator> třídy.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 V oboru je vždy alespoň jeden uzel oboru názvů pro libovolný prvek v dokumentu XML. Toto je uzel oboru názvů s předponou `xml` a identifikátorem URI oboru názvů `http://www.w3.org/XML/1998/namespace` . Chcete-li načíst identifikátor URI oboru názvů v oboru daného konkrétní předpony, použijte <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> metodu. Chcete-li přesunout <xref:System.Xml.XPath.XPathNavigator> objekt do konkrétního uzlu oboru názvů, použijte <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> metodu. Můžete také iterovat přes každý uzel oboru názvů v oboru pro element pomocí <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody, za kterou následuje více volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody.  
  
> [!NOTE]
> Když <xref:System.Xml.XPath.XPathNavigator> je objekt umístěn na uzlu atributu nebo oboru názvů, <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A> metody,, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A> , <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A> <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> vždy vracejí a `false` nemají žádný vliv na pozici <xref:System.Xml.XPath.XPathNavigator> . Výjimkou jsou <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> metody, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> a <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
### <a name="the-xpathnamespacescope-enumeration"></a>Výčet XPathNamespaceScope  
 Při navigaci v uzlech oboru <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> názvů <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> lze metody volat pomocí <xref:System.Xml.XPath.XPathNamespaceScope> parametru. Tyto metody se chovají jinak než jejich protějšky, které jsou volány bez parametrů. <xref:System.Xml.XPath.XPathNamespaceScope>Výčet obsahuje hodnoty <xref:System.Xml.XPath.XPathNamespaceScope.All> , <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml> nebo <xref:System.Xml.XPath.XPathNamespaceScope.Local> .  
  
 Následující příklady znázorňují, jaké obory názvů jsou <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> vráceny <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metodami a v různých oborech v dokumentu XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 Sekvence oboru názvů (obor názvů, na kterém <xref:System.Xml.XPath.XPathNavigator> je umístěn po volání <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody následované řadou volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody), je následující.  
  
- Při umístění na `element2` : `xmlns:books="http://www.contoso.com/books"` , `xmlns="http://www.contoso.com"` a `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- Při umístění na `element1` : `xmlns:books="http://www.contoso.com/books"` , `xmlns="http://www.contoso.com"` a `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- Při umístění na `root` :`xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator>Třída vrátí uzly oboru názvů v pořadí obráceného dokumentu. Proto se <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> v podstatě přesune na poslední uzel oboru názvů v aktuálním oboru.  
  
 Následující příklady znázorňují, jaké obory názvů jsou <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> vráceny <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metodami a s <xref:System.Xml.XPath.XPathNamespaceScope> výčtem určeným v různých oborech v dokumentu XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Když je umístěn na `child2` , sekvence oboru názvů (obor názvů, na kterém <xref:System.Xml.XPath.XPathNavigator> je umístěn po volání <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> metody následované řadou volání <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> metody), je následující.  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"` , `xmlns:a="urn:a"` , `xmlns=""` , `xmlns:b="http://www.contoso.com/b"` , `xmlns:a="http://www.contoso.com/a"` , a `xmlns="http://www.contoso.com"` `xmlns:xml="http://www.w3.org/XML/1998/namespace"` .  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"` , `xmlns:a="urn:a"` , `xmlns=""` , `xmlns:b="http://www.contoso.com/b"` , a `xmlns:a="http://www.contoso.com/a"` `xmlns="http://www.contoso.com"` .  
  
- <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator>Třída vrátí uzly oboru názvů v pořadí obráceného dokumentu. Proto se <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> v podstatě přesune na poslední uzel oboru názvů v aktuálním oboru.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](process-xml-data-using-the-xpath-data-model.md)
- [Navigace v sadě uzlů pomocí XPathNavigator](node-set-navigation-using-xpathnavigator.md)
- [Extrahování dat XML pomocí XPathNavigator](extract-xml-data-using-xpathnavigator.md)
- [Přístup k datům XML silného typu pomocí XPathNavigator](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
