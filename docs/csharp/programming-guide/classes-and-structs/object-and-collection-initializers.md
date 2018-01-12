---
title: "Inicializátory objektu a kolekce (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 628f08aaebfa209fc9cb7cfb2b506fc67d5424f9
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicializátory objektu a kolekce (Průvodce programováním v C#)
Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení. Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.  Následující příklad ukazuje, jak pomocí inicializátoru objektů s typem s názvem `Cat` a postup vyvolání výchozí konstruktor. Všimněte si, automaticky implementované vlastnosti v `Cat` třídy. Další informace najdete v tématu [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
Syntaxe inicializátory objektu umožňuje vytvoření instance, a poté přiřadí nově vytvořený objekt s její přiřazenou vlastnosti k proměnné v přiřazení.
  
## <a name="object-initializers-with-anonymous-types"></a>Inicializátory objektů s anonymními typy  
 Inicializátory objektů lze v libovolném kontextu, ale jsou užitečné zejména v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu výrazy. Výrazy dotazů využívají často [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), který lze inicializovat pouze pomocí inicializátoru objektů, jak je znázorněno v následující prohlášení.  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Povolit anonymní typy `select` klauzuli v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz výraz, který se do objektů, jehož hodnota a tvar může lišit od původního transformace objektů původní pořadí. Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci. V následujícím příkladu předpokládáme, že objekt produktu (`p`) obsahuje mnoho pole a metody, a že vás zajímá pouze při vytváření pořadí objektů, které obsahují název produktu a jednotkové ceny.  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Po provedení tohoto dotazu `productInfos` proměnná bude obsahovat objekty, které jsou přístupné z `foreach` příkaz, jak je uvedeno v následujícím příkladu:  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 Jednotlivé objekty v novém anonymním typu mají dvě veřejné vlastnosti, kterým budou přiděleny stejné názvy, jako mají vlastnosti nebo pole v původním objektu. Můžete také přejmenovat pole při vytváření anonymní typ; v následujícím příkladu se přejmenuje `UnitPrice` do `Price`.  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a>Inicializátory objektů s typy s možnou hodnotou null  
 Pokud použijete inicializátor objektu se strukturou null, dojde k chybě v době kompilace.  
  
## <a name="collection-initializers"></a>Inicializátory kolekce  
 Inicializátory kolekcí umožňují zadat jeden nebo více inicializátory elementů polí, když inicializuje kolekci zadejte této implementuje <xref:System.Collections.IEnumerable> a má `Add` s odpovídajícím podpisem jako metodu instance nebo metody rozšíření. Inicializátory prvku mohou být tvořeny jednoduchou hodnotou, výrazem nebo inicializátorem objektu. Pomocí inicializátoru kolekce nemáte zadejte několik volání `Add` metoda třídy ve zdrojovém kódu; kompilátor přidá volání.  
  
 Následující příklady znázorňují dva jednoduché inicializátory kolekce:  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 Následující kolekce inicializátoru používá inicializátory objektů se inicializovat objekty `Cat` třídy definované v předchozím příkladu. Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Můžete zadat [null](../../../csharp/language-reference/keywords/null.md) jako element v inicializátoru kolekce Pokud kolekce `Add` metoda umožňuje.  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 Můžete zadat indexované prvky, pokud kolekce podporuje indexování.  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a>Příklady

 Následující příklad kombinuje koncepty inicializátory objektu a kolekce.

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 V následujícím příkladu, k objektu, který implementuje <xref:System.Collections.IEnumerable> obsahující `Add` metoda s více parametrů umožňuje inicializátory kolekce s víc elementů na každou položku v seznamu odpovídající podpis `Add` metoda. 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 `Add`můžete použít metody `params` – klíčové slovo provést proměnný počet argumentů, jak je znázorněno v následujícím příkladu. Tento příklad ukazuje vlastní implementace indexeru také k chybě při inicializaci kolekci pomocí indexů.
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
