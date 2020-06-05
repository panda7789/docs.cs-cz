---
title: Osy LINQ to XML
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 757c765062b1d1ca1cddb0c559fa46ef6a0fe796
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368982"
---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ to XML osy (Visual Basic)
Po vytvoření stromu XML nebo načtení dokumentu XML do stromu XML můžete zadat dotaz na nalezení prvků a atributů a načíst jejich hodnoty.  
  
 Než budete moct napsat jakékoli dotazy, musíte pochopit [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osy. Existují dva typy metod osy: nejprve existují metody, které zavoláte na jeden <xref:System.Xml.Linq.XElement> objekt, <xref:System.Xml.Linq.XDocument> objekt nebo <xref:System.Xml.Linq.XNode> objekt. Tyto metody pracují s jedním objektem a vracejí kolekci <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> objektů, nebo <xref:System.Xml.Linq.XNode> . Za druhé existují metody rozšíření, které fungují na kolekcích a návratových kolekcích. Metody rozšíření vyčíslují zdrojovou kolekci, volají odpovídající metodu osy pro každou položku v kolekci a zřetězí výsledky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Description|  
|-----------|-----------------|  
|[Přehled OS LINQ to XML (Visual Basic)](linq-to-xml-axes-overview.md)|Definuje osy a vysvětluje, jak se používají v kontextu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazů.|  
|[Postupy: načtení kolekce elementů (LINQ to XML) (Visual Basic)](how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Zavádí <xref:System.Xml.Linq.XContainer.Elements%2A> metodu. Tato metoda načte kolekci podřízených elementů elementu.|  
|[Postupy: načtení hodnoty elementu (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Ukazuje, jak získat hodnoty prvků.|  
|[Postupy: filtrování názvů elementů (LINQ to XML) (Visual Basic)](how-to-filter-on-element-names-linq-to-xml.md)|Ukazuje, jak filtrovat názvy elementů při použití OS.|  
|[Postupy: zřetězení volání metod osy (LINQ to XML) (Visual Basic)](how-to-chain-axis-method-calls-linq-to-xml.md)|Ukazuje, jak zřetězit volání metod osy.|  
|[Postupy: načtení jednoho podřízeného elementu (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md)|Ukazuje, jak načíst jeden podřízený prvek elementu, podle názvu značky podřízeného prvku.|  
|[Postupy: načtení kolekce atributů (LINQ to XML) (Visual Basic)](how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Zavádí <xref:System.Xml.Linq.XElement.Attributes%2A> metodu. Tato metoda načte atributy elementu.|  
|[Postupy: načtení jednoho atributu (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-attribute-linq-to-xml.md)|Ukazuje, jak načíst jediný atribut prvku s ohledem na název atributu.|  
|[Postupy: načtení hodnoty atributu (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Ukazuje, jak získat hodnoty atributů.|  
|[Postupy: načtení omezené hodnoty elementu (Visual Basic)](how-to-retrieve-the-shallow-value-of-an-element.md)|Ukazuje, jak načíst neomezených hodnot elementu.|  
|[Osy integrované v jazyce v Visual Basic (LINQ to XML)](language-integrated-axes.md)|Shrnuje Visual Basic integrované osy.|  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním (LINQ to XML) (Visual Basic)](programming-guide-linq-to-xml.md)
