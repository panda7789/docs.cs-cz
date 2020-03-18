---
title: Hlavní() argumenty a argumenty příkazového řádku - Průvodce programováním jazyka C#
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75700598"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() a argumenty příkazového řádku (Průvodce programováním jazyka C#)

Metoda `Main` je vstupním bodem aplikace Jazyka C#. (Knihovny a služby `Main` nevyžadují metodu jako vstupní bod.) Při spuštění aplikace `Main` metoda je první metoda, která je vyvolána.

 V programu Jazyka C# může být pouze jeden vstupní bod. Pokud máte více než jednu `Main` třídu, která má metodu, musíte zkompilovat program s **parametrem /main** kompilátoru a určit, kterou `Main` metodu použít jako vstupní bod. Další informace naleznete [v tématu -main (C# Compiler Options)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Přehled

- Metoda `Main` je vstupním bodem spustitelného programu; to je místo, kde se spustí a končí ovládací prvek programu.
- `Main`je deklarována uvnitř třídy nebo struktury. `Main`musí být [statická](../../language-reference/keywords/static.md) a nemusí být [veřejná](../../language-reference/keywords/public.md). (V předchozím příkladu obdrží výchozí přístup [private](../../language-reference/keywords/private.md).) Ohraničující třída nebo struktura nemusí být statická.
- `Main`může mít `void`, `int`, nebo počínaje C# 7.1 , `Task`nebo `Task<int>` návratový typ.
- If a `Main` only `Task` if `Task<int>`returns a `Main` or [`async`](../../language-reference/keywords/async.md) , deklarace může obsahovat modifikátor. Všimněte si, že `async void Main` to výslovně vylučuje metodu.
- Metoda `Main` může být deklarována s parametrem `string[]` nebo bez něj, který obsahuje argumenty příkazového řádku. Při vytváření aplikací systému Windows pomocí sady Visual Studio můžete <xref:System.Environment.GetCommandLineArgs> parametr přidat ručně nebo použít metodu k získání [argumentů příkazového řádku](command-line-arguments.md). Parametry jsou čteny jako argumenty příkazového řádku s nulovým indexem. Na rozdíl od C a C++ název programu není považován za první `args` argument příkazového řádku v <xref:System.Environment.GetCommandLineArgs> poli, ale je prvním prvkem metody.

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

Přidání a `async` `Task`návratové `Task<int>` typy zjednodušuje programový kód, `await` když konzolové `Main`aplikace potřebují spustit a asynchronní operace v .

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Programovací příručka jazyka C#](../index.md)
- [Metody](../classes-and-structs/methods.md)
- [V programu v jazyce C#](../inside-a-program/index.md)
