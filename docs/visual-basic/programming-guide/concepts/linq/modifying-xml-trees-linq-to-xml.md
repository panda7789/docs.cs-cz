---
title: Změna stromů XML (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: e524088ac6ccde3a46de7547379eb82f9760fd57
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959520"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Změna stromů XML (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je úložiště v paměti pro stromu XML. Po načtení nebo parsovat stromu XML ze zdroje, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňuje měnit stromové struktuře na místě a potom serializaci stromu, možná ukládají do souboru nebo v odesílání dat ke vzdálenému serveru.  
  
 Při úpravě stromu v místě, můžete použít některé metody, jako <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Je však jiný přístup, který se má použít pro vygenerování nové větve s obrazcem různé funkční konstrukce. V závislosti na typy změn, které je třeba provést na vašich stromu XML a v závislosti na velikosti stromu tento přístup může být více robustní a jednodušší vývoj. V první tématu v této části porovnává tyto dva přístupy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Porovná změna stromu XML v paměti do funkční konstrukce.|  
|[Přidání elementů, atributů a uzlů do stromu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Poskytuje informace o přidání elementů, atributů nebo uzlů do stromu XML.|  
|[Změna elementů, atributů a uzlů ve stromu XML](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Poskytuje informace o změnách stávající elementy, atributy a uzly.|  
|[Odebrání elementů, atributů a uzlů ze stromu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Poskytuje informace o odebrání elementů, atributů nebo uzlů ze stromu XML.|  
|[Zachování dvojic název/hodnota (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Popisuje, jak udržovat informace o aplikaci, která nejlépe se ukládají jako dvojice název/hodnota, například informace o konfiguraci nebo globální nastavení.|  
|[Postupy: Změna Namespace pro celý strom XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Ukazuje, jak přesunout do jiného stromu XML z jednoho oboru názvů.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
