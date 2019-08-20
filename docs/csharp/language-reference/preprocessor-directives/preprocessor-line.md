---
title: '#odkaz na C# řádek'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: b4ac4fd3277fb53251e87321500d1b8007458037
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608535"
---
# <a name="line-c-reference"></a>#line (referenční dokumentace jazyka C#)

`#line`umožňuje upravit číslování řádků kompilátoru a (volitelně) výstup názvu souboru pro chyby a upozornění.

Následující příklad ukazuje, jak ohlásit dvě upozornění spojená s čísly řádků. Direktiva vynutí, aby číslo dalšího řádku bylo 200 (výchozí hodnota je #6), a až do další `#line` direktivy bude název souboru uveden jako "Special". `#line 200` `#line default` Direktiva vrátí číslování řádků do výchozího číslování, což spočítá řádky, které byly přečíslovány předchozí direktivou.

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

`#line` Direktiva může být použita v automatizovaném mezilehlém kroku procesu sestavení. Například pokud byly řádky odebrány z původního souboru zdrojového kódu, ale přesto jste chtěli, aby kompilátor vygeneroval výstup na základě původního číslování řádků v souboru, mohli byste odebrat řádky a potom simulovat původní číslování `#line`řádků.

Direktiva skryje po sobě následující řádky z ladicího programu, což znamená, že když postupuje vývojář pomocí kódu, všechny řádky `#line hidden` mezi a a `#line` další direktivou (za předpokladu, `#line hidden` že se nejedná o jinou direktivu). `#line hidden` zvýší se. Tato možnost slouží také k tomu, aby ASP.NET bylo možné odlišit od uživatelsky definovaného a strojově generovaného kódu. I když je ASP.NET primárním spotřebitelem této funkce, je pravděpodobnější, že ji budou využívat více generátorů zdrojů.

`#line hidden` Direktiva nemá vliv na názvy souborů nebo čísla řádků při zasílání zpráv o chybách. To znamená, že pokud ve skrytém bloku dojde k chybě, kompilátor oznámí aktuální název souboru a číslo řádku chyby.

`#line filename` Direktiva Určuje název souboru, který se má zobrazit ve výstupu kompilátoru. Ve výchozím nastavení se používá skutečný název souboru se zdrojovým kódem. Název souboru musí být v uvozovkách ("") a musí předcházet číslo řádku.

Soubor zdrojového kódu může mít libovolný počet `#line` direktiv.

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
