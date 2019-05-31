---
title: Parametry obecného typu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 096fce3affb9461c57ae9c0ffd57367d1b4349df
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423416"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Parametry obecného typu (C# Programming Guide)

Parametr typu v obecném typu nebo metodě, je zástupný symbol pro konkrétní typ, že klient určuje při vytváření instance obecného typu. Obecný třídy, jako například `GenericList<T>` uvedené v [Úvod do obecných typů](../../../csharp/programming-guide/generics/index.md), nelze použít jako-totiž není ve skutečnosti typu; to je více než podrobný plán pro typ. Chcete-li použít `GenericList<T>`, kód klienta musí deklarovat a vytvoření instance konstruovaný typ tak, že zadáte argument typu v lomených závorkách. Argument typu pro tuto konkrétní třídu může být libovolný typ rozpoznatelným kompilátorem. Libovolný počet instancí konstruovaný typ nelze vytvořit, každý z nich jiný typ argumentu, následujícím způsobem:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
V každé z těchto instancí `GenericList<T>`, všechny výskyty `T` ve třídě nahrazeny za běhu s argumentem typu. Prostřednictvím této nahrazení vytvořili jsme tři samostatné zajišťující bezpečnost typů a efektivní objekty pomocí definice jednu třídu. Další informace o jak toto nahrazení se provádí pomocí modulu CLR najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Parametr typu pokyny pro pojmenování  
  
- **Proveďte** název parametry obecného typu pomocí popisných názvů, pokud je jedno písmeno názvu zcela vlastní vysvětlující a popisný název nepřispěl k vyšší hodnotu.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- **Vezměte v úvahu** pomocí T jako název parametru typu u typů s jedním parametrem typu jedno písmeno.  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- **Proveďte** předpony typu popisné názvy parametrů s "T".  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- **Vezměte v úvahu** označující omezení umístí na parametr typu název parametru. Například s omezením parametru `ISession` může být volána `TSession`.

Pravidel nástroje Analýza kódu [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) slouží k zajištění, že jsou správně pojmenované parametry typu.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)
- [Rozdíly mezi šablonami C++ a obecnými typy C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
