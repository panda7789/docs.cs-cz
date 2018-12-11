---
title: extern – modifikátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 89c5ec7713c6420060310b5df90acec0cc3b088b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237865"
---
# <a name="extern-c-reference"></a>extern (Referenční dokumentace jazyka C#)

`extern` Modifikátor se používá k deklaraci metody, která je implementována externě. Běžně `extern` modifikátor se `DllImport` atribut, pokud používáte služby Interop pro volání nespravovaného kódu. V takovém případě metoda musí být deklarovány také jako `static`, jak je znázorněno v následujícím příkladu:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

`extern` – Klíčové slovo lze také definovat alias externího sestavení, který umožňuje odkazovat na různé verze stejné součásti v rámci jednoho sestavení. Další informace najdete v tématu [externí alias](extern-alias.md).

Jedná se o chybu používat [abstraktní](abstract.md) a `extern` modifikátory pro změny stejného členu. Použití `extern` modifikátor znamená, že je metoda implementována mimo kód jazyka C#, zatímco použití `abstract` modifikátor znamená, že implementace metody není k dispozici ve třídě.

Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++. Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.

## <a name="example-1"></a>Příklad 1

V tomto příkladu program přijme od uživatele řetězec a zobrazí ho v okně se zprávou. Program používá `MessageBox` metoda naimportované z knihovny User32.dll.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Příklad 2

Tento příklad znázorňuje program C#, který volá knihovnu jazyka C (nativní knihovnu DLL).

1. Vytvořte následující soubor C s názvem `cmdll.c`:

```c
// cmdll.c
// Compile with: -LD
int __declspec(dllexport) SampleMethod(int i)
{
  return i*10;
}
```

2. Otevřete okno příkazového řádku nativních nástrojů x64 (nebo x32) sady Visual Studio z adresáře instalace sady Visual Studio a zkompilovat `cmdll.c` souboru tak, že zadáte **cl -LD cmdll.c** příkazového řádku.

3. Ve stejném adresáři vytvořte následující soubor C# a pojmenujte ho `cm.cs`:

```csharp
// cm.cs
using System;
using System.Runtime.InteropServices;
public class MainClass
{
    [DllImport("Cmdll.dll")]
      public static extern int SampleMethod(int x);

    static void Main()
    {
        Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
    }
}
```

4. Otevřete okno příkazového řádku nativních nástrojů x64 (nebo x32) sady Visual Studio z adresáře instalace sady Visual Studio a zkompilovat `cm.cs` souboru tak, že zadáte:

> **CSC cm.cs** (pro x64 příkazového řádku) – nebo – **csc-platform: x 86 cm.cs** (pro x32 příkazového řádku)

Tím se vytvoří spustitelný soubor `cm.exe`.

5. Spusťte `cm.exe`. `SampleMethod` Metoda předává hodnota 5 souboru knihovny DLL, která vrací hodnotu vynásobenou 10.  Program vygeneruje následující výstup:

```
SampleMethod() returns 50.
```

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [Modifikátory](modifiers.md)  