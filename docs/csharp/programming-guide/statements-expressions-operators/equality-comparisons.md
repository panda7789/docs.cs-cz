---
title: Porovnání rovnosti – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: f09d9891f79eda44c428d5509e341a54ad3a3eee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157101"
---
# <a name="equality-comparisons-c-programming-guide"></a>Porovnání rovnosti (Průvodce programováním jazyka C#)

Někdy je nutné porovnat dvě hodnoty rovnosti. V některých případech testujete *rovnost hodnot*, označovanou také jako *ekvivalence*, což znamená, že hodnoty, které jsou obsaženy v obou proměnných, jsou stejné. V ostatních případech je třeba určit, zda dvě proměnné odkazují na stejný základní objekt v paměti. Tento typ rovnosti se nazývá *referenční rovnost*nebo *identita*. Toto téma popisuje tyto dva druhy rovnosti a poskytuje odkazy na další témata pro další informace.  
  
## <a name="reference-equality"></a>Referenční rovnost

 Rovnost odkazů znamená, že dva odkazy na objekt y odkazují na stejný základní objekt. K tomu může dojít prostřednictvím jednoduchého přiřazení, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 V tomto kódu jsou vytvořeny dva objekty, ale po příkazu přiřazení oba odkazy odkazují na stejný objekt. Proto mají referenční rovnost. Pomocí <xref:System.Object.ReferenceEquals%2A> metody určete, zda dva odkazy odkazují na stejný objekt.  
  
Pojem rovnosti odkazů se vztahuje pouze na referenční typy. Objekty typu hodnoty nemohou mít rovnost odkazů, protože když je proměnné přiřazena instance typu hodnoty, je provedena kopie hodnoty. Proto nikdy nemůžete mít dvě unboxed struktury, které odkazují na stejné umístění v paměti. Navíc pokud použijete <xref:System.Object.ReferenceEquals%2A> k porovnání dvou typů hodnot, `false`výsledek bude vždy , i v případě, že hodnoty, které jsou obsaženy v objektech jsou všechny identické. Důvodem je, že každá proměnná je zabalena do samostatné instance objektu. Další informace naleznete v [tématu Jak otestovat rovnost odkazů (Identita)](./how-to-test-for-reference-equality-identity.md).

## <a name="value-equality"></a>Rovnost hodnoty

 Rovnost hodnot znamená, že dva objekty obsahují stejnou hodnotu nebo hodnoty. Pro primitivní typy hodnot, jako je [například int](../../language-reference/builtin-types/integral-numeric-types.md) nebo [bool](../../language-reference/builtin-types/bool.md), testy rovnosti hodnot jsou jednoduché. Můžete použít [==](../../language-reference/operators/equality-operators.md#equality-operator-) operátor, jak je znázorněno v následujícím příkladu.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.
if (b == a)
{  
    // The two integers are equal.  
}  
```  
  
 Pro většinu ostatních typů testování rovnosti hodnot je složitější, protože vyžaduje, abyste pochopili, jak typ definuje. Pro třídy a struktury, které mají více polí nebo vlastností, je rovnost hodnot často definována tak, aby znamenala, že všechna pole nebo vlastnosti mají stejnou hodnotu. Například dva `Point` objekty mohou být definovány jako ekvivalentní, pokud pointA.X se rovná pointB.X a pointA.Y se rovná pointB.Y.  
  
Neexistuje však žádný požadavek, aby rovnocennost byla založena na všech polích typu. Může být založen na podmnožině. Při porovnávání typů, které nevlastníte, měli byste se ujistit, že přesně pochopit, jak je definována rovnocennost pro tento typ. Další informace o tom, jak definovat rovnost hodnot ve vlastních třídách a strukturách, naleznete v [tématu Jak definovat rovnost hodnot pro typ](./how-to-define-value-equality-for-a-type.md).
  
### <a name="value-equality-for-floating-point-values"></a>Rovnost hodnot pro hodnoty s plovoucí desetinnou desetinnou desetinnou mezí

 Porovnání rovnosti hodnot s plovoucí desetinnou desetinnou desetinnou hodnotou ([double](../../language-reference/builtin-types/floating-point-numeric-types.md) a [float](../../language-reference/builtin-types/floating-point-numeric-types.md)) jsou problematické z důvodu nepřesnosti aritmetiky s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou vrstvou v binárních počítačích. Další informace naleznete v poznámkách <xref:System.Double?displayProperty=nameWithType>v tématu .  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Jak otestovat referenční rovnost (Identita)](./how-to-test-for-reference-equality-identity.md)|Popisuje, jak zjistit, zda dvě proměnné mají rovnost odkazů.|  
|[Jak definovat rovnost hodnoty pro typ](./how-to-define-value-equality-for-a-type.md)|Popisuje, jak poskytnout vlastní definici rovnosti hodnot pro typ.|  
|[Programovací příručka jazyka C#](../index.md)|Obsahuje odkazy na podrobné informace o důležitých funkcích jazyka C# a funkcích, které jsou k dispozici pro jazyk C# prostřednictvím rozhraní .NET Framework.|  
|[Typy](../types/index.md)|Obsahuje informace o systému typu C# a odkazy na další informace.|  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
