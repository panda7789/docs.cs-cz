---
title: Delegáti C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: c0f28716926d4c9d74cde58fd00e27d1fdfa7ce1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705363"
---
# <a name="delegates-c-programming-guide"></a>Delegáti (Průvodce programováním v C#)
[Delegát](../../language-reference/builtin-types/reference-types.md) je typ, který představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem. Pokud vytvoříte instanci delegátu, můžete příslušnou instanci přidružit s jakoukoli metodou s kompatibilním podpisem a návratovým typem. Metodu můžete vyvolat (nebo volat) prostřednictvím instance delegátu.  
  
 Delegáty se používají pro předávání metod jako argumentů jiným metodám. Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Můžete vytvořit vlastní metodu a konkrétní třída, jako je ovládací prvek Windows, může volat vaši metodu, pokud dojde k určité události. Následující příklad znázorňuje deklaraci delegátu.  
  
 [!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]  
  
 Delegátu lze přiřadit jakoukoli metodu z jakékoli přístupné třídy nebo struktury odpovídající typu delegátu. Metoda může být buď statická, anebo se jedná o metodu instance. Díky tomu je možné programově změnit volání metody a vložit nový kód do stávajících tříd.  
  
> [!NOTE]
> V kontextu přetížení metody nezahrnuje podpis metody návratovou hodnotu. V kontextu delegátů však podpis zahrnuje návratovou hodnotu. Jinými slovy to znamená, že metoda musí mít stejný návratový typ jako delegát.  
  
 Díky této možnosti odkazovat na metodu jako parametr jsou delegáty ideální pro definování metod zpětného volání. Například odkaz na metodu, která srovnává dva objekty, lze jako argument předat algoritmu řazení. Vzhledem k tomu, že srovnávací kód je součástí samostatné procedury, lze algoritmus řazení napsat obecnějším způsobem.  
  
## <a name="delegates-overview"></a>Přehled delegátů  
 Delegáty mají následující vlastnosti:  
  
- Delegáti jsou podobní ukazatelům C++ funkce, ale Delegáti jsou plně objektově orientované a na C++ rozdíl od ukazatelů na členské funkce, delegáty zapouzdřují instanci objektu i metodu.
  
- Delegáty umožňují předávání metod jako parametrů.  
  
- Delegáty lze použít pro definování metod zpětného volání.  
  
- Delegáty lze zřetězit; například je možné volat větší počet metod v rámci jediné události.  
  
- Metody nemusí přesně odpovídat typu delegátu. Další informace naleznete v tématu [použití variance v delegátech](../concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
- C#verze 2,0 představila koncept [anonymních metod](../../language-reference/operators/delegate-operator.md), které umožňují, aby byly bloky kódu předány jako parametry namísto samostatně definované metody. Verze 3.0 jazyka C# představila výrazy lambda jako přesnější způsob psaní bloků vloženého kódu. Anonymní metody i výrazy lambda (v určitých kontextech) se kompilují na typy delegátů. Tyto funkce se souhrnně označují jako anonymní funkce. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../statements-expressions-operators/lambda-expressions.md).
  
## <a name="in-this-section"></a>V tomto oddílu  
  
- [Použití delegátů](./using-delegates.md)  
  
- [Kdy použít delegáty namísto rozhraní (C# Průvodce programováním)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Delegáti s pojmenovanými vs. anonymními metodami](./delegates-with-named-vs-anonymous-methods.md)  
  
- [Použití odchylek v delegátech](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Postup kombinování delegátů (Delegáti vícesměrového vysílání)](./how-to-combine-delegates-multicast-delegates.md)  
  
- [Postup deklarace, vytvoření instance a použití delegáta](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a>C# – jazyková specifikace  

Další informace naleznete v tématu [Delegáti](~/_csharplang/spec/delegates.md) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3,0 kuchařka, třetí vydání: více než 250 řešení pro C# 3,0 programátorů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) ve [studiu C# 3,0: hlavní základy pro C# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Delegate>
- [Průvodce programováním v jazyce C#](../index.md)
- [Události](../events/index.md)
