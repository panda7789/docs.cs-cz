---
title: '#řádek – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 51cffe40321aad2c91fb9a09821531545a415aec
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845918"
---
# <a name="line-c-reference"></a>#line (referenční dokumentace jazyka C#)
`#line` Umožňuje upravit kompilátoru číslování řádků a (volitelně) název výstupního souboru pro chyby a upozornění.

Následující příklad ukazuje, jak ohlásit dvě upozornění související s čísly řádků. `#line 200` Směrnice vynutí na další řádek číslo, které má být 200 (i když výchozí hodnota je #6) a až do další `#line` direktiv, název souboru se ohlásí jako "Speciální". `#line default` – Direktiva vrátí řádku číslování na jeho výchozí čísla, která vrátí počet řádků, které se označuje jako předchozí direktivou.  
  
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
Kompilace vytvoří následující výstup:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Poznámky  
 `#line` v jednom z automatizované, zprostředkující kroků v procesu sestavení, může se použít direktiva. Například pokud řádky byly odebrány z původního souboru se zdrojovým kódem, ale stále chtěla kompilátor, aby generoval výstupní založené na původní řádek číslování v souboru, můžete odebrat řádky a potom simulovat původní řádek číslování s `#line`.  
  
 `#line hidden` – Direktiva skrývá po sobě jdoucích řádků z ladicího programu, takže když vývojář provede kód, některé řádky mezi `#line hidden` a dalších `#line` – direktiva (za předpokladu, že není jiné `#line hidden` – direktiva) bude se stupňovitým přes. Tuto možnost lze také povolit ASP.NET k rozlišení mezi uživatelem a počítačem generovaný kód. I když je primární příjemce této funkce technologie ASP.NET, je pravděpodobnost, že další zdroje, které způsobí, že generátorů využije ho.  
  
 A `#line hidden` direktiva ovlivnit názvy souborů nebo čísla řádků v hlášení chyb. To znamená pokud dojde k chybě v bloku skryté, že kompilátor nahlásí aktuální soubor název a číslo řádku chyby.  
  
 `#line filename` Direktiva Určuje název souboru, které se mají zobrazit ve výstupu kompilátoru. Ve výchozím nastavení se používá skutečný název souboru se zdrojovým kódem. Název souboru musí být v dvojitých uvozovkách ("") a musí být předcházen číslo řádku.  
  
 Soubor zdrojového kódu může mít libovolný počet `#line` direktivy.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad ukazuje, jak ladicí program ignoruje skryté řádky v kódu. Při spuštění v příkladu se zobrazí tři řádky textu. Ale při nastavení přerušení, jak je znázorněno v příkladu a stiskněte F10 a krokovat kód, si všimnete, že ladicí program ignoruje řádku skryté. Všimněte si také, že i v případě, že jste nastavili přerušení na řádku skryté, ladicí program bude stále ho ignorovat.  
  
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

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
