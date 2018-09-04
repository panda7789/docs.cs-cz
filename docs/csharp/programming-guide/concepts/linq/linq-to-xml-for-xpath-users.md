---
title: LINQ to XML pro uživatele jazyka XPath (C#)
ms.date: 07/20/2015
ms.assetid: 91774511-1dca-4f06-ac0b-913746f104fe
ms.openlocfilehash: c5c3d94c218f712a127ad313d3b000174644f9dd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516403"
---
# <a name="linq-to-xml-for-xpath-users-c"></a>LINQ to XML pro uživatele jazyka XPath (C#)
Tato sada témat zobrazit počet výrazů XPath a jejich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ekvivalenty.  
  
 Všechny příklady používají funkce XPath v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , který je rozšiřující metody v zpřístupní <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>. Příklady provedení výraz XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] výrazu. Každý příklad poté porovnává výsledky oba dotazy a ověřuje, že je funkčně ekvivalentní výraz XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu. Jak oba typy dotazů vrací uzlů ze stromu XML, je provedeno porovnání výsledků dotazu pomocí referenční identity.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Porovnání jazyka XPath a technologie LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Poskytuje přehled o podobnostech a rozdílech mezi XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Postupy: vyhledání podřízeného elementu (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|Porovná osu XPath podřízený element pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metody.<br /><br /> Je přidružený výraz XPath:`"DeliveryNotes"`.|  
|[Postupy: vyhledání seznamu podřízených elementů (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Porovná ose XPath podřízené prvky do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> osy.<br /><br /> Je přidružený výraz XPath:`"./*"`|  
|[Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|Jak získat kořenový element, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"/PurchaseOrders"`|  
|[Postupy: vyhledání následnických elementů (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|Jak získat následovnické elementy s určitým názvem jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"//Name"`|  
|[Postupy: filtrování atributu (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Jak získat Následnické prvky se zadaným názvem a atribut se zadanou hodnotou, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`".//Address[@Type='Shipping']"`|  
|[Postupy: vyhledání souvisejících elementů (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|Jak získat element výběru se na atribut, který je uvedené hodnotou jiného elementu, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Postupy: vyhledání elementů v Namespace (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace-xpath-linq-to-xml.md)|Použití jazyka XPath porovná <xref:System.Xml.XmlNamespaceManager> třídy s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> vlastnost <xref:System.Xml.Linq.XName> tříd pro práci s obory názvů XML.<br /><br /> Je přidružený výraz XPath:`"./aw:*"`|  
|[Postupy: vyhledání předcházejících elementů (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Porovnání jazyka XPath `preceding-sibling` osy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podřízené <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> osy.<br /><br /> Je přidružený výraz XPath:`"preceding-sibling::*"`|  
|[Postupy: vyhledání potomků podřízeného elementu (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Jak získat následnickým elementům podřízeného elementu s konkrétním názvem XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"./Paragraph//Text/text()"`|  
|[Postupy: vyhledání sjednocení dvou cest k umístění (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml.md)|Použití operátoru sjednocení, porovná <code>&#124;</code>, ve výrazu XPath s <xref:System.Linq.Enumerable.Concat%2A> operátor standardního dotazu v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:<code>"//Category&#124;//Price"</code>|  
|[Postupy: vyhledání uzlů na stejné úrovni (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Jak najít všechny na stejné úrovni uzlu, které mají konkrétní název, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"../Book"`|  
|[Postupy: Vyhledání atributu nadřazeného elementu (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Přejděte do nadřazeného elementu a najít přidružený atribut pomocí XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"../@id"`|  
|[Postupy: vyhledání atributů elementů na stejné úrovni s konkrétním názvem (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml.md)|Vyhledání konkrétních atributů na stejné úrovni kontextu uzlu, jejichž výraz XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"``../Book/@id``"`|  
|[Postupy: vyhledání elementů s konkrétním atributem (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml.md)|Jak najít al elementy, které obsahují konkrétní atribut, pomocí XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"./*[@Select]"`|  
|[Postupy: vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position-xpath-linq-to-xml.md)|Postup k zjištění prvek na základě jeho relativní pozice pomocí XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"Test[position() >= 2 and position() <= 4]"`|  
|[Postupy: vyhledání okamžité předcházející na stejné úrovni (XPath – LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Jak najít okamžité předchozí úrovni uzlu pomocí XPath porovná a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> Je přidružený výraz XPath:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XPath?displayProperty=nameWithType>  
- [Dotazování na stromy XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)  
- [Zpracování dat XML pomocí modelu dat XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
