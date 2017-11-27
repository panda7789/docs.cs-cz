---
title: "Porovnání rovnosti (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 199257b1fe371dea3e4ee1eedcf11f3bdce02366
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="equality-comparisons-c-programming-guide"></a>Porovnání rovnosti (Průvodce programováním v C#)
Někdy je nezbytné k porovnání rovnosti dvou hodnot. V některých případech testujete pro *hodnotu rovnosti*, také známé jako *ekvivalenční*, což znamená, že hodnoty, které jsou obsaženy v dvě proměnné, které jsou stejné. V ostatních případech budete muset určit, zda dvě proměnné odkazovat na stejnou základní objekt v paměti. Tento typ rovnosti se nazývá *referenční rovnosti*, nebo *identity*. Toto téma popisuje tyto dva druhy rovnosti a poskytuje odkazy na další témata pro další informace.  
  
## <a name="reference-equality"></a>Referenční rovnost  
 Referenční rovnost znamená, že dva odkazy na objekty odkazovat na stejnou základní objekt. Tato situace může nastat prostřednictvím jednoduchého přiřazení, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]  
  
 V tomto kódu jsou vytvořeny dva objekty, ale po příkazu přiřazení i odkazy odkazují na stejný objekt. Proto mají referenční rovnosti. Použití <xref:System.Object.ReferenceEquals%2A> metoda k určení, zda dva odkazy odkazují na stejný objekt.  
  
 Referenční rovnost koncept se vztahuje pouze na odkazové typy. Hodnota objekty typu nemůže mít referenční rovnost, protože při instanci typ hodnoty je přiřazený k proměnné, se provádí kopie hodnoty. Proto může mít nikdy dvě nezabalený struktury, které odkazují na stejné umístění v paměti. Kromě toho pokud používáte <xref:System.Object.ReferenceEquals%2A> k porovnání dvou typů hodnot, výsledkem bude vždy `false`i v případě, že jsou všechny identické hodnoty, které jsou obsažené v objektech. Je to proto, že je zabalená každou proměnnou, do instance samostatný objekt. Další informace najdete v tématu [postupy: Test rovnosti (Identity) odkazů](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).  
  
## <a name="value-equality"></a>Hodnota rovnosti  
 Rovnosti hodnoty znamená, že obsahují dva objekty stejnou hodnotu nebo hodnoty. Pro hodnotu primitivní typy, jako [int](../../../csharp/language-reference/keywords/int.md) nebo [bool](../../../csharp/language-reference/keywords/bool.md), testování rovnosti hodnoty jsou jednoduché. Můžete použít [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) operátor, jak je znázorněno v následujícím příkladu.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Testování rovnosti hodnoty je složitější pro většinu jiné typy, protože vyžaduje pochopit, jak ji definuje typ. Pro třídy a struktury, které mají více polí a vlastností je často rovnosti hodnoty definována znamená, že všechny vlastnosti nebo pole mají stejnou hodnotu. Například dvě `Point` objekty mohou být definovány jako ekvivalentní Pokud pointA.X rovná pointB.X a pointA.Y rovná pointB.Y.  
  
 Neexistuje však žádný požadavek, aby ekvivalenční byla založena na všechna pole v typu. Může být založen na podmnožinu. Při porovnávání typy, které nevlastníte, měli byste si ověřit, abyste pochopili, jak je konkrétně ekvivalenční definované pro tento typ. Další informace o tom, jak definování rovnosti hodnoty v vlastní třídy a struktury najdete v tématu [postupy: definování rovnosti hodnoty pro typ](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).  
  
### <a name="value-equality-for-floating-point-values"></a>Rovnosti hodnoty pro číslo s plovoucí čárkou hodnoty bodu  
 Porovnání rovnosti hodnot s plovoucí čárkou bodu hodnoty ([dvojité](../../../csharp/language-reference/keywords/double.md) a [float](../../../csharp/language-reference/keywords/float.md)) problematické jsou z důvodu nepřesnosti z plovoucí aritmetické bodu na binární počítačích. Další informace najdete v části poznámky v tématu <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Test rovnosti (Identity) odkazů](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|Popisuje, jak zjistit, zda dvě proměnné referenční rovnosti.|  
|[Postupy: definování rovnosti hodnoty pro typ](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|Popisuje, jak poskytnout vlastní definice rovnosti hodnoty pro typ.|  
|[Průvodce programováním v C#](../../../csharp/programming-guide/index.md)|Obsahuje odkazy na podrobné informace o důležitých funkcí jazyka C# a funkce, které jsou k dispozici pro C# prostřednictvím rozhraní .NET Framework.|  
|[Typy](../../../csharp/programming-guide/types/index.md)|Poskytuje informace o systém typů jazyka C# a odkazy na další informace.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)
