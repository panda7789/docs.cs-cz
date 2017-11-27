---
title: "Anonymní metody (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d942e0f3245f6404c896173b2c7ca6f1090a8c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 Anonymní metody nemůže získat přístup k [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out.md) parametry vnějším oboru.  
  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Lambda – výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Delegáti s pojmenované vs. Anonymní metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
