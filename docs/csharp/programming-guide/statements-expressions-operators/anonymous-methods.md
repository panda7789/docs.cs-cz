---
title: Anonymní metody (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 7f6c596dcc73cdfb335071f57aab18e836ceaae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338419"
---
# <a name="anonymous-methods-c-programming-guide"></a>Anonymní metody (Průvodce programováním v C#)
Ve verzi jazyka C# před 2.0, lze deklarovat pouze [delegovat](../../../csharp/language-reference/keywords/delegate.md) pomocí [s názvem metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). C# 2.0 zavedená anonymní metody a v C# 3.0 nebo novější, výrazů lambda jako upřednostňovaný způsob, jak napsat kód vložený mají přednost před anonymní metody. Ale informace o anonymní metody v tomto tématu platí taky pro výrazy lambda. Neexistuje jeden případ, ve kterém anonymní metoda poskytuje funkce nebyla nalezena v výrazy lambda. Anonymní metody umožňují vynechejte parametr seznamu. To znamená, že anonymní metody lze převést na delegáty s různými podpisy. To není možné pomocí výrazů lambda. Další informace o výrazy lambda konkrétně najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Vytvoření anonymní metody je v podstatě způsob, jak předat blok kódu jako parametr delegáta. Zde jsou dva příklady:  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 Pomocí anonymní metody se snižuje režie kódování v vytváření instancí delegáti, protože není nutné vytvořit samostatné metodě.  
  
 Například uvádějící že blok kódu místo delegáta může být užitečná v situaci, když nutnosti vytvoření metody zdát nepotřebné režijní náklady. Dobrým příkladem může být, kdy spustit nové vlákno. Tato třída se vytvoří vlákno a také obsahuje kód, který provede vlákno bez vytvoření další metodu pro delegáta.  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a>Poznámky  
 Rozsah parametry anonymní metody je *anonymní blok metody*.  
  
 Jedná se o chybu tak, aby měl výpis přechod, jako například [goto](../../../csharp/language-reference/keywords/goto.md), [zalomení](../../../csharp/language-reference/keywords/break.md), nebo [pokračovat](../../../csharp/language-reference/keywords/continue.md), uvnitř bloku anonymní metody, pokud je cílem mimo blok. Je také chybu tak, aby měl výpis přechod, jako například `goto`, `break`, nebo `continue`, mimo blok anonymní metody, pokud je cílem uvnitř bloku.  
  
 Místní proměnné a parametry, jehož obor obsahuje deklaraci anonymní metoda se nazývají *vnější* proměnné anonymní metody. Například v následujícím kódu segmentu `n` je proměnná vnější:  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 Odkaz na proměnnou vnější `n` se říká, že *zachytit* vytvoření delegát. Na rozdíl od místní proměnné doba platnosti zaznamenané proměnné rozšiřuje dokud delegáti, které odkazují na anonymní metody jsou způsobilé pro uvolňování paměti.  
  
 Anonymní metody nemůže získat přístup k [v](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry vnějším oboru.  
  
 Žádné nezabezpečený kód je přístupná v rámci *anonymní blok metody*.  
  
 Anonymní metody nejsou povoleny na levé straně [je](../../../csharp/language-reference/keywords/is.md) operátor.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva způsoby vytvoření instance delegáta:  
  
-   Delegát přidružením anonymní metody.  
  
-   Delegát přidružením metodu s názvem (`DoWork`).  
  
 V každém případě se zobrazí zpráva při vyvolání delegáta.  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Delegáti s pojmenovanými vs. anonymními metodami](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
