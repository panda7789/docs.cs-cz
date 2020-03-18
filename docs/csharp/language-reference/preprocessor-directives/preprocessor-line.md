---
title: '#řádek – odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 79033fa652af62c76d54737fbf0a0b47cf3aae99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712491"
---
# <a name="line-c-reference"></a>#line (referenční dokumentace jazyka C#)

`#line`umožňuje upravit číslování řádků kompilátoru a (volitelně) výstup názvu souboru pro chyby a upozornění.

Následující příklad ukazuje, jak nahlásit dvě upozornění přidružená k číslům řádků. Směrnice `#line 200` vynutí číslo dalšího řádku na 200 (i když je `#line` výchozí hodnota #6) a až do další směrnice bude název souboru vykázán jako "Zvláštní". Směrnice `#line default` vrátí číslování řádků na výchozí číslování, které počítá řádky, které byly přečíslovány předchozí směrnicí.

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

Kompilace vytváří následující výstup:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Poznámky

Směrnice `#line` může být použita v automatizovaném, mezikroku v procesu sestavení. Pokud byly například řádky odebrány z původního souboru zdrojového kódu, ale přesto jste chtěli, aby kompilátor generoval výstup na `#line`základě původního číslování řádků v souboru, můžete řádky odebrat a potom simulovat původní číslování řádků pomocí aplikace .

Směrnice `#line hidden` skryje po sobě jdoucí řádky z ladicího programu, tak, že `#line hidden` když `#line` vývojář kroky prostřednictvím kódu, všechny řádky mezi a další směrnice (za předpokladu, že není další `#line hidden` směrnice) bude přešel. Tuto možnost lze také použít k povolení ASP.NET rozlišovat mezi uživatelem definovaným a strojově generovaným kódem. Přestože ASP.NET je primárním spotřebitelem této funkce, je pravděpodobné, že ji využije více zdrojových generátorů.

Direktiva `#line hidden` nemá vliv na názvy souborů nebo čísla řádků v hlášení chyb. To znamená, že pokud dojde k chybě ve skrytém bloku, kompilátor ohlásí aktuální název souboru a číslo řádku chyby.

Směrnice `#line filename` určuje název souboru, který se má zobrazit ve výstupu kompilátoru. Ve výchozím nastavení se používá skutečný název souboru zdrojového kódu. Název souboru musí být v uvozovkách ("") a musí mu předcházet číslo řádku.

Soubor zdrojového kódu může `#line` mít libovolný počet směrnic.

## <a name="example-1"></a>Příklad 1

Následující příklad ukazuje, jak ladicí program ignoruje skryté řádky v kódu. Při spuštění příkladu se zobrazí tři řádky textu. Však při nastavení bodu přerušení, jak je znázorněno v příkladu a hit F10 krokovat kód, zjistíte, že ladicí program ignoruje skryté čáry. Všimněte si také, že i v případě, že nastavíte bod přerušení na skryté čáry, ladicí program bude stále ignorovat.

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

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
