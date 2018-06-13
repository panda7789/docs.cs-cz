---
title: Main() a argumenty příkazového řádku (C# Průvodce programováním)
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
ms.openlocfilehash: 03d6e7185a0a16589fb612724be52ce51e813173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332365"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() a argumenty příkazového řádku (C# Průvodce programováním)

`Main` Metoda je vstupní bod aplikace v jazyce C#. (Knihovny a služby nevyžadují `Main` metoda jako vstupní bod.) Při spuštění aplikace `Main` je první metody, která je volána metoda.

 Může existovat pouze jeden vstupní bod v programu v C#. Pokud máte více než jednu třídu, která má `Main` metoda, je nutné kompilovat s vaším programem **/main** – možnost kompilátoru k určení, které `Main` metoda se má použít jako vstupní bod. Další informace najdete v tématu [/Main (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Přehled

- `Main` Metoda je vstupní bod spustitelný program, je kde ovládacího prvku programu spuštění a ukončení.
- `Main` je deklarovaná ve třídě nebo struktuře. `Main` musí být [statické](../../../csharp/language-reference/keywords/static.md) a nemusí být [veřejné](../../../csharp/language-reference/keywords/public.md). (V předchozím příkladu, obdrží přístup výchozí [privátní](../../../csharp/language-reference/keywords/private.md).) Nadřazených třídě nebo struktuře nemusí být statická.
- `Main` mohou mít buď `void`, `int`, nebo, počínaje C# 7.1, `Task`, nebo `Task<int>` návratovým typem.
- Jenom v případě `Main` vrátí `Task` nebo `Task<int>`, deklaraci `Main` může zahrnovat [ `async` ](../../language-reference/keywords/async.md) modifikátor. Všimněte si, že konkrétně vyloučeny `async void Main` metoda.
- `Main` Metoda lze deklarovat, bez ohledu `string[]` parametr, který obsahuje argumenty příkazového řádku. Když pomocí sady Visual Studio k vytvoření aplikace systému Windows, můžete můžete ručně přidat parametr jinak použít <xref:System.Environment> třída získat argumenty příkazového řádku. Parametry jsou přečíst jako nové indexované argumenty příkazového řádku. Na rozdíl od C a C++ nepovažuje se název programu jako první argument příkazového řádku.

Přidání `async` a `Task`, `Task<int>` vrátit typy zjednodušuje kódu programu, když je potřeba spustit konzolové aplikace a `await` asynchronních operací v `Main`.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také
[Sestavování pomocí programu csc.exe v příkazovém řádku](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
[V programu v jazyce C#](../../../csharp/programming-guide/inside-a-program/index.md)  
