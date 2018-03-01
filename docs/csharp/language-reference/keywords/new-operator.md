---
title: "new – – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
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
ms.openlocfilehash: 3c2b484b9872a54ce42520de77a723b9edb441a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-c-reference"></a>new – – operátor (Referenční dokumentace jazyka C#)
Slouží k vytvoření objektů a vyvolání konstruktory. Příklad:  
  
```  
Class1 obj  = new Class1();  
```  
  
 Také se používá k vytvoření instance anonymní typy:  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 `new` Operátor slouží také k vyvolání pro typy hodnot výchozí konstruktor. Příklad:  
  
```  
int i = new int();  
```  
  
 V předchozím příkazu `i` je inicializováno `0`, což je výchozí hodnota pro typ `int`. Příkaz má stejný účinek jako následující:  
  
```  
int i = 0;  
```  
  
 Úplný seznam výchozích hodnot, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Mějte na paměti, že se jedná o chybu deklarovat pro výchozí konstruktor [struktura](../../../csharp/language-reference/keywords/struct.md) vzhledem k tomu, že každý typ hodnoty implicitně má výchozí veřejný konstruktor. Je možné deklarovat parametrizované konstruktory typu Struktura k nastavení jeho počáteční hodnoty, ale to je potřeba, pouze pokud jiné než výchozí hodnoty jsou povinné.  
  
 Typ hodnoty objekty například struktury jsou vytvořené v zásobníku, zatímco odkazový typ objektů, jako jsou třídy vytvořené v haldě. Oba typy objektů jsou zničen automaticky, ale objekty na základě typů hodnotu jsou zničený, když se dostala mimo rozsah, zatímco na základě objektů odkazové typy jsou zničen neurčené během po odebrání odkazu na poslední k nim. Pro odkazové typy, které využívají pevné prostředky, jako je například velké množství paměti, obslužné rutiny souborů nebo připojení k síti je někdy žádoucí využívat deterministické dokončení zajistit, že objekt co nejdříve zničena. Další informace najdete v tématu [pomocí příkazu](../../../csharp/language-reference/keywords/using-statement.md).  
  
 `new` Operátor nemohou být přetíženy.  
  
 Pokud `new` operátor se nepodařilo přidělit paměť, vyvolá výjimku, <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `struct` objekt a objekt třídy jsou vytvořeny a inicializovány pomocí `new` operátor a potom přiřadit hodnoty. Zobrazí se výchozí hodnota a přiřazené hodnoty.  
  
 [!code-csharp[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 Všimněte si v příkladu, který je výchozí hodnota řetězce `null`. Proto se nezobrazí.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Nový](../../../csharp/language-reference/keywords/new.md)  
 [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
