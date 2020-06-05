---
title: Funkční vs. procedurální programování (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 0b525f13298e7402369b890516434cec47e01542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398432"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>Funkce vs. procedurální programování (LINQ to XML) (Visual Basic)
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
  
 Chcete-li zobrazit tyto dva přístupy, přečtěte si část [Úprava stromu XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).  
  
 Kurz týkající se psaní funkčních transformací najdete v tématu [čistě funkční transformace XML (Visual Basic)](pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled programování LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)
