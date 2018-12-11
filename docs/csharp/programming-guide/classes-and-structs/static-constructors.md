---
title: Statické konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: fabcbb084a74334a7a1bcddb9a04cc6705caeb29
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234926"
---
# <a name="static-constructors-c-programming-guide"></a>Statické konstruktory (Průvodce programováním v C#)
Statický konstruktor slouží k inicializaci žádný [statické](../../../csharp/language-reference/keywords/static.md) data, nebo k provedení konkrétní akce, kterou je potřeba provést pouze jednou. Je volána automaticky před první instance je vytvořena nebo jsou odkazovány jakékoli statické členy.  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Statické konstruktory mají následující vlastnosti:  
  
-   Statický konstruktor není trvat modifikátory přístupu nebo mít parametry.  
  
-   Statický konstruktor je automaticky volána k inicializaci [třídy](../../../csharp/language-reference/keywords/class.md) před první instance je vytvořena nebo jsou odkazovány jakékoli statické členy.  
  
-   Statický konstruktor nelze volat přímo.  
  
-   Uživatel nemá žádnou kontrolu na při spouštění statický konstruktor se v programu.  
  
-   Typické použití statických konstruktorů je při třídu používá soubor protokolu a konstruktor se používá k zápisu položky do tohoto souboru.  
  
-   Statické konstruktory jsou také užitečné při vytváření obálkových tříd pro nespravovaný kód, konstruktor může volat `LoadLibrary` metody.  
  
-   Pokud statický konstruktor vyvolá výjimku, modul runtime nebude volat podruhé a typ zůstanou neinicializované po dobu životnosti domény aplikace, ve kterém je spuštěna aplikace.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída `Bus` má statický konstruktor. Při první instance `Bus` je vytvořen (`bus1`), je vyvolána statický konstruktor k inicializaci třídy. Ukázkový výstup ověřuje, že statický konstruktor spouští jenom jednou, i když dvě instance `Bus` jsou vytvořeny, a že běží před spuštěním konstruktoru instance.  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
