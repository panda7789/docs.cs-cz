---
title: Statické konstruktory (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 52c52f68bc3612807b810047044aedbd2c457cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315708"
---
# <a name="static-constructors-c-programming-guide"></a>Statické konstruktory (Průvodce programováním v C#)
Statický konstruktor se používá k chybě při inicializaci žádné [statické](../../../csharp/language-reference/keywords/static.md) data, nebo provádět určité akce, které je nutné provést pouze jednou. Je volána automaticky dřív, než se vytvoří první instance nebo všechny statické členy odkazují.  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Statické konstruktory mít následující vlastnosti:  
  
-   Statický konstruktor nemá trvat modifikátory přístupu nebo mít parametry.  
  
-   Statický konstruktor je automaticky volat za účelem inicializace [třída](../../../csharp/language-reference/keywords/class.md) dřív, než se vytvoří první instance nebo všechny statické členy odkazují.  
  
-   Statický konstruktor nelze volat přímo.  
  
-   Uživatel nemá žádnou kontrolu na provedení statického konstruktoru v programu.  
  
-   Typické použití statických konstruktorů je při třídu používá soubor protokolu a konstruktor se používá k zápisu položky do tohoto souboru.  
  
-   Statické konstruktory jsou užitečné také při vytváření Obálka – třídy pro nespravovaného kódu, když konstruktor může volat `LoadLibrary` metoda.  
  
-   Pokud statického konstruktoru vyvolá výjimku, modul runtime nebude vyvolání ještě jednou a typ zůstanou Neinicializovaný po dobu jeho existence doménu aplikace, ve kterém běží váš program.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída `Bus` má statického konstruktoru. Při první instance `Bus` se vytvoří (`bus1`), statického konstruktoru je vyvolána k inicializaci třídy. Ukázkový výstup ověřuje, že statického konstruktoru spouští pouze jednou, i když dvě instance `Bus` vytváří, a aby byl spouštěn před spuštěním konstruktoru instance.  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
