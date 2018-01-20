---
title: "Řetězec interpolace - C#"
description: "Zjistěte, jak funguje interpolace řetězce v jazyce C# 6"
keywords: "Rozhraní .NET, .NET core, C#, řetězec"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: b6b3ce53a08cfacfacb19266b0be216a40633352
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="string-interpolation-in-c"></a>Interpolace řetězce v jazyce C# #

Řetězec interpolace je způsob zástupné symboly v řetězci se nahrazují hodnota proměnné řetězce. Před C# 6, je tím způsobem, jak to udělat pomocí `System.String.Format`. Tento postup funguje v pořádku, ale protože ji používá číslem zástupné symboly, může být těžší ke čtení a podrobnější.

Jinými programovací jazyky předtím řetězec interpolace integrované do jazyka nějakou dobu. Například v jazyce PHP:

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

V jazyce C# 6 máme nakonec tento styl interpolace řetězec. Můžete použít `$` před řetězec k označení, že ho měli nahraďte proměnné nebo výrazy pro jejich hodnoty.

## <a name="prerequisites"></a>Požadavky
Budete muset nastavit svůj počítač ke spuštění .NET core. Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.
Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, systému macOS nebo v kontejner Docker. Budete muset nainstalovat editor vaše oblíbené kódu. Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor. Můžete však použít, ať nástroje umíte pracovat s.

## <a name="create-the-application"></a>Vytvoření aplikace

Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci .NET Core. Pokud chcete použít Generátor příkazového řádku, vytvořit adresář pro svůj projekt `interpolated`a ve své oblíbené prostředí spustíte následující příkaz:

```
dotnet new console
```

Tento příkaz vytvoří projektu jen nejzákladnější .NET core s soubor projektu *interpolated.csproj*a soubor zdrojového kódu *Program.cs*. Budete muset provést `dotnet restore` Obnovit závislosti potřebné ke kompilaci tento projekt.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Spuštění programu, použijte `dotnet run`. Měli byste vidět "Hello, World" výstup do konzoly.



## <a name="intro-to-string-interpolation"></a>Úvod do řetězce interpolace

S `System.String.Format`, zadejte "zástupné symboly" řetězec, který se nahrazují následující řetězec parametry. Například:

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

Který výstup "Moje název je Matt hájů".

V jazyce C# 6, místo použití `String.Format`, definujete interpolované řetězce je s předponou `$` symbolů a potom pomocí proměnné přímo v řetězci. Například:

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

Nemusíte používat jenom proměnné. Můžete použít libovolný výraz v hranatých závorkách. Například:

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

Které by výstup:

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a>Jak funguje řetězec interpolace

Na pozadí je tato syntaxe interpolace řetězec přeložit na String.Format kompilátorem. Ano, můžete provést [stejného typu, vy provedete krok před s String.Format](https://msdn.microsoft.com/library/dwhawy9k(v=vs.110).aspx).

Můžete například přidat odsazení a formátování čísel:

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

Výše by výstup podobný:

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

Pokud název proměnné není nalezen, bude vygenerována chybu v době kompilace.

Například:

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

Pokud je kompilovat, bude docházet k chybám:
 
* `Cannot use local variable 'adj' before it is declared`- `adj` proměnná nebyl deklarován dokud *po* interpolované řetězce.
* `The name 'otheranimal' does not exist in the current context`-názvem proměnné `otheranimal` nikdy i byla deklarována

## <a name="localization-and-internationalization"></a>Lokalizace a internacionalizace

Interpolované řetězce podporuje `IFormattable` a `FormattableString`, což může být užitečné pro internacionalizace.

Interpolované řetězce ve výchozím nastavení používá aktuální jazykovou verzi. Pokud chcete použít jinou jazykovou verzi, může ho jako přetypování`IFormattable`

Například:

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a>Závěr 

V tomto kurzu jste zjistili, jak používat funkce interpolace řetězec jazyka C# 6. Je v podstatě přesnější způsob jednoduché psaní `String.Format` příkazy se některých aspektů pro pokročilejší použití.
