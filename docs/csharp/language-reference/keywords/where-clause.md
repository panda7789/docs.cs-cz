---
title: "where – klauzule (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0324346ee5e214bf467fcb522ef781c91fa1b76f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-c-reference"></a>where – klauzule (Referenční dokumentace jazyka C#)
`where` Klauzule ve výrazu dotazu slouží k určení, které prvky ze zdroje dat bude vrácen ve výrazu dotazu. Platí Boolean podmínku (*predikát*) pro každý element source (odkazuje proměnná rozsahu) a vrátí ty, pro které je zadaná podmínka pravdivá. Výraz jeden dotaz může obsahovat více `where` klauzule a jedna klauzule může obsahovat několik predikátů podvýrazy.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `where` klauzule filtruje všechna čísla kromě těch, které jsou menší než 5. Pokud odeberete `where` klauzule, všechna čísla ze zdroje dat by vrátila. Výraz `num < 5` je predikát, který se použije pro každý prvek.  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a>Příklad  
 V rámci jednoho `where` klauzuli tolik predikáty podle potřeby můžete zadat pomocí [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) a [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operátory. V následujícím příkladu dotaz určuje dvě predikáty Chcete-li vybrat pouze sudá čísla, které jsou menší než 5.  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a>Příklad  
 A `where` klauzule může obsahovat jednu nebo více metod, které vracejí logické hodnoty. V následujícím příkladu `where` klauzule používá k určení, zda je aktuální hodnota proměnné rozsahu popisných metody.  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a>Poznámky  
 `where` Mechanismus filtrování je klauzule. Je možné umístit téměř odkudkoli ve výrazu dotazu s výjimkou nemůže být klauzuli první nebo poslední. A `where` před nebo po, může se zobrazit klauzule [skupiny](../../../csharp/language-reference/keywords/group-clause.md) klauzule v závislosti na tom, jestli máte k filtrování zdrojové elementy před nebo po jsou seskupené.  
  
 Pokud zadaným predikátem není platný pro elementy ve zdroji dat, dojde k chybě kompilace. Toto je jednou z výhod silné – kontrola typu poskytované [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
 Při kompilaci `where` – klíčové slovo je převeden na volání <xref:System.Linq.Enumerable.Where%2A> metoda standardní – operátor dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [from – klauzule](../../../csharp/language-reference/keywords/from-clause.md)  
 [Select – klauzule](../../../csharp/language-reference/keywords/select-clause.md)  
 [Filtrování dat](../../programming-guide/concepts/linq/filtering-data.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Začínáme s dotazy LINQ v jazyku C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
