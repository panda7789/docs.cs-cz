---
title: Funkční vs. Procedurální programování (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 1f713e54cefed5b1fcf8c29cd88aa7587a737327
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486944"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Funkční vs. Procedurální programování (LINQ to XML) (C#)
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
  
 Tyto dva přístupy rozdíly najdete v tématu [změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Kurz týkající se zápisu funkční transformace, najdete v části [čistě funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
