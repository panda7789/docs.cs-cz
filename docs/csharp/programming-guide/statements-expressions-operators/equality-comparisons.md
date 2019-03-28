---
title: Porovnání rovnosti - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: 7cbd1a2c1a9968ae8ed4f96d503d472bbe9b32c4
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545452"
---
# <a name="equality-comparisons-c-programming-guide"></a>Porovnání rovnosti (C# Programming Guide)

Někdy je nutné srovnat dvě hodnoty na rovnost. V některých případech testujete *hodnota rovnosti*, označované také jako *ekvivalence*, což znamená, že hodnoty, které jsou obsaženy ve dvou proměnných jsou stejné. V ostatních případech je nutné určit, zda hodnoty dvou proměnných odkazují na stejný základní objekt v paměti. Tento typ rovnosti se nazývá *referenční rovnost*, nebo *identity*. Toto téma popisuje tyto dva druhy rovnosti a obsahuje odkazy na další témata pro další informace.  
  
## <a name="reference-equality"></a>Referenční rovnost

 Referenční rovnost znamená, že reference na dva objekty odkazují na stejný základní objekt. Tato situace může nastat prostřednictvím jednoduchého přiřazení, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 V tomto kódu jsou vytvořeny dva objekty, ale po příkazu přiřazení oba odkazy odkazují na stejný objekt. Proto mají referenční rovnost. Použití <xref:System.Object.ReferenceEquals%2A> metodou ke zjištění, zda dva odkazy odkazují na stejný objekt.  
  
 Pojem referenční rovnosti platí pouze pro typy odkazů. Hodnota typu objektů nemůže mít referenční rovnosti, protože při instanci hodnotového typu přiřazena proměnné, je vytvořena kopie hodnoty. Proto nikdy nemůžete mít dvě nezabalené struktury, které odkazují na stejné místo v paměti. Navíc pokud použijete <xref:System.Object.ReferenceEquals%2A> k porovnání dvou typů hodnot, výsledek bude vždy `false`i v případě, že jsou všechny stejné hodnoty, které jsou obsaženy v objektech. Je to proto, že každá proměnná je zabalená do samostatného objekt instance. Další informace najdete v tématu [jak: Test rovnosti (Identity) odkazů](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).  

## <a name="value-equality"></a>Hodnota rovnosti

 Hodnota rovnost znamená, že dva objekty obsahují stejnou hodnotu nebo hodnoty. Pro primitivní hodnotové typy, jako [int](../../../csharp/language-reference/keywords/int.md) nebo [bool](../../../csharp/language-reference/keywords/bool.md), jsou testy pro hodnotu rovnosti jednoduché. Můžete použít [ == ](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) operátoru, jak je znázorněno v následujícím příkladu.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Testování rovnosti hodnoty je složitější pro většinu ostatních typů, protože vyžaduje pochopit, jak ji definuje typ. Tříd a struktur, které mají více polí nebo vlastností je rovnost hodnoty často definována tak, že všechny vlastnosti nebo pole mají stejnou hodnotu. Například dva `Point` objekty mohou být definovány jako ekvivalentní, pokud se pointA.X rovná pointB.X a pointA.Y se rovná pointB.Y.  
  
 Neexistuje však žádný požadavek, aby rovnocennost byla založena na všechna pole v typu. Může být založen na podmnožinu. Při porovnávání typů, které nevlastníte, měli pochopit, konkrétně jak ekvivalence definované pro daný typ. Další informace o tom, jak definovat rovnost hodnot ve vašich třídách a strukturách naleznete v tématu [jak: Definování rovnosti hodnoty pro typ](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).  
  
### <a name="value-equality-for-floating-point-values"></a>Hodnota rovnosti pro hodnoty s plovoucí desetinnou čárkou

 Porovnání rovnosti hodnot s plovoucí desetinnou čárkou ([double](../../../csharp/language-reference/keywords/double.md) a [float](../../../csharp/language-reference/keywords/float.md)) je problematické z důvodu nepřesnosti z s plovoucí desetinnou čárkou aritmetické operace v binárních počítačích. Další informace naleznete v poznámkách v tématu <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Testování rovnosti (Identity) odkazů](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|Popisuje, jak zjistit, zda mají dvě proměnné referenční rovnost.|  
|[Postupy: Definování rovnosti hodnoty pro typ](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|Popisuje, jak poskytnout vlastní definici rovnosti hodnot daného typu.|  
|[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)|Obsahuje odkazy na podrobné informace o důležitých funkcích jazyka C# a funkce, které jsou k dispozici pro C# pomocí rozhraní .NET Framework.|  
|[Typy](../../../csharp/programming-guide/types/index.md)|Poskytuje informace o typu systému C# a odkazy na další informace.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
