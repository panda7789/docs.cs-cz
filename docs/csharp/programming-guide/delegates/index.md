---
title: "Delegáti (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a6649537238af38e073eeb8747487822d058b7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delegates-c-programming-guide"></a>Delegáti (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) je typ, který reprezentuje odkazy na metody se seznamem konkrétní parametr a návratový typ. Pokud vytvoříte instanci delegátu, můžete příslušnou instanci přidružit s jakoukoli metodou s kompatibilním podpisem a návratovým typem. Metodu můžete vyvolat (nebo volat) prostřednictvím instance delegátu.  
  
 Delegáty se používají pro předávání metod jako argumentů jiným metodám. Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Můžete vytvořit vlastní metodu a konkrétní třída, jako je ovládací prvek Windows, může volat vaši metodu, pokud dojde k určité události. Následující příklad znázorňuje deklaraci delegátu.  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 Delegátu lze přiřadit jakoukoli metodu z jakékoli přístupné třídy nebo struktury odpovídající typu delegátu. Metoda může být buď statická, anebo se jedná o metodu instance. Díky tomu je možné programově změnit volání metody a vložit nový kód do stávajících tříd.  
  
> [!NOTE]
>  V kontextu přetížení metody nezahrnuje podpis metody návratovou hodnotu. V kontextu delegátů však podpis zahrnuje návratovou hodnotu. Jinými slovy to znamená, že metoda musí mít stejný návratový typ jako delegát.  
  
 Díky této možnosti odkazovat na metodu jako parametr jsou delegáty ideální pro definování metod zpětného volání. Například odkaz na metodu, která srovnává dva objekty, lze jako argument předat algoritmu řazení. Vzhledem k tomu, že srovnávací kód je součástí samostatné procedury, lze algoritmus řazení napsat obecnějším způsobem.  
  
## <a name="delegates-overview"></a>Přehled delegátů  
 Delegáty mají následující vlastnosti:  
  
-   Delegáty odpovídají ukazatelům funkcí jazyka C++, jsou však typově bezpečné.  
  
-   Delegáty umožňují předávání metod jako parametrů.  
  
-   Delegáty lze použít pro definování metod zpětného volání.  
  
-   Delegáty lze zřetězit; například je možné volat větší počet metod v rámci jediné události.  
  
-   Metody nemusí přesně odpovídat typu delegátu. Další informace najdete v tématu [použití odchylky v delegátech](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
-   C# verze 2.0 zaveden koncept [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), které umožňují bloky kódu, které mají být předány jako parametry místo samostatně definovaný metoda. Verze 3.0 jazyka C# představila výrazy lambda jako přesnější způsob psaní bloků vloženého kódu. Anonymní metody i výrazy lambda (v určitých kontextech) se kompilují na typy delegátů. Tyto funkce se souhrnně označují jako anonymní funkce. Další informace o výrazy lambda najdete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Použití delegátů](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [Kdy použít delegáti místo rozhraní (C# Průvodce programováním)](http://msdn.microsoft.com/en-us/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [Delegáti s pojmenované vs. Anonymní metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [Použití odchylek v delegátech](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [Postupy: kombinování delegátů (vícesměroví delegáti)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [Postupy: deklarování, vytváření instancí a použití delegáta](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Výrazy Lambda, delegáti a události](http://go.microsoft.com/fwlink/?LinkId=195395) v [C# 3.0 Cookbook, Third Edition: víc než 250 řešení pro programátory v jazyce C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
 [Delegáti a události](http://go.microsoft.com/fwlink/?LinkId=195418) v [Learning C# 3.0: Master Základy C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Delegate>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)
