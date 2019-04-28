---
title: Anonymní metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 94e9f7133c9a78ece7df5bd10cfc27c79d0652c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710001"
---
# <a name="anonymous-methods-c-programming-guide"></a>Anonymní metody (Průvodce programováním v C#)
Ve verzích jazyka C# před 2.0, je možné deklarovat jedině [delegovat](../../../csharp/language-reference/keywords/delegate.md) pomocí [s názvem metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). 2.0 C# zavedl anonymní metody a v C# 3.0 nebo novější, výrazy lambda jako upřednostňovaný způsob, jak napsat kód vloženého mají přednost před anonymní metody. Ale informace o anonymní metody v tomto tématu platí taky pro výrazy lambda. Existuje jeden případ, ve kterém anonymní metoda poskytuje funkce, nebyl nalezen v lambda výrazech. Anonymní metody umožňují vynechat seznam parametrů. To znamená, že na delegáty s různými podpisy lze převést anonymní metodu. To není možné s výrazy lambda. Další informace konkrétně o výrazech lambda naleznete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Vytvoření anonymní metody je v podstatě způsob, jak předat bloku kódu jako parametr delegátu. Tady jsou dva příklady:  
  
 [!code-csharp[csProgGuideDelegates#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#6)]  
  
 [!code-csharp[csProgGuideDelegates#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#5)]  
  
 S použitím anonymní metody, snížit režii kódování v vytvoření instance delegátů, protože není nutné vytvářet samostatné metodě.  
  
 Například zadání bloku kódu namísto delegát může být užitečné v situaci, pokud by bylo nutné vytvořit metodu zdát, že zbytečnou režii. Dobrým příkladem může být při spuštění nového vlákna. Tato třída vytvoří vlákno a také obsahuje kód, který se vlákna spustí bez vytváření další metoda pro delegáta.  
  
 [!code-csharp[csProgGuideDelegates#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#7)]  
  
## <a name="remarks"></a>Poznámky  
 Rozsah parametry anonymní metodu *anonymní metoda bloku*.  
  
 Jedná se o chybu, jako mít příkaz skoku [goto](../../../csharp/language-reference/keywords/goto.md), [přerušení](../../../csharp/language-reference/keywords/break.md), nebo [pokračovat](../../../csharp/language-reference/keywords/continue.md), uvnitř blok anonymní metody, pokud je cílem mimo blok. Je také chybou mít příkaz skoku, jako například `goto`, `break`, nebo `continue`, mimo blok anonymní metody, pokud je cíl uvnitř bloku.  
  
 Místní proměnné a parametry, jejichž rozsah obsahuje deklaraci anonymní metody jsou volány *vnější* proměnné anonymní metody. Například v následující segment kódu `n` je vnější proměnné:  
  
 [!code-csharp[csProgGuideDelegates#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#8)]  
  
 Odkaz na proměnnou vnějšího `n` je označen jako *zachycené* při vytvoření delegáta. Na rozdíl od místních proměnných dobu života zachycené proměnné rozšiřuje dokud delegáty, které odkazují na anonymní metody, které jsou způsobilé pro uvolňování paměti.  
  
 Nelze získat přístup k anonymní metodu [v](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry vnějším oboru.  
  
 Žádné nebezpečný kód může přistupovat v rámci *anonymní metoda bloku*.  
  
 Anonymní metody nejsou povoleny na levé straně [je](../../../csharp/language-reference/keywords/is.md) operátor.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva způsoby vytvoření instance delegáta:  
  
- Přidružíte delegáta s anonymní metodou.  
  
- Přidružení pojmenované metody delegáta (`DoWork`).  
  
 V obou případech se zobrazí zpráva, když je vyvolán delegát.  
  
 [!code-csharp[csProgGuideDelegates#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#4)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Delegáti s pojmenovanými vs. anonymními metodami](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
