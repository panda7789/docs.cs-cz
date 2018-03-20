---
title: "new – – operátor (Referenční dokumentace jazyka C#)"
ms.date: 03/15/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab582cd14bc649ca8d1678a583a8f95e78c6bf7e
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2018
---
# <a name="new-operator-c-reference"></a>new – – operátor (Referenční dokumentace jazyka C#)
Slouží k vytvoření objektů a vyvolání konstruktory. Příklad:  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 Také se používá k vytvoření instance anonymní typy:  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 `new` Operátor slouží také k vyvolání pro typy hodnot výchozí konstruktor. Příklad:  
  
```csharp
int i = new int();  
```  
  
 V předchozím příkazu `i` je inicializováno `0`, což je výchozí hodnota pro typ `int`. Příkaz má stejný účinek jako následující:  
  
```csharp
int i = 0;  
```  
  
 Úplný seznam výchozích hodnot, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Mějte na paměti, že se jedná o chybu deklarovat pro výchozí konstruktor [struktura](../../../csharp/language-reference/keywords/struct.md) vzhledem k tomu, že každý typ hodnoty implicitně má výchozí veřejný konstruktor. Je možné deklarovat parametrizované konstruktory typu Struktura k nastavení jeho počáteční hodnoty, ale to je potřeba, pouze pokud jiné než výchozí hodnoty jsou povinné.  
  
 Typ hodnoty objekty, jako je například struktury a odkaz na typ objektů, jako jsou třídy zničen automaticky, ale typ hodnoty objekty budou ztraceny při jejich obsahující kontext zničení, zatímco paměti jsou zničena objekty typu odkazu kolekce neurčené během po odebrání odkazu na poslední k nim. Pro typy, které obsahují prostředky, jako jsou popisovače souborů nebo připojení k síti je třeba použít deterministický čištění zajistit, aby co nejdříve uvolnění prostředků, které obsahují. Další informace najdete v tématu [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md).  
  
 `new` Operátor nemohou být přetíženy.  
  
 Pokud `new` operátor se nepodařilo přidělit paměť, vyvolá výjimku, <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `struct` objekt a objekt třídy jsou vytvořeny a inicializovány pomocí `new` operátor a potom přiřadit hodnoty. Zobrazí se výchozí hodnota a přiřazené hodnoty.  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 Všimněte si v příkladu, který je výchozí hodnota řetězce `null`. Proto se nezobrazí.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
