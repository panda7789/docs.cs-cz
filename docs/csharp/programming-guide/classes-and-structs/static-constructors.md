---
title: "Statické konstruktory (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee5448095cf06c2473c94bae542c02557918271a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
