---
title: Parametry obecného typu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8b9e040beea0590320a34d35ca323374f357bf2f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238192"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Obecné parametry typu (Průvodce programováním v C#)
Parametry typu v obecném typu nebo metodě, je zástupný symbol pro konkrétní typ klienta Určuje, kdy se vytvořit instanci proměnné obecného typu. Obecný třídy, jako například `GenericList<T>` uvedené v [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md), nelze použít jako-totiž není ve skutečnosti typu; to je více než podrobný plán pro typ. Chcete-li použít `GenericList<T>`, kód klienta musí deklarovat a vytvoření instance konstruovaný typ tak, že zadáte argument typu v lomených závorkách. Argument typu pro tuto konkrétní třídu může být libovolný typ rozpoznatelným kompilátorem. Libovolný počet instancí konstruovaný typ nelze vytvořit, každý z nich jiný typ argumentu, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 V každé z těchto instancí `GenericList<T>`, všechny výskyty `T` ve třídě, bude nahrazena v době běhu s argumentem typu. Prostřednictvím této nahrazení vytvořili jsme tři samostatné zajišťující bezpečnost typů a efektivní objekty pomocí definice jednu třídu. Další informace o jak toto nahrazení se provádí pomocí modulu CLR najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Parametr typu pokyny pro pojmenování  
  
-   **Proveďte** název parametry obecného typu pomocí popisných názvů, pokud je jedno písmeno názvu zcela vlastní vysvětlující a popisný název nepřispěl k vyšší hodnotu.  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **Vezměte v úvahu** pomocí T jako název parametru typu u typů s jedním parametrem typu jedno písmeno.  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **Proveďte** předpony typu popisné názvy parametrů s "T".  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **Vezměte v úvahu** označující omezení umístí na parametr typu název parametru. Například s omezením parametru `ISession` může být volána `TSession`.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
- [Rozdíly mezi šablonami C++ a obecnými typy C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
