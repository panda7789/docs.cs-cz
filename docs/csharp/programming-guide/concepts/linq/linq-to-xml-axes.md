---
title: Osy LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
ms.openlocfilehash: 6a27adb1c7e1dcfefda13a355700202ccda3ffab
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071910"
---
# <a name="linq-to-xml-axes-c"></a>Osy LINQ to XML (C#)
Po vytvoření stromu XML nebo načíst dokument XML do stromu XML, můžete ho najít prvky a atributy a jejich hodnoty získat dotazovat.  
  
 Než napíšete žádné dotazy, je třeba porozumět [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osy. Existují dva typy metod osy: nejprve existují metody, které můžete volat v rámci jednoho <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> objektu, nebo <xref:System.Xml.Linq.XNode> objektu. Tyto metody provádět jeden objekt a vrátí kolekci <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, nebo <xref:System.Xml.Linq.XNode> objekty. Za druhé se rozšiřující metody, které pracují s kolekcemi a vrací kolekce. Rozšiřující metody výčet zdrojové kolekce, zavolejte metodu vhodná osa pro každou položku v kolekci a zřetězit výsledky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Přehled LINQ to XML osy (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Definuje osy a vysvětluje, jak se používají v rámci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.|  
|[Postupy: načtení kolekce elementů (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Zavádí <xref:System.Xml.Linq.XContainer.Elements%2A> metody. Tato metoda načte kolekci podřízených elementů elementu.|  
|[Postupy: načtení hodnoty elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Ukazuje, jak získat hodnoty prvků.|  
|[Postupy: Filtrování názvů elementů (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Ukazuje, jak k filtrování názvů elementů při použití osy.|  
|[Postupy: zřetězení volání metod osy (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Ukazuje, jak zřetězení volání metod osy.|  
|[Postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Ukazuje, jak načíst jeden podřízený prvek elementu, vzhledem k názvu značky podřízený element.|  
|[Postupy: načtení kolekce atributů (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Zavádí <xref:System.Xml.Linq.XElement.Attributes%2A> metody. Tato metoda načte atributy elementu.|  
|[Postupy: Načtení jednoho atributu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Ukazuje, jak načíst jeden atribut elementu, název atributu.|  
|[Postupy: načtení hodnoty atributu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Ukazuje, jak získat hodnoty atributů.|  
|[Postupy: načtení mělké hodnoty elementu (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Ukazuje, jak k načtení mělké hodnoty elementu.|  
  
## <a name="see-also"></a>Viz také

- [Rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
- [Průvodce programováním (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
