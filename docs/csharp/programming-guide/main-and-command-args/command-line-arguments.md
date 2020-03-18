---
title: Argumenty příkazového řádku – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: d6775263e6f1afb227aa263b01d60f5181da74f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093507"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty příkazového řádku (Průvodce programováním v C#)

Argumenty můžete odeslat `Main` metodě definováním metody jedním z následujících způsobů:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Chcete-li povolit argumenty `Main` příkazového řádku v metodě v aplikaci `Main` Windows Forms, je nutné ručně upravit podpis aplikace *v program.cs*. Kód generovaný návrhářem windows `Main` forms vytvoří bez vstupního parametru. Argumenty příkazového řádku můžete také použít <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> nebo <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> k nim získat přístup z libovolného bodu v konzoli nebo v aplikaci systému Windows.

Parametr `Main` metody je <xref:System.String> pole, které představuje argumenty příkazového řádku. Obvykle můžete určit, zda existují `Length` argumenty testováním vlastnosti, například:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

Argumenty řetězce můžete také převést na <xref:System.Convert> číselné `Parse` typy pomocí třídy nebo metody. Například následující příkaz převede `string` na `long` číslo pomocí <xref:System.Int64.Parse%2A> metody:

```csharp
long num = Int64.Parse(args[0]);
```

Je také možné použít c# `long`typ , `Int64`který aliasy :

```csharp
long num = long.Parse(args[0]);
```

Můžete také použít `Convert` metodu `ToInt64` třídy k tomu, že totéž:

```csharp
long num = Convert.ToInt64(s);
```

Další informace naleznete v tématech <xref:System.Int64.Parse%2A> a <xref:System.Convert>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat argumenty příkazového řádku v aplikaci konzoly. Aplikace přebírá jeden argument za běhu, převede argument na celé číslo a vypočítá faktoriál čísla. Pokud nejsou zadány žádné argumenty, aplikace vydá zprávu, která vysvětluje správné použití programu.

Chcete-li aplikaci zkompilovat a spustit z příkazového řádku, postupujte takto:

1. Vložte následující kód do libovolného textového editoru a uložte soubor jako textový soubor s názvem *Factorial.cs*.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. Na **úvodní** obrazovce nebo v nabídce **Start** otevřete okno **příkazového řádku vývojáře** sady Visual Studio a přejděte do složky obsahující právě vytvořený soubor.

3. Chcete-li zkompilovat aplikaci, zadejte následující příkaz.
  
     `csc Factorial.cs`  
  
     Pokud vaše aplikace nemá žádné chyby kompilace, vytvoří se spustitelný soubor s názvem *Factorial.exe.*
  
4. Pro výpočet faktoriál 3 zadejte následující příkaz:
  
     `Factorial 3`  
  
5. Příkaz vytváří tento výstup:`The factorial of 3 is 6.`

> [!NOTE]
> Při spuštění aplikace v sadě Visual Studio můžete zadat argumenty příkazového řádku na [stránce Ladění, Návrháře projektu](/visualstudio/ide/reference/debug-page-project-designer).

## <a name="see-also"></a>Viz také

- <xref:System.Environment?displayProperty=nameWithType>
- [Programovací příručka jazyka C#](../index.md)
- [Argumenty Main() a příkazového řádku](index.md)
- [Jak zobrazit argumenty příkazového řádku](how-to-display-command-line-arguments.md)
- [Návratové hodnoty Main()](main-return-values.md)
- [Třídy](../classes-and-structs/classes.md)
