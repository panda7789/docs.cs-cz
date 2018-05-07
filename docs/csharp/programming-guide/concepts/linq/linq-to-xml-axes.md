---
title: Technologie LINQ to XML osy (C#)
ms.date: 07/20/2015
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
ms.openlocfilehash: d12d35a6f9b02056946ba201a7bd5a961f64ba36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-axes-c"></a>Technologie LINQ to XML osy (C#)
Po vytvoření strom XML nebo načíst dokument XML do strom XML, můžete ji najít elementy a atributy a jejich hodnoty načíst dotazovat.  
  
 Než napíšete žádné dotazy, musíte pochopit [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osy. Existují dva typy metod osy: nejdřív existují metody, které zavoláte na jednom <xref:System.Xml.Linq.XElement> objekt, <xref:System.Xml.Linq.XDocument> objekt, nebo <xref:System.Xml.Linq.XNode> objektu. Tyto metody pracovat na jediný objekt a vracet kolekci <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, nebo <xref:System.Xml.Linq.XNode> objekty. Druhý existují rozšiřující metody, které pracují kolekce a vrátí kolekce. Rozšiřující metody výčet zdrojové kolekci volat metodu vhodná osa pro každou položku v kolekci a řetězení výsledky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Technologie LINQ to přehled osy XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Definuje osy a vysvětluje, jak se používají v rámci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.|  
|[Postupy: načtení kolekci elementů (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Zavádí <xref:System.Xml.Linq.XContainer.Elements%2A> metoda. Tato metoda načte kolekci podřízených elementů elementu.|  
|[Postupy: načtení hodnoty elementu (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Ukazuje, jak získat hodnoty elementů.|  
|[Postupy: filtru na názvy elementu (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Ukazuje, jak filtrovat názvy elementů při použití osy.|  
|[Postupy: tvoří řetěz volání metod osy (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Ukazuje, jak zřetězit volání metod osy.|  
|[Postupy: načtení jeden podřízený Element (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Ukazuje, jak načíst jeden podřízený element elementu, zadaný název značky podřízený element.|  
|[Postupy: načtení kolekci atributů (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Zavádí <xref:System.Xml.Linq.XElement.Attributes%2A> metoda. Tato metoda načte atributy elementu.|  
|[Postupy: načtení jeden atribut (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Ukazuje, jak načíst jeden atribut elementu, název atributu.|  
|[Postupy: načtení hodnoty atributu (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Ukazuje, jak získat hodnoty atributů.|  
|[Postupy: načtení hodnoty bez podstruktury elementu (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Ukazuje, jak načíst bez podstruktury hodnotu elementu.|  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [Průvodce programováním (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
