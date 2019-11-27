---
title: Změna stromů XML (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: c946052beb612c087d26e312875b7f7950ceadf5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353177"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Úprava stromů XML (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] je úložiště v paměti pro strom XML. Po načtení nebo analýze stromu XML ze zdroje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňuje změnit tuto stromovou strukturu a poté serializovat strom, případně ho uložit do souboru nebo ho odeslat na vzdálený server.  
  
 Když upravíte strom na místě, použijete určité metody, například <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Existuje však další přístup, který slouží k vygenerování nového stromu s jiným obrazcem pomocí funkční konstrukce. V závislosti na typech změn, které je třeba provést v rámci stromu XML a v závislosti na velikosti stromu, může být tento přístup robustnější a snazší pro vývoj. První téma v této části porovnává tyto dva přístupy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Úprava struktury XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Porovná úpravu stromu XML v paměti až po funkční konstrukci.|  
|[Přidání elementů, atributů a uzlů do stromu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Poskytuje informace o přidávání prvků, atributů nebo uzlů do stromu XML.|  
|[Změna elementů, atributů a uzlů ve stromu XML](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Poskytuje informace o úpravách existujících prvků, atributů nebo uzlů.|  
|[Odebrání elementů, atributů a uzlů ze stromu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Poskytuje informace o odebírání prvků, atributů nebo uzlů ze stromu XML.|  
|[Udržování párů název/hodnota (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Popisuje, jak spravovat informace o aplikaci, které jsou nejvhodnější jako páry název/hodnota, jako jsou konfigurační informace nebo globální nastavení.|  
|[Postupy: Změna oboru názvů pro celý strom XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Ukazuje, jak přesunout strom XML z jednoho oboru názvů do jiného.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
