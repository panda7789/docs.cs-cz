---
title: '#řádek (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 08ba94ec3f1799f858e098bd2c0e059b7f45af2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="line-c-reference"></a>#line (referenční dokumentace jazyka C#)
`#line` Umožňuje změnit číslo řádku kompilátoru a (volitelně) název výstupního souboru chyby a upozornění. Tento příklad ukazuje, jak vytvářet sestavu dvě upozornění související s čísla řádků. `#line 200` – Direktiva vynutí číslo řádku, které má být 200 (i když výchozí hodnota je #7) a dokud další #line – direktiva, název souboru budou hlášené jako "Zvláštní". Směrnice výchozí #line vrátí číslování k jeho výchozí číslování, řádek, který zjistí, kolik řádků se označuje jako v předchozí direktivě.  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 `#line` – Direktiva mohou být používány na automatické, zprostředkující krok v procesu sestavení. Například pokud řádky byly odebrány z původního souboru se zdrojovým kódem, ale přesto chtěli kompilátoru generovat výstup na základě původní řádku číslování v souboru, můžete odstranit řádky a pak simulovat původní řádek číslování s `#line`.  
  
 `#line hidden` – Direktiva skryje po sobě jdoucích řádků ze ladicího programu, tak, že když vývojáři kroky prostřednictvím kód, všechny řádků mezi `#line hidden` a další `#line` – direktiva (za předpokladu, že není jiná `#line hidden` – direktiva) bude mít stupně přes. Tuto možnost lze také povolit ASP.NET k rozlišení mezi kódu uživatelem definované a generované počítače. I když primární příjemce této funkce je technologie ASP.NET, je pravděpodobné, že další zdroje, které budou generátory používat ho.  
  
 A `#line hidden` – direktiva nemá vliv na názvy souborů nebo čísla řádků v zasílání zpráv o chybách. To znamená je-li k chybě v skrytá bloku, kompilátor zprávu aktuální soubor název a řádek číslo chyby.  
  
 `#line filename` – Direktiva Určuje název souboru, který se má zobrazit ve výstupu kompilátoru. Ve výchozím nastavení se používá skutečný název souboru se zdrojovým kódem. Název souboru musí být v uvozovkách ("") a musí předcházet číslo řádku.  
  
 Zdrojový soubor může mít libovolný počet `#line` direktivy.  
  
## <a name="example-1"></a>Příklad 1  
 Následující příklad ukazuje, jak ladicího programu ignoruje skryté řádky v kódu. Při spuštění v příkladu, zobrazí se tří řádků textu. Ale nastavit bod přerušení, jak je znázorněno v příkladu, a stiskněte tlačítko F10 procházet kód, si všimněte, že ladicí program ignoruje skrytá řádku. Všimněte si také, že i v případě, že nastavíte bod zalomení na řádku Skrytá, ladicího programu bude stále ji ignorovat.  
  
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
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
