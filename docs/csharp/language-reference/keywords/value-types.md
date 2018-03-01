---
title: "Typy hodnot (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 281b811f2a8a1f2c364405b563f9f103899b492c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-c-reference"></a>Typy hodnot (Referenční dokumentace jazyka C#)
Typy hodnot se skládá ze dvou hlavních kategorií:  
  
-   [Struktury](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Výčty](../../../csharp/language-reference/keywords/enum.md)  
  
 Struktury spadá do následujících kategorií:  
  
-   Číselné typy  
  
    -   [Celočíselné typy](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Typy s plovoucí desetinnou čárkou](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [Decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [BOOL](../../../csharp/language-reference/keywords/bool.md)  
  
-   Struktury definované uživatelem.  
  
## <a name="main-features-of-value-types"></a>Hlavní funkce typů hodnot  
 Proměnné, které jsou založeny na typy hodnot přímo obsahovat hodnoty. Přiřazení jednu proměnnou zadejte hodnotu do jiné kopie obsažené hodnoty. To se liší od přiřazení odkaz na typ proměnné, která zkopíruje odkaz na objekt, ale ne samotný objekt.  
  
 Všechny typy hodnot implicitně odvozena z <xref:System.ValueType?displayProperty=nameWithType>.  
  
 Na rozdíl od pro odkazové typy, nemůže být nový typ odvozený od typu hodnotu. Odkazové typy, ale jako struktury můžete implementovat rozhraní.  
  
 Na rozdíl od odkazové typy nemohou obsahovat typ hodnoty `null` hodnotu. Ale [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md) funkce povolit u typů hodnot pro přiřazení ke `null`.  
  
 Každý typ hodnota má implicitní výchozí konstruktor, který inicializuje výchozí hodnota tohoto typu. Informace o výchozí hodnoty typů hodnot najdete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="main-features-of-simple-types"></a>Hlavní funkce jednoduché typy  
 Všechny jednoduché typy – tyto celé číslo na jazyka C# – jsou aliasy typy rozhraní .NET Framework systému. Například [int](../../../csharp/language-reference/keywords/int.md) je zástupce <xref:System.Int32?displayProperty=nameWithType>. Úplný seznam aliasy, najdete v části [tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 Výrazy konstant, jejichž operandy jsou všechny jednoduchý typ konstanty, jsou vyhodnocovány v době kompilace.  
  
 Jednoduché typy lze inicializovat pomocí literály. Například "A" je literál typu `char` a 2001 je literál typu `int`.  
  
## <a name="initializing-value-types"></a>Inicializace typů hodnot  
 Před použitím je nutné inicializovat místní proměnné v jazyce C#. Například může deklarovat místní proměnné bez inicializace jako v následujícím příkladu:  
  
```  
int myInt;  
```  
  
 Předtím, než je inicializovat nemůžete ji použít. Můžete inicializovat pomocí následujícího příkazu:  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Tento příkaz je ekvivalentní následující příkaz:  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 V příkazu stejné jako v následujících příkladech můžou mít samozřejmě deklaraci a inicializace:  
  
```  
int myInt = new int();  
```  
  
 – nebo –  
  
```  
int myInt = 0;  
```  
  
 Pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor volání výchozí konstruktor z konkrétního typu a přiřadí výchozí hodnota proměnné. V předchozím příkladu výchozí konstruktor přiřazenu hodnotu `0` k `myInt`. Další informace o přiřazených voláním výchozí konstruktory hodnot najdete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Uživatelem definované typy využít [nové](../../../csharp/language-reference/keywords/new.md) volat výchozí konstruktor. Například následující příkaz volá výchozí konstruktor z `Point` struktura:  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Po toto volání se považuje struct výborný přiřadit; To znamená, že všichni její členové jsou inicializovány na výchozí hodnoty.  
  
 Další informace o operátor new najdete v tématu [nové](../../../csharp/language-reference/keywords/new.md).  
  
 Informace o Formátovaní výstupu číselnými typy najdete v tématu [formátování číselných výsledků tabulky](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [Referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)
