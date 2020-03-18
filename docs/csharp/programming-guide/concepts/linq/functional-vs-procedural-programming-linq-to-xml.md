---
title: Funkční vs. procedurální programování (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594258"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Funkční vs. procedurální programování (LINQ to XML) (C#)
Existují různé typy xml aplikací:  
  
- Některé aplikace přebírají zdrojové dokumenty XML a vytvářejí nové dokumenty XML, které mají jiný tvar než zdrojové dokumenty.  
  
- Některé aplikace přebírají zdrojové dokumenty XML a vytvářejí výsledné dokumenty ve zcela jiné podobě, například textové soubory HTML nebo CSV.  
  
- Některé aplikace přebírají zdrojové dokumenty XML a vkládají záznamy do databáze.  
  
- Některé aplikace přebírají data z jiného zdroje, například z databáze, a vytvářejí z ní dokumenty XML.  
  
 Nejedná se o všechny typy aplikací XML, ale jedná se o reprezentativní sadu typů funkcí, které musí programátor XML implementovat.  
  
 U všech těchto typů aplikací existují dva kontrastní přístupy, které může vývojář použít:  
  
- Funkční konstrukce s použitím deklarativního přístupu.  
  
- Úprava stromu XML v paměti pomocí procedurálního kódu.  
  
 LINQ na XML podporuje oba přístupy.  
  
 Při použití funkčního přístupu píšete transformace, které berou zdrojové dokumenty a generují zcela nové výsledné dokumenty s požadovaným tvarem.  
  
 Při úpravách stromu XML na místě napíšete kód, který prochází a prochází uzly ve stromu XML v paměti, vkládání, odstranění a úpravy uzlů podle potřeby.  
  
 LinQ můžete použít xml s oběma přístupy. Používáte stejné třídy a v některých případech stejné metody. Struktura a cíle obou přístupů jsou však velmi odlišné. Například v různých situacích jeden nebo druhý přístup bude mít často lepší výkon a používat více či méně paměti. Kromě toho jeden nebo druhý přístup bude snazší psát a výnos více udržovatelný kód.  
  
 Chcete-li zobrazit dva přístupy v kontrastu, naleznete [v tématu Modifikace stromu XML v paměti vs funkční konstrukce (LINQ na XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Pro výuku psaní funkční transformace, naleznete v části [Čisté funkční transformace XML (C#)](./introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)
