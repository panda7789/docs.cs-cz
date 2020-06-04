---
title: LINQ to XML pro uživatele jazyka XPath
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 7942d33831644875f390e9128965fe1c36433808
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368787"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML pro uživatele XPath (Visual Basic)

Tato sada témat zobrazuje počet výrazů XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.  
  
 Všechny příklady používají funkci XPath v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , která je k dispozici v rámci rozšiřujících metod v <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> . V příkladech se spustí výraz XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výraz. Každý příklad pak porovná výsledky obou dotazů a ověří, zda je výraz XPath funkčně ekvivalentní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu. Jak oba typy dotazů vracejí uzly ze stejného stromu XML, porovnání výsledku dotazu je provedeno pomocí referenční identity.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Description|  
|-----------|-----------------|  
|[Porovnání jazyka XPath a technologie LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Poskytuje přehled o podobnostech a rozdílech mezi XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .|  
|[Postupy: Vyhledání podřízeného elementu (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-child-element-xpath-linq-to-xml.md)|Porovná osu podřízených elementů XPath s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metodou.<br /><br /> Přidružený výraz XPath je: `"DeliveryNotes"` .|  
|[Postupy: vyhledání seznamu podřízených elementů (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Porovná osu podřízených elementů XPath s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> osou.<br /><br /> Přidružený výraz XPath je:`"./*"`|  
|[Postupy: Vyhledání kořenového elementu (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-root-element-xpath-linq-to-xml.md)|Porovná, jak získat kořenový prvek pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"/PurchaseOrders"`|  
|[Postupy: Vyhledání Potomkových elementů (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendant-elements-xpath-linq-to-xml.md)|Porovná, jak získat následníky s určitým názvem pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"//Name"`|  
|[Postupy: filtrování atributu (XPath-LINQ to XML) (Visual Basic)](how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Porovná, jak získat odvozené prvky se zadaným názvem a s atributem se zadanou hodnotou XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"./Address[@Type='Shipping']"`|  
|[Postupy: hledání souvisejících elementů (XPath-LINQ to XML) (Visual Basic)](how-to-find-related-elements-xpath-linq-to-xml.md)|Porovná, jak získat prvek pro výběr atributu, na který odkazuje hodnota jiného elementu pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"./Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Postupy: hledání elementů v oboru názvů (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-in-a-namespace.md)|Porovná použití <xref:System.Xml.XmlNamespaceManager> třídy XPath s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> vlastností <xref:System.Xml.Linq.XName> třídy pro práci s obory názvů XML.<br /><br /> Přidružený výraz XPath je:`"./aw:*"`|  
|[Postupy: Vyhledání předcházejících položek na stejné úrovni (XPath-LINQ to XML) (Visual Basic)](how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Porovná `preceding-sibling` osu XPath s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podřízenou <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> osou.<br /><br /> Přidružený výraz XPath je:`"preceding-sibling::*"`|  
|[Postupy: Vyhledání potomků podřízeného elementu (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Porovná, jak získat odvozené prvky podřízeného elementu s konkrétním názvem pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"./Paragraph//Text/text()"`|  
|[Postupy: Vyhledání sjednocení dvou cest umístění (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-union-of-two-location-paths-xpath.md)|Porovná použití operátoru Union, <code>&#124;</code> ve výrazu XPath se <xref:System.Linq.Enumerable.Concat%2A> standardní operátor dotazu v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:<code>"//Category&#124;//Price"</code>|  
|[Postupy: Vyhledání uzlů na stejné úrovni (XPath-LINQ to XML) (Visual Basic)](how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Porovná, jak najít všechny na stejné úrovni uzlu, který má konkrétní název s XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"../Book"`|  
|[Postupy: Vyhledání atributu nadřazené položky (XPath-LINQ to XML) (Visual Basic)](how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Porovná, jak přejít na nadřazený element a najít přidružený atribut pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"../@id"`|  
|[Postupy: hledání atributů na stejné úrovni s konkrétním názvem (XPath-LINQ to XML) (Visual Basic)](how-to-find-attributes-of-siblings-with-a-specific-name.md)|Porovná, jak najít konkrétní atributy na stejné úrovni kontextu uzlu pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"../Book/@id"`|  
|[Postupy: Vyhledání elementů s konkrétním atributem (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-with-a-specific-attribute.md)|Porovná, jak najít elementy Al obsahující konkrétní atribut pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"./*[@Select]"`|  
|[Postupy: hledání podřízených elementů na základě pozice (XPath-LINQ to XML) (Visual Basic)](how-to-find-child-elements-based-on-position.md)|Porovná, jak najít element na základě jeho relativní pozice pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"Test[position() >= 2 and position() <= 4]"`|  
|[Postupy: Vyhledání bezprostředního předchozího uzlu na stejné úrovni (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Porovná, jak najít bezprostřední předchozí uzel na stejné úrovni, pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Přidružený výraz XPath je:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [Dotazování na stromy XML (Visual Basic)](querying-xml-trees.md)
- [Zpracování dat XML pomocí modelu dat XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
