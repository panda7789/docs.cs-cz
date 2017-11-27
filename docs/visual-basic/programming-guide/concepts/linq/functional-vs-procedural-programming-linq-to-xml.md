---
title: "Funkční vs. Procedurální programování (technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e47ff583146ab4258e219537cdc01821009e965
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>Funkční vs. Procedurální programování (technologie LINQ to XML) (Visual Basic)
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
  
 Tyto dva přístupy, na rozdíl od aktualizovaného najdete v sekci [vs úpravy stromu XML v paměti. Funkční konstrukce (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).  
  
 Kurz týkající se funkční transformace zápis, najdete v části [čistý funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to přehled programování v XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
