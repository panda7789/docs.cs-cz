---
title: extern modifikátor – C# referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 5f4a4b143578603a3285b1a3bc0b1efa11840e77
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422815"
---
# <a name="extern-c-reference"></a>extern (Referenční dokumentace jazyka C#)

Modifikátor `extern` slouží k deklaraci metody, která je implementována externě. Běžné použití modifikátoru `extern` je s atributem `DllImport`, pokud používáte služby vzájemné spolupráce pro volání do nespravovaného kódu. V tomto případě musí být metoda deklarována také jako `static`, jak je znázorněno v následujícím příkladu:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

Klíčové slovo `extern` může také definovat externí alias sestavení, který umožňuje odkazování na různé verze stejné součásti v rámci jednoho sestavení. Další informace najdete v tématu [extern alias](extern-alias.md).

Použití [abstraktních](abstract.md) a `extern` modifikátorů pro úpravu stejného člena je chybné. Pomocí modifikátoru `extern` znamená, že metoda je implementována mimo C# kód, zatímco použití modifikátoru `abstract` znamená, že implementace metody není ve třídě k dispozici.

Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++. Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.

## <a name="example-1"></a>Příklad 1

V tomto příkladu program obdrží od uživatele řetězec a zobrazí jej v okně se zprávou. Program používá metodu `MessageBox` naimportovanou z knihovny User32. dll.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Příklad 2

Tento příklad ilustruje C# program, který volá do knihovny jazyka C (nativní knihovna DLL).

1. Vytvořte následující soubor C a pojmenujte ho `cmdll.c`:

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio a zkompilujte soubor `cmdll.c` tím, že na příkazovém řádku zadáte **CL-ld cmdll. c** .

3. Ve stejném adresáři vytvořte následující C# soubor a pojmenujte ho `cm.cs`:

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

4. Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio a zkompilujte soubor `cm.cs` zadáním:

    > **csc cm.cs** (pro příkazový řádek x64), nebo – **CSC-platform: x86 cm.cs** (pro příkazový řádek x32)

    Tím se vytvoří spustitelný soubor `cm.exe`.

5. Spusťte `cm.exe`. Metoda `SampleMethod` předá hodnotu 5 souboru DLL, která vrací hodnotu vynásobenou 10.  Program vytvoří následující výstup:

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
