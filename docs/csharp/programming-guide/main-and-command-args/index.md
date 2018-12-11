---
title: Main() a argumenty příkazového řádku - C# Průvodce programováním pro službu
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
ms.openlocfilehash: e9fcee86f8a3daed73adebb1f4ce3e16f7ea2042
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237087"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() a argumenty příkazového řádku (C# Programming Guide)

`Main` Metoda je vstupní bod aplikace v jazyce C#. (Knihoven a služeb nevyžadují `Main` metoda jako vstupní bod.) Při spuštění aplikace `Main` metody je první metoda, která je vyvolána.

 Může existovat pouze jeden vstupní bod v programu v jazyce C#. Pokud máte více než jednu třídu, která má `Main` metodu, musí zkompilujete program se **/main** – možnost kompilátoru k určení `Main` metody pro použití jako vstupní bod. Další informace najdete v tématu [/Main (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Přehled

- `Main` Metoda je vstupním bodem spustitelný program; je ve kterém ovládací prvek programu začíná a končí.
- `Main` je deklarované uvnitř třídy nebo struktury. `Main` musí být [statické](../../../csharp/language-reference/keywords/static.md) a nemusí být [veřejné](../../../csharp/language-reference/keywords/public.md). (V předchozím příkladu přijme výchozí přístup [privátní](../../../csharp/language-reference/keywords/private.md).) Nadřazené třídy nebo struktury se musí být statické.
- `Main` mohou mít buď `void`, `int`, nebo od verze C# 7.1, `Task`, nebo `Task<int>` návratového typu.
- Pouze v případě `Main` vrátí `Task` nebo `Task<int>`, deklarace `Main` mohou zahrnovat [ `async` ](../../language-reference/keywords/async.md) modifikátor. Všimněte si, že to vylučuje `async void Main` metody.
- `Main` Metody mohou být deklarovány s nebo bez něj `string[]` parametr, který obsahuje argumenty příkazového řádku. Při používání sady Visual Studio k vytváření aplikací pro Windows, které můžete ručně přidejte parametr jinak použít <xref:System.Environment> třídy získat argumenty příkazového řádku. Parametry se načtou jako argumenty příkazového řádku nulový index. Na rozdíl od jazyka C a C++ název aplikace není považován za první argument příkazového řádku.

Přidání `async` a `Task`, `Task<int>` vrátí typy zjednodušuje kód programu při konzolové aplikace, musí spustit a `await` asynchronních operací v `Main`.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [V programu v jazyce C#](../../../csharp/programming-guide/inside-a-program/index.md)  
