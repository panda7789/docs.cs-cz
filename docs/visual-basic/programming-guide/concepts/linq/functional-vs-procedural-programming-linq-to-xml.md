---
title: Funkční vs. Procedurální programování (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 892c6b7113fe1efdb8e855749c86ac5f9da8cbe4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028392"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>Funkční vs. Procedurální programování (LINQ to XML) (Visual Basic)
Existují různé typy aplikací XML:  
  
- Některé aplikace trvat zdroje dokumentů XML a vytvářet nové dokumenty XML, které jsou v odlišném tvaru než dokumenty zdroje.  
  
- Některé aplikace trvat zdroje dokumentů XML a vytvoří výsledek dokumenty v úplně jiném formuláře, jako je HTML nebo text souborů CSV.  
  
- Některé aplikace trvat zdroje dokumentů XML a vkládání záznamů do databáze.  
  
- Některé aplikace vzít data z jiného zdroje, jako je například databáze a vytvářet dokumenty XML z něj.  
  
 Nejsou to všechny typy aplikací XML, ale toto jsou reprezentativní sadu typů funkcí, které má programátor XML k implementaci.  
  
 Se všemi typy aplikací se používají dva přístupy kontrastní, které vývojář může trvat:  
  
- Funkční konstrukce pomocí deklarativního přístupu.  
  
- Změna stromu XML v paměti pomocí kódu procedury.  
  
 Technologie LINQ to XML podporuje oba přístupy.  
  
 Při použití funkční přístup, můžete napsat transformace, které používat zdroje dokumentů a generovat zcela nové dokumenty výsledek s požadovaný tvar.  
  
 Při úpravě stromu XML v místě, píšete kód, který prochází skrz a prochází uzly ve stromu XML v paměti, vkládání, odstraňování a úpravy uzlů podle potřeby.  
  
 LINQ to XML můžete použít s oběma. Použít stejné třídy a v některých případech stejné metody. Struktura a cíle tyto dvě metody jsou však velmi odlišné. Například v různých situacích, jeden nebo jiný přístup se často mají lepší výkon a použijte více nebo méně paměti. Kromě toho jeden nebo jiný přístup bude jednodušší zápis a poskytovat další udržovatelného kódu.  
  
 Tyto dva přístupy rozdíly najdete v tématu [změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).  
  
 Kurz týkající se zápisu funkční transformace, najdete v části [čistě funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled LINQ to XML programování (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
