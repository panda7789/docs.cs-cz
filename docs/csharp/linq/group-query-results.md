---
title: "Výsledky dotazu skupiny"
description: "Jak výsledky skupiny."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: ca68cf96a2c27bbd1999d5445c14fc93e8e2566c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="group-query-results"></a>Výsledky dotazu skupiny

Seskupení je jedním z nejúčinnějších možnosti LINQ. Následující příklady ukazují, jak k seskupení dat různými způsoby:  
  
-   Pomocí vlastnosti jediné.  
  
-   První písmeno ve vlastnosti string.  
  
-   Podle počítaný číselný rozsah.  
  
-   Logická hodnota predikátu nebo jiných výraz.  
  
-   Pomocí složeného klíče.  
  
 Kromě toho poslední dva dotazy projektu jejich výsledky do nové anonymní typ, který obsahuje pouze student je první a poslední název. Další informace najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).  
  
## <a name="example"></a>Příklad  
 V příkladech v tomto tématu použijte následující pomocné rutiny třídy a datové zdroje.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak chcete seskupit zdrojové elementy pomocí vlastnosti jediné elementu jako klíč skupiny. V takovém případě je klíč `string`, Studentova příjmení. Je také možné použít dílčí řetězec pro klíč. Operace seskupení se pro typ používá výchozí procedury rovnosti.  
  
 Vložte následující metodu do `StudentClass` třídy. Změňte volání příkaz v `Main` metodu `sc.GroupBySingleProperty()`.  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak chcete seskupit zdrojové elementy něco jiného než vlastnost objektu pomocí pro klíč skupiny. V tomto příkladu je klíč první písmeno Studentova příjmení.  
  
 Vložte následující metodu do `StudentClass` třídy. Změňte volání příkaz v `Main` metodu `sc.GroupBySubstring()`.  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak chcete seskupit zdrojové elementy pomocí číselný rozsah jako klíč skupiny. Výsledky dotazu pak projekty do anonymní typ, který obsahuje pouze první a poslední název a percentilu rozsahu, ke kterému patří student. Anonymní typ se používá, protože není nutné k použití kompletní `Student` objekt, který chcete zobrazit výsledky. `GetPercentile`pomocné funkce pro výpočet percentilu podle Studentova průměrné skóre. Metoda vrátí celé číslo mezi 0 a 10.  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 Vložte následující metodu do `StudentClass` třídy. Změňte volání příkaz v `Main` metodu `sc.GroupByRange()`.  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak chcete seskupit pomocí výrazu Boolean porovnání zdrojové elementy. V tomto příkladu logický výraz ověřuje, zda je větší než 75 Studentova průměrná zkoušku skóre. Jako v předchozích příkladech jsou výsledky promítnout do anonymního typu, protože není potřeba kompletní zdrojový element. Všimněte si, že vlastnosti v anonymního typu stát vlastnosti `Key` člen a je přístupný pomocí názvu, když je proveden dotaz.  
  
 Vložte následující metodu do `StudentClass` třídy. Změňte volání příkaz v `Main` metodu `sc.GroupByBoolean()`.  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít anonymní typ k zapouzdření klíč, který obsahuje více hodnot. V tomto příkladu je první hodnota klíče první písmeno Studentova příjmení. Druhá hodnota klíče je logická hodnota, která určuje, zda student skóre pro magnitudu více než 85 na první zkoušku. Skupiny můžete uspořádat podle libovolných vlastností v klíči.  
  
 Vložte následující metodu do `StudentClass` třídy. Změňte volání příkaz v `Main` metodu `sc.GroupByCompositeKey()`.  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [LINQ – výrazy dotazů](index.md)  
 [Group – klauzule](../language-reference/keywords/group-clause.md)  
 [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)  
 [Provádění poddotazů na skupinách](perform-a-subquery-on-a-grouping-operation.md)  
 [Vytvoření vnořené skupiny](create-a-nested-group.md)  
 [Seskupování dat](../programming-guide/concepts/linq/grouping-data.md)
