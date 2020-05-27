---
title: Main () a argumenty příkazového řádku – Průvodce programováním v C#
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
ms.openlocfilehash: 723884dd448232777ae2cfeac5bfcf5ea24363b0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007738"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Argumenty Main () a příkazového řádku (Průvodce programováním v C#)

`Main`Metoda je vstupním bodem aplikace v jazyce C#. (Knihovny a služby nevyžadují `Main` metodu jako vstupní bod.) Po spuštění aplikace `Main` je metoda první vyvolanou metodou.

V programu v jazyce C# může být pouze jeden vstupní bod. Pokud máte více než jednu třídu, která má `Main` metodu, je nutné zkompilovat program s `-main` možností kompilátoru pro určení, kterou `Main` metodu použít jako vstupní bod. Další informace naleznete v části [-Main (možnosti kompilátoru C#)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Přehled

- `Main`Metoda je vstupním bodem spustitelného programu; je místo, kde se ovládací prvek program spouští a končí.
- `Main`je deklarován uvnitř třídy nebo struktury. `Main`musí být [statický](../../language-reference/keywords/static.md) a nemusí být [veřejný](../../language-reference/keywords/public.md). (V předchozím příkladu obdrží výchozí přístup [Private](../../language-reference/keywords/private.md).) Nadřazené třídy nebo struktury není nutné provádět staticky.
- `Main`může mít buď `void` , `int` nebo, počínaje jazykem C# 7,1, `Task` nebo `Task<int>` návratový typ.
- Pokud a pouze pokud `Main` vrátí `Task` nebo `Task<int>` , deklaraci `Main` může obsahovat [`async`](../../language-reference/keywords/async.md) modifikátor. Všimněte si, že to konkrétně vylučuje `async void Main` metodu.
- `Main`Metoda může být deklarována s `string[]` parametrem, který obsahuje argumenty příkazového řádku nebo bez něj. Při použití sady Visual Studio k vytváření aplikací pro Windows můžete zadat parametr ručně nebo jinak použít <xref:System.Environment.GetCommandLineArgs> metodu k získání [argumentů příkazového řádku](command-line-arguments.md). Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem. Na rozdíl od jazyka C a C++ se název programu nepovažuje za první argument příkazového řádku v `args` poli, ale je prvním prvkem <xref:System.Environment.GetCommandLineArgs> metody.

Následuje seznam platných `Main` podpisů:

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

Předchozí příklady používají modifikátor veřejného přístupového objektu. To je typické, ale není nutné.

Sčítání `async` a `Task` `Task<int>` návratové typy zjednodušují kód programu, když aplikace konzoly potřebují spustit a `await` asynchronní operace v `Main` .

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Průvodce programováním v C#](../index.md)
- [Metody](../classes-and-structs/methods.md)
- [V programu v jazyce C#](../inside-a-program/index.md)
