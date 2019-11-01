---
title: Parametry obecného typu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 992b71fa2afa6b511d09c69ade26e3b5bc13acd2
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195473"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Parametry obecného typu (C# Průvodce programováním)

V definici obecného typu nebo metody je parametr typu zástupný symbol pro konkrétní typ, který klient určí při vytvoření instance obecného typu. Obecnou třídu, jako je například `GenericList<T>` uvedená v [úvodu do obecných typů](./index.md), nelze použít, protože není ve skutečnosti typu; je větší jako plán pro určitý typ. Chcete-li použít `GenericList<T>`, musí kód klienta deklarovat a vytvořit instanci konstruovaného typu zadáním argumentu typu v lomených závorkách. Argument typu pro tuto konkrétní třídu může být jakýkoli typ rozpoznávaný kompilátorem. Lze vytvořit libovolný počet instancí konstruovaného typu, přičemž každý z nich používá jiný argument typu, a to následujícím způsobem:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
V každé z těchto instancí `GenericList<T>`je každý výskyt `T` ve třídě nahrazen v době běhu pomocí argumentu typu. Prostřednictvím této náhrady jsme vytvořili tři samostatné typy bezpečné a efektivní objekty pomocí definice jediné třídy. Další informace o tom, jak tato náhrada provádí modulem CLR, naleznete v tématu [Obecné typy v době běhu](./generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Pokyny pro pojmenovávání parametrů typu  
  
- Pojmenujte parametry obecného typu s popisnými názvy, pokud **je název jednoho** písmene zcela zřejmý a popisný název nepřidá hodnotu.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- **Zvažte** použití parametru T jako názvu parametru typu pro typ s jedním parametrem typu písmene Single.  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- **Udělejte** prefix názvů parametrů popisného typu s "T".  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- **Zvažte** označení omezení umístěných u parametru typu v názvu parametru. Například parametr omezený na `ISession` může být volán `TSession`.

Pravidlo analýzy kódu [CA1715](/visualstudio/code-quality/ca1715) lze použít k zajištění toho, že parametry typu jsou pojmenovány správně.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Obecné typy](./index.md)
- [Rozdíly mezi šablonami C++ a obecnými typy C#](./differences-between-cpp-templates-and-csharp-generics.md)
