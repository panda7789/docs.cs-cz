---
title: Delegáti (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 516f5193509d3c87cc8fb7a36e2d69e04a85a6b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
-   [Kdy použít delegáti místo rozhraní (C# Průvodce programováním)](http://msdn.microsoft.com/library/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [Delegáti s pojmenovanými vs. anonymními metodami](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [Použití odchylek v delegátech](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [Postupy: kombinování delegátů (vícesměroví delegáti)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [Postupy: Deklarování, vytváření instancí a použití delegáta](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Výrazy Lambda, delegáti a události](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) v [C# 3.0 Cookbook, Third Edition: víc než 250 řešení pro programátory v jazyce C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Delegáti a události](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) v [Learning C# 3.0: Master Základy C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Delegate>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)
