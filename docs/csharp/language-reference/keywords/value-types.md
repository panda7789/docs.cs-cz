---
title: Typy hodnot (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 3bbaea9247d975c27ed6f49dedb749312f675296
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331847"
---
# <a name="value-types-c-reference"></a>Typy hodnot (Referenční dokumentace jazyka C#)
Typy hodnot se skládá ze dvou hlavních kategorií:  
  
-   [Struktury](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Výčty](../../../csharp/language-reference/keywords/enum.md)  
  
 Struktury spadá do následujících kategorií:  
  
-   Číselné typy  
  
    -   [Celočíselné typy](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Typy s plovoucí desetinnou čárkou](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   Struktury definované uživatelem.  
  
## <a name="main-features-of-value-types"></a>Hlavní funkce typů hodnot  
 Proměnné, které jsou založené na hodnotách přímo obsahovat hodnoty. Přiřazení jednu proměnnou typu hodnoty na jiné kopie omezením hodnoty. Tím se liší od přiřazení proměnné referenčního typu, který zkopíruje odkaz na objekt, ale nikoli samotného objektu.  
  
 Všechny hodnotové typy jsou implicitně odvozena z <xref:System.ValueType?displayProperty=nameWithType>.  
  
 Na rozdíl od v případě typů odkazu nelze odvodit nový typ z typu hodnoty. Nicméně, jako jsou typy odkazů, struktury mohou implementovat rozhraní.  
  
 Na rozdíl od typy odkazů, nemůže obsahovat typ hodnoty `null` hodnotu. Ale [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md) funkci povolit pro typy hodnot má být přiřazena k `null`.  
  
 Každý hodnotový typ má implicitní výchozí konstruktor, který inicializuje výchozí hodnota tohoto typu. Informace o výchozí hodnoty typů hodnot najdete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="main-features-of-simple-types"></a>Hlavní funkce jednoduché typy  
 Některé jednoduché typy – tyto celé číslo na jazyk C# – jsou aliasy typů rozhraní .NET Framework System. Například [int](../../../csharp/language-reference/keywords/int.md) je alias pro <xref:System.Int32?displayProperty=nameWithType>. Úplný seznam aliasů naleznete v tématu [tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 Konstantní výrazy, jehož operandy jsou všechny jednoduchý typ konstanty, jsou vyhodnocovány v době kompilace.  
  
 Jednoduché typy může být inicializována pomocí literálů. Například "A" je literál typu `char` a 2001 je literál typu `int`.  
  
## <a name="initializing-value-types"></a>Inicializace typů hodnot  
 Lokální proměnné v jazyce C# musí být inicializován před jejich použití. Například může prohlásit místní proměnné bez inicializace jako v následujícím příkladu:  
  
```csharp  
int myInt;  
```  
  
 Nelze ji použít předtím, než ji inicializovat. Můžete inicializovat pomocí následujícího příkazu:  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Tento příkaz je ekvivalentem následujícího příkazu:  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 Můžete samozřejmě máte deklaraci a inicializaci ve stejném příkazu jako v následujících příkladech:  
  
```csharp  
int myInt = new int();  
```  
  
 – nebo –  
  
```csharp  
int myInt = 0;  
```  
  
 Použití [nové](../../../csharp/language-reference/keywords/new.md) operátor volá výchozí konstruktor třídy určitého typu a přiřadí výchozí hodnotu proměnné. V předchozím příkladu, výchozí konstruktor přiřazena hodnota `0` k `myInt`. Další informace o hodnoty přiřazené voláním výchozí konstruktory, naleznete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Pomocí uživatelem definované typy [nové](../../../csharp/language-reference/keywords/new.md) k vyvolání výchozího konstruktoru. Například následující příkaz volá výchozí konstruktor třídy `Point` struktury:  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Po tomto volání struktury považuje je jednoznačně přiřazovat; To znamená všech jejích členů jsou inicializovány na výchozích hodnotách.  
  
 Další informace o operátoru new najdete v tématu [nové](../../../csharp/language-reference/keywords/new.md).  
  
 Informace o formátování výstupu číselné typy najdete v tématu [tabulka formátování číselných výsledků](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [Referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
- [Typy s možnou hodnotou Null](../../programming-guide/nullable-types/index.md)  
