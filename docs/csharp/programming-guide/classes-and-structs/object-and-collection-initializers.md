---
title: Inicializátory objektu a kolekce (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: def33041c4202c80aad9f08d1ff8d9dbbc477061
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892416"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicializátory objektu a kolekce (Průvodce programováním v C#)
Inicializátory objektů umožňují přiřadit hodnoty k jakýmkoli přístupným polím nebo vlastnostem objektu při vytváření, bez nutnosti vyvolání konstruktoru následovaného řádky příkazů přiřazení. Syntaxe inicializátoru objektu umožňuje zadat argumenty pro konstruktor, nebo tyto argumenty (a syntaxi se závorkami) vynechat.  Následující příklad ukazuje, jak použít inicializátor objektu s pojmenovaným typem `Cat` a vyvolání výchozího konstruktoru. Všimněte si použití automaticky implementované vlastnosti v `Cat` třídy. Další informace najdete v tématu [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
Syntaxi inicializátory objektů lze vytvářet instance, a poté přiřadí nově vytvořený objekt s vlastností přiřazené k proměnné v přiřazení.
  
## <a name="object-initializers-with-anonymous-types"></a>Inicializátory objektů s anonymními typy  
 Přestože inicializátory objektů lze použít v libovolném kontextu, jsou zvláště užitečná v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů. Výrazy dotazů používají často [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), které lze inicializovat pouze pomocí inicializátoru objektu, jak je znázorněno v následující deklaraci.  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Anonymní typy umožňují `select` klauzule [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu transformovat objekty původní sekvence na objekty, jejichž hodnota a tvar se může lišit od původního dotazu. Tato možnost je užitečná, pokud chcete uložit pouze část informace z jednotlivých objektů v sekvenci. V následujícím příkladu se předpokládá, že objekt produktu (`p`) obsahuje mnoho polí a metod, a že si jenom chcete vytvořit pouze sekvenci objektů, které obsahují název produktu a jednotkovou cenu.  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Při spuštění tohoto dotazu `productInfos` proměnná bude obsahovat sekvenci objektů, které mohou být přístupné v `foreach` jak je uvedeno v tomto příkladu:  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 Jednotlivé objekty v novém anonymním typu mají dvě veřejné vlastnosti, kterým budou přiděleny stejné názvy, jako mají vlastnosti nebo pole v původním objektu. Můžete také přejmenovat pole při vytváření anonymního typu; Následující příklad přejmenuje `UnitPrice` pole `Price`.  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a>Inicializátory kolekce  
 Inicializátory kolekce umožňují určit jeden nebo více inicializátorů prvku při inicializaci kolekce typu tohoto implementuje <xref:System.Collections.IEnumerable> a má `Add` s odpovídajícím podpisem jako metodu instance nebo metody rozšíření. Inicializátory prvku mohou být tvořeny jednoduchou hodnotou, výrazem nebo inicializátorem objektu. Pomocí inicializátoru kolekce není nutné zadat více volání `Add` metoda třídy ve zdrojovém kódu; volání přidá kompilátor.  
  
 Následující příklady znázorňují dva jednoduché inicializátory kolekce:  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 Následující inicializátor kolekce používá inicializátory objektů k inicializaci objektů třídy `Cat` třídy definované v předchozím příkladu. Pamatujte, že jednotlivé incializátory objektů jsou uzavřeny ve složených závorkách a odděleny čárkami.  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Můžete zadat [null](../../../csharp/language-reference/keywords/null.md) jako prvek v incializátoru kolekce Pokud kolekce `Add` metoda umožňuje.  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 Můžete zadat indexované elementy, pokud kolekce podporuje indexování.  
  
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
 
 Je znázorněno v následujícím příkladu, objekt, který implementuje <xref:System.Collections.IEnumerable> obsahující `Add` metodu s více parametry umožňuje inicializátory kolekce s více prvky každou položku v seznamu odpovídající podpis `Add` metody. 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 `Add` můžete použít metody `params` – klíčové slovo se proměnný počet argumentů, jak je znázorněno v následujícím příkladu. Tento příklad ukazuje vlastní implementaci indexer i k inicializaci kolekce pomocí indexů.
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
