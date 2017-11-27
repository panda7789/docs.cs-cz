---
title: "Main() a argumenty příkazového řádku (C# Průvodce programováním)"
ms.date: 08/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab0b93a867ecf252bffd529d284ef9ddcc9163ba
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() a argumenty příkazového řádku (C# Průvodce programováním)

`Main` Metoda je vstupní bod aplikace v jazyce C#. (Knihovny a služby nevyžadují `Main` metoda jako vstupní bod.) Při spuštění aplikace `Main` je první metody, která je volána metoda.

 Může existovat pouze jeden vstupní bod v programu v C#. Pokud máte více než jednu třídu, která má `Main` metoda, je nutné kompilovat s vaším programem **/main** – možnost kompilátoru k určení, které `Main` metoda se má použít jako vstupní bod. Další informace najdete v tématu [/Main (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Přehled

- `Main` Metoda je vstupní bod spustitelný program, je kde ovládacího prvku programu spuštění a ukončení.
- `Main`je deklarovaná ve třídě nebo struktuře. `Main`musí být [statické](../../../csharp/language-reference/keywords/static.md) a nemusí být [veřejné](../../../csharp/language-reference/keywords/public.md). (V předchozím příkladu, obdrží přístup výchozí [privátní](../../../csharp/language-reference/keywords/private.md).) Nadřazených třídě nebo struktuře nemusí být statická.
- `Main`mohou mít buď `void`, `int`, nebo, počínaje C# 7.1, `Task`, nebo `Task<int>` návratovým typem.
- Jenom v případě `Main` vrátí `Task` nebo `Task<int>`, deklaraci `Main` může zahrnovat [ `async` ](../../language-reference/keywords/async.md) modifikátor. Všimněte si, že konkrétně vyloučeny `async void Main` metoda.
- `Main` Metoda lze deklarovat, bez ohledu `string[]` parametr, který obsahuje argumenty příkazového řádku. Při použití [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] k vytvoření aplikace systému Windows, můžete můžete ručně přidat parametr jinak použít <xref:System.Environment> třída získat argumenty příkazového řádku. Parametry jsou přečíst jako nové indexované argumenty příkazového řádku. Na rozdíl od C a C++ nepovažuje se název programu jako první argument příkazového řádku.

Přidání `async` a `Task`, `Task<int>` vrátit typy zjednodušuje kódu programu, když je potřeba spustit konzolové aplikace a `await` asynchronních operací v `Main`.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také
[Sestavení příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
[Průvodce programováním v C#](../../../csharp/programming-guide/index.md)
[metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
[uvnitř programu v C#](../../../csharp/programming-guide/inside-a-program/index.md)
