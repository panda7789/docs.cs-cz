---
title: Delegáti - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 1c272dd9ab4f810a0eb1a1064b4c7731873d2c80
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675371"
---
# <a name="delegates-c-programming-guide"></a>Delegáti (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) je typ, který představuje odkazy na metody se seznamem konkrétních parametrů a návratovým typem. Pokud vytvoříte instanci delegátu, můžete příslušnou instanci přidružit s jakoukoli metodou s kompatibilním podpisem a návratovým typem. Metodu můžete vyvolat (nebo volat) prostřednictvím instance delegátu.  
  
 Delegáty se používají pro předávání metod jako argumentů jiným metodám. Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Můžete vytvořit vlastní metodu a konkrétní třída, jako je ovládací prvek Windows, může volat vaši metodu, pokud dojde k určité události. Následující příklad znázorňuje deklaraci delegátu.  
  
 [!code-csharp[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 Delegátu lze přiřadit jakoukoli metodu z jakékoli přístupné třídy nebo struktury odpovídající typu delegátu. Metoda může být buď statická, anebo se jedná o metodu instance. Díky tomu je možné programově změnit volání metody a vložit nový kód do stávajících tříd.  
  
> [!NOTE]
>  V kontextu přetížení metody nezahrnuje podpis metody návratovou hodnotu. V kontextu delegátů však podpis zahrnuje návratovou hodnotu. Jinými slovy to znamená, že metoda musí mít stejný návratový typ jako delegát.  
  
 Díky této možnosti odkazovat na metodu jako parametr jsou delegáty ideální pro definování metod zpětného volání. Například odkaz na metodu, která srovnává dva objekty, lze jako argument předat algoritmu řazení. Vzhledem k tomu, že srovnávací kód je součástí samostatné procedury, lze algoritmus řazení napsat obecnějším způsobem.  
  
## <a name="delegates-overview"></a>Přehled delegátů  
 Delegáty mají následující vlastnosti:  
  
-   Delegáti jsou podobné na ukazatele funkcí jazyka C++, ale delegáti jsou plně objektově orientované a na rozdíl od C++ ukazatelů na členské funkce, delegáti zapouzdřit instance objektu a metody.
  
-   Delegáty umožňují předávání metod jako parametrů.  
  
-   Delegáty lze použít pro definování metod zpětného volání.  
  
-   Delegáty lze zřetězit; například je možné volat větší počet metod v rámci jediné události.  
  
-   Metody nemusí přesně odpovídat typu delegátu. Další informace najdete v tématu [použití odchylky v delegátech](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
-   C# verze 2.0 byl zaveden koncept [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), které umožňují bloky kódu mají být předány jako parametrů, namísto samostatně definované metody. Verze 3.0 jazyka C# představila výrazy lambda jako přesnější způsob psaní bloků vloženého kódu. Anonymní metody i výrazy lambda (v určitých kontextech) se kompilují na typy delegátů. Tyto funkce se souhrnně označují jako anonymní funkce. Další informace o výrazech lambda naleznete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Použití delegátů](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [Použití delegátů namísto rozhraní (C# Programming Guide)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
-   [Delegáti s pojmenovanými vs. anonymními metodami](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [Použití odchylek v delegátech](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [Postupy: Kombinování delegátů (vícesměroví delegáti)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [Postupy: Deklarování, vytváření instancí a použití delegáta](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [delegáti](~/_csharplang/spec/delegates.md) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Delegáty, události a výrazy Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3.0 Cookbook, Third Edition: Víc než 250 řešení pro C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) v [učení C# 3.0: Hlavní základní informace o C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Delegate>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Události](../../../csharp/programming-guide/events/index.md)
