---
title: Main () a argumenty příkazového řádku – C# Průvodce programováním
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: db4464cdd3d98103bbc61b824081b59cb1e01cb9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588914"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Argumenty Main () a příkazového řádku (C# Průvodce programováním)

Metoda je vstupním bodem C# aplikace. `Main` (Knihovny a služby nevyžadují `Main` metodu jako vstupní bod.) Po spuštění `Main` aplikace je metoda první vyvolanou metodou.

 V C# programu může být pouze jeden vstupní bod. Pokud máte více než jednu třídu, která má `Main` metodu, je nutné zkompilovat program pomocí možnosti kompilátoru **/Main** a určit, kterou `Main` metodu použít jako vstupní bod. Další informace naleznete v tématu [/Main (C# možnosti kompilátoru)](../../language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Přehled

- `Main` Metoda je vstupním bodem spustitelného programu; je místo, kde se ovládací prvek program spouští a končí.
- `Main`je deklarován uvnitř třídy nebo struktury. `Main`musí být [statický](../../language-reference/keywords/static.md) a nemusí být [veřejný](../../language-reference/keywords/public.md). (V předchozím příkladu obdrží výchozí přístup [Private](../../language-reference/keywords/private.md).) Nadřazené třídy nebo struktury není nutné provádět staticky.
- `Main``void`může mít C# `Task` `Task<int>` buď,, nebo, počínaje 7,1, nebo návratovým typem. `int`
- Pokud a pouze pokud `Main` `Task` vrátí `Task<int>` [nebo,`async`](../../language-reference/keywords/async.md) deklaraci můžeobsahovatmodifikátor.`Main` Všimněte si, že to konkrétně vylučuje `async void Main` metodu.
- Metoda může být deklarována s `string[]` parametrem, který obsahuje argumenty příkazového řádku nebo bez něj. `Main` Při použití sady <xref:System.Environment> Visual Studio k vytváření aplikací pro Windows můžete zadat parametr ručně nebo jinak použít třídu k získání argumentů příkazového řádku. Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem. Na rozdíl od jazyka C++C a se název programu nepovažuje za první argument příkazového řádku.

`async` Sčítání `Task` `Main` `await` a návratové typy zjednodušují kód programu, když aplikace konzoly potřebují spustit a asynchronní operace v. `Task<int>`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Průvodce programováním v jazyce C#](../index.md)
- [Metody](../classes-and-structs/methods.md)
- [V programu v jazyce C#](../inside-a-program/index.md)
