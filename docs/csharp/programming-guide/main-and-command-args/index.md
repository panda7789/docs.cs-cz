---
title: Main () a argumenty příkazového řádku – C# Průvodce programováním
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
ms.openlocfilehash: 0571ec6dbc42f103ec922a6b2b13a52510640a78
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700598"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Argumenty Main () a příkazového řádku (C# Průvodce programováním)

Metoda `Main` je vstupním bodem C# aplikace. (Knihovny a služby nevyžadují jako vstupní bod metodu `Main`.) Po spuštění aplikace je metoda `Main` první vyvolanou metodou.

 V C# programu může být pouze jeden vstupní bod. Pokud máte více než jednu třídu, která má metodu `Main`, je nutné zkompilovat program pomocí možnosti kompilátoru **/Main** a určit, která `Main` metoda, která má být použita jako vstupní bod. Další informace naleznete v tématu [-Main (C# možnosti kompilátoru)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Přehled

- Metoda `Main` je vstupním bodem spustitelného programu; je to místo, kde se spouští a končí ovládací prvek programu.
- `Main` je deklarován uvnitř třídy nebo struktury. `Main` musí být [statické](../../language-reference/keywords/static.md) a nemusí být [veřejné](../../language-reference/keywords/public.md). (V předchozím příkladu obdrží výchozí přístup [Private](../../language-reference/keywords/private.md).) Nadřazené třídy nebo struktury není nutné provádět staticky.
- `Main` může mít `void`, `int`nebo, počínaje C# 7,1, `Task`nebo `Task<int>` návratový typ.
- Pokud a pouze pokud `Main` vrátí `Task` nebo `Task<int>`, deklarace `Main` může obsahovat modifikátor [`async`](../../language-reference/keywords/async.md) . Všimněte si, že to konkrétně vylučuje metodu `async void Main`.
- Metodu `Main` lze deklarovat s nebo bez `string[]` parametr, který obsahuje argumenty příkazového řádku. Při použití sady Visual Studio k vytváření aplikací pro Windows můžete zadat parametr ručně nebo jinak použít metodu <xref:System.Environment.GetCommandLineArgs> k získání [argumentů příkazového řádku](command-line-arguments.md). Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem. Na rozdíl od jazyka C++C a není název programu považován za první argument příkazového řádku v poli `args`, ale je prvním prvkem <xref:System.Environment.GetCommandLineArgs> metody.

Následuje seznam platných signatur `Main`:

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

Přidání `async` a `Task`, `Task<int>` návratové typy, zjednodušuje kód programu, když aplikace konzoly potřebují spustit a `await` asynchronní operace v `Main`.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Průvodce programováním v jazyce C#](../index.md)
- [Metody](../classes-and-structs/methods.md)
- [V programu v jazyce C#](../inside-a-program/index.md)
