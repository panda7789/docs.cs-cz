---
title: Osy LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 4a04c15357b5630de06dc0743523e5a98c91745e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780975"
---
# <a name="linq-to-xml-axes-visual-basic"></a>Osy LINQ to XML (Visual Basic)
Po vytvoření stromu XML nebo načíst dokument XML do stromu XML, můžete ho najít prvky a atributy a jejich hodnoty získat dotazovat.  
  
 Než napíšete žádné dotazy, je třeba porozumět [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osy. Existují dva typy metod osy: Nejprve, existují metody, které můžete volat v rámci jednoho <xref:System.Xml.Linq.XElement> objektu, <xref:System.Xml.Linq.XDocument> objektu, nebo <xref:System.Xml.Linq.XNode> objektu. Tyto metody provádět jeden objekt a vrátí kolekci <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, nebo <xref:System.Xml.Linq.XNode> objekty. Za druhé se rozšiřující metody, které pracují s kolekcemi a vrací kolekce. Rozšiřující metody výčet zdrojové kolekce, zavolejte metodu vhodná osa pro každou položku v kolekci a zřetězit výsledky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Přehled LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Definuje osy a vysvětluje, jak se používají v rámci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.|  
|[Postupy: Načtení kolekce elementů (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Zavádí <xref:System.Xml.Linq.XContainer.Elements%2A> metody. Tato metoda načte kolekci podřízených elementů elementu.|  
|[Postupy: Načtení hodnoty elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Ukazuje, jak získat hodnoty prvků.|  
|[Postupy: Filtrování názvů elementů (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Ukazuje, jak k filtrování názvů elementů při použití osy.|  
|[Postupy: Zřetězení volání metod osy (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Ukazuje, jak zřetězení volání metod osy.|  
|[Postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Ukazuje, jak načíst jeden podřízený prvek elementu, vzhledem k názvu značky podřízený element.|  
|[Postupy: Načtení kolekce atributů (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Zavádí <xref:System.Xml.Linq.XElement.Attributes%2A> metody. Tato metoda načte atributy elementu.|  
|[Postupy: Načtení jednoho atributu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Ukazuje, jak načíst jeden atribut elementu, název atributu.|  
|[Postupy: Načtení hodnoty atributu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Ukazuje, jak získat hodnoty atributů.|  
|[Postupy: Načtení mělké hodnoty elementu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Ukazuje, jak k načtení mělké hodnoty elementu.|  
|[Osy integrované v jazyce v jazyce Visual Basic (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Obsahuje souhrn osy integrované jazyka Visual Basic.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
