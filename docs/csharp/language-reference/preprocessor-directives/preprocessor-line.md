---
title: '#odkaz na C# řádek'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712491"
---
# <a name="line-c-reference"></a>#line (referenční dokumentace jazyka C#)

`#line` umožňuje upravit číslování řádků kompilátoru a (volitelně) výstup názvu souboru pro chyby a upozornění.

Následující příklad ukazuje, jak ohlásit dvě upozornění spojená s čísly řádků. Direktiva `#line 200` vynutí, aby číslo dalšího řádku bylo 200 (i když je výchozí hodnota #6) a do další `#line` direktivy, název souboru bude hlášen jako "Special". Direktiva `#line default` vrací číslování řádků do výchozího číslování, což počítá řádky, které byly přečíslovány předchozí direktivou.

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

Kompilace generuje následující výstup:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Poznámky

Direktiva `#line` může být použita v automatizovaném mezilehlém kroku procesu sestavení. Například pokud byly řádky odebrány z původního souboru zdrojového kódu, ale přesto jste chtěli, aby kompilátor vygeneroval výstup na základě originálního číslování řádků v souboru, mohli byste odebrat řádky a potom simulovat původní číslování řádků pomocí `#line`.

Direktiva `#line hidden` skrývá po sobě jdoucí řádky z ladicího programu, což znamená, že pokud kroky pro vývojáře procházejí kódem, všechny řádky mezi `#line hidden` a další `#line`ou direktivou (za předpokladu, že se nejedná o jinou direktivu `#line hidden`), se zvýší. Tato možnost slouží také k tomu, aby ASP.NET bylo možné odlišit od uživatelsky definovaného a strojově generovaného kódu. I když je ASP.NET primárním spotřebitelem této funkce, je pravděpodobnější, že ji budou využívat více generátorů zdrojů.

Direktiva `#line hidden` neovlivňuje názvy souborů nebo čísla řádků při zasílání zpráv o chybách. To znamená, že pokud ve skrytém bloku dojde k chybě, kompilátor oznámí aktuální název souboru a číslo řádku chyby.

Direktiva `#line filename` Určuje název souboru, který se má zobrazit ve výstupu kompilátoru. Ve výchozím nastavení se používá skutečný název souboru se zdrojovým kódem. Název souboru musí být v uvozovkách ("") a musí předcházet číslo řádku.

Soubor se zdrojovým kódem může mít libovolný počet direktiv `#line`.

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje, jak ladicí program ignoruje skryté řádky v kódu. Když spustíte příklad, zobrazí se tři řádky textu. Nicméně pokud nastavíte bod přerušení, jak je znázorněno v příkladu, a stisknutím klávesy F10 projdete kód, zjistíte, že ladicí program ignoruje skrytý řádek. Všimněte si také, že i když nastavíte bod přerušení na skrytém řádku, ladicí program ho bude stále ignorovat.

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
