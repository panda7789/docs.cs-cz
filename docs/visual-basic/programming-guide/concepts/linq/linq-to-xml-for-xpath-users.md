---
title: LINQ to XML pro uživatele jazyka XPath (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 13c23eec1261700b15bea7f92f6c50e9231e900a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824244"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML pro uživatele jazyka XPath (Visual Basic)

Tato sada témat zobrazit počet výrazů XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.  
  
 Všechny příklady používají funkce XPath v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , který je rozšiřující metody v zpřístupní <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>. Příklady provedení výraz XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazu. Každý příklad poté porovnává výsledky oba dotazy a ověřuje, že je funkčně ekvivalentní výraz XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu. Jak oba typy dotazů vrací uzlů ze stromu XML, je provedeno porovnání výsledků dotazu pomocí referenční identity.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Porovnání jazyka XPath a technologie LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Poskytuje přehled o podobnostech a rozdílech mezi XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Postupy: Vyhledání podřízeného elementu (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|Porovná osu XPath podřízený element pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metody.<br /><br /> Je přidružený výraz XPath:`"DeliveryNotes"`.|  
|[Postupy: Vyhledání seznamu podřízených elementů (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Porovná ose XPath podřízené prvky do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> osy.<br /><br /> Je přidružený výraz XPath:`"./*"`|  
|[Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|Jak získat kořenový element, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"/PurchaseOrders"`|  
|[Postupy: Vyhledání následnických elementů (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|Jak získat následovnické elementy s určitým názvem jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"//Name"`|  
|[Postupy: Filtrovat podle atributu (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Jak získat Následnické prvky se zadaným názvem a atribut se zadanou hodnotou, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`".//Address[@Type='Shipping']"`|  
|[Postupy: Vyhledání souvisejících elementů (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|Jak získat element výběru se na atribut, který je uvedené hodnotou jiného elementu, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Postupy: Vyhledávání elementů v Namespace (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace.md)|Použití jazyka XPath porovná <xref:System.Xml.XmlNamespaceManager> třídy s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> vlastnost <xref:System.Xml.Linq.XName> tříd pro práci s obory názvů XML.<br /><br /> Je přidružený výraz XPath:`"./aw:*"`|  
|[Postupy: Vyhledání předcházejících elementů (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Porovnání jazyka XPath `preceding-sibling` osy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podřízené <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> osy.<br /><br /> Je přidružený výraz XPath:`"preceding-sibling::*"`|  
|[Postupy: Vyhledání potomků podřízeného elementu (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Jak získat následnickým elementům podřízeného elementu s konkrétním názvem XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"./Paragraph//Text/text()"`|  
|[Postupy: Vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath.md)|Použití operátoru sjednocení, porovná <code>&#124;</code>, ve výrazu XPath s <xref:System.Linq.Enumerable.Concat%2A> operátor standardního dotazu v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:<code>"//Category&#124;//Price"</code>|  
|[Postupy: Vyhledání uzlů na stejné úrovni (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Jak najít všechny na stejné úrovni uzlu, které mají konkrétní název, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"../Book"`|  
|[Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Přejděte do nadřazeného elementu a najít přidružený atribut pomocí XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"../@id"`|  
|[Postupy: Vyhledání atributů elementů na stejné úrovni s konkrétním názvem (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name.md)|Vyhledání konkrétních atributů na stejné úrovni kontextu uzlu, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"../Book/@id"`|  
|[Postupy: Vyhledání elementů s konkrétním atributem (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute.md)|Jak najít al elementy, které obsahují konkrétní atribut, pomocí XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"./*[@Select]"`|  
|[Postupy: Vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position.md)|Postup k zjištění prvek na základě jeho relativní pozice pomocí XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"Test[position() >= 2 and position() <= 4]"`|  
|[Postupy: Najít okamžité předcházející na stejné úrovni (XPath – LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Jak najít okamžité předchozí úrovni uzlu pomocí XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [Dotazování na stromy XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
- [Zpracování dat XML pomocí modelu dat XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
