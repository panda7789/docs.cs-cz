---
title: "Funkční vs. Procedurální programování (technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b6aa8ce45afdb68f7ff544b8c8f2f5e1e4a79533
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Funkční vs. Procedurální programování (technologie LINQ to XML) (C#)
Existují různé typy aplikací XML:  
  
-   Některé aplikace trvat zdroj XML – dokumenty a vytváření nových dokumentů XML, které se nacházejí v různých obrazce než dokumenty zdroje.  
  
-   Některé aplikace trvat zdroj XML – dokumenty a vytvořit výsledek dokumenty ve formuláři úplně jiné, jako jsou soubory HTML nebo CSV text.  
  
-   Některé aplikace trvat zdroj XML – dokumenty a vložit záznamů do databáze.  
  
-   Některé aplikace trvat data z jiného zdroje, jako je například databáze a vytvářet dokumenty XML z něj.  
  
 Tyto nejsou všechny typy aplikací, XML, ale toto jsou reprezentativní sadu typy funkcí, které programátory XML musí implementovat.  
  
 Se všemi z těchto typů aplikací existují dva přístupy kontrastní, které může provádět vývojář:  
  
-   Funkční konstrukce deklarativní přístup.  
  
-   Změna stromu XML v paměti pomocí procedurální kódu.  
  
 Technologie LINQ to XML podporuje obou přístupů.  
  
 Pokud používáte funkční přístup, napíšete transformace, které provádějí dokumenty zdroje a generovat úplně nové dokumenty výsledek s požadovaný tvar.  
  
 Při úpravě strom XML na místě, můžete napsat kód, který prochází a přejde na uzly ve stromu XML v paměti, vkládání, odstraňování a změny uzly podle potřeby.  
  
 Technologie LINQ to XML můžete použít s buď přístup. Můžete použít stejné třídy a v některých případech stejné metody. Struktura a cílů dva přístupy se však velmi liší. Například v různých situacích jedno nebo jiných přístup se často mají lepší výkon a použít více nebo méně paměti. Kromě toho jeden nebo jiných přístupu bude jednodušší k zápisu a yield další udržovatelného kódu.  
  
 Tyto dva přístupy, na rozdíl od aktualizovaného najdete v sekci [vs úpravy stromu XML v paměti. Funkční konstrukce (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Kurz týkající se funkční transformace zápis, najdete v části [čistý funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML přehled programování (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
