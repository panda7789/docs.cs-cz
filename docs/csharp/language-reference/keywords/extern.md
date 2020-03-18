---
title: extern modifikátor - C# Reference
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: c121d810e64b5fa27f105f814253c0752e028a95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713530"
---
# <a name="extern-c-reference"></a>extern (Referenční dokumentace jazyka C#)

Modifikátor `extern` se používá k deklarování metody, která je implementována externě. Běžné použití modifikátoru `extern` `DllImport` je s atributem, když používáte služby Interop pro volání do nespravovaného kódu. V tomto případě musí být metoda `static`deklarována také jako , jak je znázorněno v následujícím příkladu:

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

Klíčové `extern` slovo může také definovat alias externí sestavy, který umožňuje odkazovat na různé verze stejné součásti z jedné sestavy. Další informace naleznete v tématu [extern alias](extern-alias.md).

Je chyba použít [abstraktní](abstract.md) a `extern` modifikátory společně upravit stejný člen. Použití `extern` modifikátoru znamená, že metoda je implementována `abstract` mimo kód Jazyka C#, zatímco použití modifikátoru znamená, že implementace metody není k dispozici ve třídě.

Externí klíčové slovo má v jazyce C# omezenější použití než v jazyce C++. Chcete-li porovnat klíčové slovo C# s klíčovým slovem C++, přečtěte si informace v kapitole Určení zapojení v referenci jazyka C++.

## <a name="example-1"></a>Příklad 1

V tomto příkladu program obdrží řetězec od uživatele a zobrazí jej uvnitř okna se zprávou. Program používá `MessageBox` metodu importovoz knihovny User32.dll.

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a>Příklad 2

Tento příklad ilustruje c# program, který volá do knihovny Jazyka C (nativní knihovna DLL).

1. Vytvořte následující soubor C `cmdll.c`a pojmenujte jej :

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio a zkompilujte `cmdll.c` soubor zadáním **souboru cl -LD cmdll.c** na příkazovém řádku.

3. Ve stejném adresáři vytvořte následující soubor `cm.cs`Jazyka C# a pojmenujte jej :

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

4. Otevřete okno příkazového řádku nativních nástrojů sady Visual Studio x64 (nebo x32) z instalačního adresáře sady Visual Studio a zkompilujte `cm.cs` soubor zadáním:

    > **csc cm.cs** (pro příkazový řádek x64) - nebo- **csc -platform:x86 cm.cs** (pro příkazový řádek x32)

    Tím vytvoříte spustitelný `cm.exe`soubor .

5. Spusťte `cm.exe`. Metoda `SampleMethod` předá hodnotu 5 do souboru DLL, který vrátí hodnotu vynásobenou hodnotou 10.  Program vytváří následující výstup:

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Modifikátory](index.md)
