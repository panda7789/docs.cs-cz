---
title: Porovnání rovnosti – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: 46d6881955252b21de6a92e25d65d1f76c8ec06c
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241913"
---
# <a name="equality-comparisons-c-programming-guide"></a>Porovnání rovnosti (Průvodce programováním v C#)

Někdy je nutné porovnat dvě hodnoty pro rovnost. V některých případech testujete *rovnost hodnot*, označovanou také jako *ekvivalenci*, což znamená, že hodnoty, které jsou obsaženy v těchto dvou proměnných, jsou stejné. V jiných případech je nutné určit, zda dvě proměnné odkazují na stejný základní objekt v paměti. Tento typ rovnosti se označuje jako *rovnost referencí*nebo *Identita*. Toto téma popisuje tyto dva druhy rovnosti a obsahuje odkazy na další témata, kde najdete další informace.  
  
## <a name="reference-equality"></a>Referenční rovnost

 Odkazová rovnost znamená, že dva odkazy na objekty odkazují na stejný základní objekt. K tomu může dojít prostřednictvím jednoduchého přiřazení, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 V tomto kódu jsou vytvořeny dva objekty, ale po příkazu přiřazení oba odkazy odkazují na stejný objekt. Proto mají referenční rovnost. Použijte <xref:System.Object.ReferenceEquals%2A> metodu k určení, zda dva odkazy odkazují na stejný objekt.  
  
Koncept rovnosti referencí se vztahuje pouze na typy odkazů. Objekty typu hodnoty nemohou mít referenční rovnost, protože když je instance hodnotového typu přiřazena proměnné, je vytvořena kopie hodnoty. Proto nikdy nemůžete mít dvě nezabalené struktury, které odkazují na stejné umístění v paměti. Kromě toho, pokud použijete <xref:System.Object.ReferenceEquals%2A> k porovnání dvou typů hodnot, výsledek bude vždy `false` i v případě, že hodnoty, které jsou obsaženy v objektech, jsou všechny identické. Je to proto, že každá proměnná je zabalena do samostatné instance objektu. Další informace najdete v tématu [testování rovnosti referencí (identity)](./how-to-test-for-reference-equality-identity.md).

## <a name="value-equality"></a>Hodnota rovnosti

 Hodnota rovnost znamená, že dva objekty obsahují stejnou hodnotu nebo hodnoty. U primitivních hodnot typu, jako jsou [int](../../language-reference/builtin-types/integral-numeric-types.md) nebo [bool](../../language-reference/builtin-types/bool.md), testy pro rovnost hodnot jsou jednoduché. Můžete použít [==](../../language-reference/operators/equality-operators.md#equality-operator-) operátor, jak je znázorněno v následujícím příkladu.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.
if (b == a)
{  
    // The two integers are equal.  
}  
```  
  
 U většiny ostatních typů je testování rovnosti hodnoty složitější, protože vyžaduje, abyste porozuměli tomu, jak typ definuje. Pro třídy a struktury, které mají více polí nebo vlastností, je rovnost hodnot často definována tak, že všechna pole nebo vlastnosti mají stejnou hodnotu. Například dva `Point` objekty mohou být definovány jako ekvivalentní, pokud je ukazatel Point. x roven pointB. x a pointa. y se rovná pointB. y.  
  
Neexistuje však žádný požadavek na to, aby byla rovnocennost založena na všech polích v typu. Může být založen na podmnožině. Při porovnání typů, které nevlastníte, je vhodné pochopit, zda je pro tento typ definována rovnocennost. Další informace o definování rovnosti hodnoty ve vlastních třídách a strukturách naleznete v tématu [How to define Value rovnost pro typ](./how-to-define-value-equality-for-a-type.md).
  
### <a name="value-equality-for-floating-point-values"></a>Hodnota rovnosti pro hodnoty s plovoucí desetinnou čárkou

 Porovnávání rovnosti hodnot s plovoucí desetinnou čárkou ([Double](../../language-reference/builtin-types/floating-point-numeric-types.md) a [float](../../language-reference/builtin-types/floating-point-numeric-types.md)) je problematické z důvodu nepřesnosti aritmetických operací s plovoucí desetinnou čárkou v binárních počítačích. Další informace najdete v poznámkách v tématu <xref:System.Double?displayProperty=nameWithType> .  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Testování rovnosti referencí (identita)](./how-to-test-for-reference-equality-identity.md)|Popisuje, jak určit, zda dvě proměnné mají referenční rovnost.|  
|[Jak definovat rovnost hodnoty pro typ](./how-to-define-value-equality-for-a-type.md)|Popisuje způsob poskytnutí vlastní definice rovnosti hodnoty pro typ.|  
|[Průvodce programováním v C#](../index.md)|Obsahuje odkazy na podrobné informace o důležitých funkcích jazyka C# a funkcích, které jsou k dispozici pro C# prostřednictvím rozhraní .NET.|  
|[Typy](../types/index.md)|Obsahuje informace o typu systému C# a odkazy na Další informace.|  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
