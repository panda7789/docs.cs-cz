---
title: Funkční vs. Procedurální programování (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 888c360e1b868c79d378f2fc46a26c152121300f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "44756337"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Funkční vs. Procedurální programování (LINQ to XML) (C#)
Existují různé typy aplikací XML:  
  
-   Některé aplikace trvat zdroje dokumentů XML a vytvářet nové dokumenty XML, které jsou v odlišném tvaru než dokumenty zdroje.  
  
-   Některé aplikace trvat zdroje dokumentů XML a vytvoří výsledek dokumenty v úplně jiném formuláře, jako je HTML nebo text souborů CSV.  
  
-   Některé aplikace trvat zdroje dokumentů XML a vkládání záznamů do databáze.  
  
-   Některé aplikace vzít data z jiného zdroje, jako je například databáze a vytvářet dokumenty XML z něj.  
  
 Nejsou to všechny typy aplikací XML, ale toto jsou reprezentativní sadu typů funkcí, které má programátor XML k implementaci.  
  
 Se všemi typy aplikací se používají dva přístupy kontrastní, které vývojář může trvat:  
  
-   Funkční konstrukce pomocí deklarativního přístupu.  
  
-   Změna stromu XML v paměti pomocí kódu procedury.  
  
 Technologie LINQ to XML podporuje oba přístupy.  
  
 Při použití funkční přístup, můžete napsat transformace, které používat zdroje dokumentů a generovat zcela nové dokumenty výsledek s požadovaný tvar.  
  
 Při úpravě stromu XML v místě, píšete kód, který prochází skrz a prochází uzly ve stromu XML v paměti, vkládání, odstraňování a úpravy uzlů podle potřeby.  
  
 LINQ to XML můžete použít s oběma. Použít stejné třídy a v některých případech stejné metody. Struktura a cíle tyto dvě metody jsou však velmi odlišné. Například v různých situacích, jeden nebo jiný přístup se často mají lepší výkon a použijte více nebo méně paměti. Kromě toho jeden nebo jiný přístup bude jednodušší zápis a poskytovat další udržovatelného kódu.  
  
 Tyto dva přístupy rozdíly najdete v tématu [změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Kurz týkající se zápisu funkční transformace, najdete v části [čistě funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled LINQ to XML programování (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
