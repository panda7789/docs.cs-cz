---
title: new – – operátor (Referenční dokumentace jazyka C#)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243944"
---
# <a name="new-operator-c-reference"></a>new – – operátor (Referenční dokumentace jazyka C#)
Použít k vytvoření objektů a vyvolávání konstruktorů. Příklad:  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 Používá se také k vytváření instancí anonymních typů:  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 `new` Operátor slouží také k vyvolání výchozího konstruktoru pro typy hodnot. Příklad:  
  
```csharp
int i = new int();  
```  
  
 V předchozím příkazu `i` je inicializován na `0`, což je výchozí hodnota pro typ `int`. Příkaz má stejný účinek jako následující:  
  
```csharp
int i = 0;  
```  
  
 Úplný seznam výchozích hodnot, naleznete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Mějte na paměti, že se jedná o chybu deklarovat výchozí konstruktor [struktura](../../../csharp/language-reference/keywords/struct.md) vzhledem k tomu, že každý typ hodnoty implicitně nemá veřejný výchozí konstruktor. Je možné deklarovat konstruktor s parametry u typu Struktura nastavit jeho počáteční hodnoty, ale to je potřeba, pouze pokud jsou požadované hodnoty jiné než výchozí.  
  
 Objekty typu hodnoty, jako jsou struktury a objekty typu odkazu, jako jsou třídy, jsou zničeny automaticky, ale objekty typu hodnoty je zničen při zničení jejich obsahující kontext, zatímco objekty typu odkazu jsou zničeny podle uvolňování paměti kolekce neurčené době po odebrání poslední odkazy na ně. Pro typy, které obsahují prostředky, jako jsou popisovače souborů nebo připojení k síti je třeba využívat deterministické vyčištění zajistit, že se prostředky, které obsahují vydávají co nejdříve. Další informace najdete v tématu [příkaz using](../../../csharp/language-reference/keywords/using-statement.md).  
  
 `new` Operátor nelze přetížit.  
  
 Pokud `new` operátor selže přidělování paměti, vyvolá výjimku, <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `struct` jsou vytvořeny a inicializovány pomocí objektů a objekt třídy `new` operátor a potom přiřadit hodnoty. Zobrazí se výchozí nastavení a přiřazené hodnoty.  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 Všimněte si, že v příkladu, který je výchozí hodnota řetězce `null`. Proto se nezobrazí.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
