---
title: Funkční vs. Procedurální programování (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594258"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Funkční vs. Procedurální programování (LINQ to XML) (C#)
Existují různé typy aplikací XML:  
  
- Některé aplikace přijímají zdrojové dokumenty XML a vytvoří nové dokumenty XML, které se nacházejí v jiném tvaru než zdrojové dokumenty.  
  
- Některé aplikace přijímají zdrojové dokumenty XML a vytvářejí výsledné dokumenty v zcela jiném formuláři, například v HTML nebo v textových souborech CSV.  
  
- Některé aplikace přijímají zdrojové dokumenty XML a vkládají záznamy do databáze.  
  
- Některé aplikace přebírají data z jiného zdroje, jako je například databáze, a vytvářejí z nich dokumenty XML.  
  
 Nejedná se o všechny typy aplikací XML, ale jedná se o reprezentativní sadu typů funkcí, které musí programátor XML implementovat.  
  
 U všech těchto typů aplikací existují dva způsoby kontrastu, které může vývojář provést:  
  
- Funkční konstrukce s použitím deklarativního přístupu.  
  
- Úprava stromu XML v paměti pomocí procedurálního kódu.  
  
 LINQ to XML podporuje oba přístupy.  
  
 Při použití funkčního přístupu zapisujete transformace, které přijímají zdrojové dokumenty, a generují zcela nové dokumenty výsledků s požadovaným tvarem.  
  
 Při úpravách stromu XML na místě napíšete kód, který přechází do uzlů ve stromu XML v paměti, vkládání, odstraňování a upravování uzlů podle potřeby.  
  
 LINQ to XML můžete použít buď s přístupem. Použijete stejné třídy, a v některých případech stejné metody. Struktura a cíle těchto dvou přístupů se však velmi liší. Například v různých situacích bude mít jeden nebo druhý přístup často vyšší výkon a bude používat více nebo méně paměti. Kromě toho bude jeden nebo druhý přístup snazší psát a vracet více udržovatelnější kód.  
  
 Chcete-li zobrazit kontrast dvou přístupů, přečtěte si část [úprava stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Kurz týkající se psaní funkčních transformací naleznete v tématu [čistě funkční transformace jazyka XMLC#()](./introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled programování LINQ to XML (C#)](./linq-to-xml-overview.md)
