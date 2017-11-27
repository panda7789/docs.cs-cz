---
title: "Úprava XML stromů (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de66788186f3ffd09560d8eacdebbbaa5edf067c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>Úprava XML stromů (technologie LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]je úložiště v paměti pro strom XML. Po načíst a analyzovat strom XML ze zdroje, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňuje měnit stromové struktuře na místě a pak serializovat stromu, případně ho uložit do souboru nebo odeslání na vzdálený server.  
  
 Při úpravě stromu v místě, použijete některé metody, jako například <xref:System.Xml.Linq.XContainer.Add%2A>.  
  
 Je však jiný přístup, kde je použít funkční konstrukce vygenerovat novou větev s jinou obrazce. V závislosti na typech změn, které musíte udělat na vaše strom XML a v závislosti na velikosti stromu tento přístup může být robustnější a usnadňují vývoj. První téma v této části porovnání těchto dvou přístupů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Změna stromové struktury v paměti XML vs. Funkční konstrukce (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|Porovná úprava strom XML v paměti, aby funkční konstrukce.|  
|[Přidání prvky, atributy a uzly na strom XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|Poskytuje informace o přidání prvky, atributy a uzly na strom XML.|  
|[Úprava prvky, atributy a uzly ve stromu XML](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|Poskytuje informace o úpravě existující prvky, atributy a uzly.|  
|[Odebrání prvky, atributy a uzly ze stromu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|Poskytuje informace o odebrání prvky, atributy a uzly ve stromové struktuře XML.|  
|[Zachování dvojice název hodnota (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|Popisuje, jak udržovat informace o aplikaci, která je lepší je ponechat jako dvojice název/hodnota, například informace o konfiguraci nebo globální nastavení.|  
|[Postupy: Změna Namespace pro strom celý XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|Ukazuje, jak přesunout strom XML z jednoho oboru názvů do jiné.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
