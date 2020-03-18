---
title: Obecné parametry typu – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8412980d35989c445d2e0a44c0b9f35e6087bb8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712179"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Parametry obecného typu (Průvodce programováním jazyka C#)

V definici obecného typu nebo metody je parametr typu zástupným symbolem pro určitý typ, který klient určí při vytváření instance obecného typu. Obecná třída, například `GenericList<T>` uvedená v [úvodu k obecným typům](./index.md), nelze použít jako-je, protože není ve skutečnosti typ; je to spíš jako plán pro typ. Chcete-li použít `GenericList<T>`, klientský kód musí deklarovat a konkretizovat vytvořený typ zadáním argumentu typu uvnitř úhlových závorek. Argument typu pro tuto konkrétní třídu může být libovolný typ rozpoznaný kompilátorem. Lze vytvořit libovolný počet instancí konstruovaného typu, z nichž každá používá jiný argument typu, a to následovně:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
V každé z těchto `GenericList<T>`instancí `T` , každý výskyt ve třídě je nahrazen za běhu s argumentem typu. Pomocí této náhrady jsme vytvořili tři samostatné typově bezpečné a efektivní objekty pomocí jedné definice třídy. Další informace o tom, jak je toto nahrazení provádí CLR, naleznete [v tématu Obecné typy v době spuštění](./generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Pokyny pro pojmenování parametrů typu  
  
- **Do** name generic type parameters with descriptive names, unless jeden název písmene je zcela vysvětlující a popisný název by nepřidal hodnotu.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- **Zvažte** použití T jako názvu parametru typu pro typy s jedním parametrem typu s jedním písmenem.  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- **Proveďte** názvy parametrů popisného typu předpony s písmenem "T".  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- **Zvažte** označení omezení umístěných na parametr typu v názvu parametru. Například parametr omezen na `ISession` může být `TSession`volána .

Pravidlo analýzy kódu [CA1715](/visualstudio/code-quality/ca1715) lze použít k zajištění, že parametry typu jsou pojmenovány odpovídajícím způsobem.
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Programovací příručka jazyka C#](../index.md)
- [Obecné typy](./index.md)
- [Rozdíly mezi šablonami C++ a obecnými typy C#](./differences-between-cpp-templates-and-csharp-generics.md)
