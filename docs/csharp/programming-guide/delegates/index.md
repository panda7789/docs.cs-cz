---
title: Delegáti – Průvodce programováním v C#
description: Delegát v jazyce C# je typ, který odkazuje na metody se seznamem parametrů a návratovým typem. Delegáty se používají pro předávání metod jako argumentů jiným metodám.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 2c1be56b67528c17a6cf1d8d8517817ff93b2aa5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063635"
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
  
- Delegáti jsou podobný ukazatelům funkcí jazyka C++, ale Delegáti jsou plně objektově orientované a na rozdíl od ukazatelů jazyka C++ na členské funkce, delegáty zapouzdřují instanci objektu i metodu.
  
- Delegáty umožňují předávání metod jako parametrů.  
  
- Delegáty lze použít pro definování metod zpětného volání.  
  
- Delegáty lze zřetězit; například je možné volat větší počet metod v rámci jediné události.  
  
- Metody nemusí přesně odpovídat typu delegátu. Další informace naleznete v tématu [použití variance v delegátech](../concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
- C# verze 2,0 představil koncept [anonymních metod](../../language-reference/operators/delegate-operator.md), které umožňují předávat bloky kódu jako parametry namísto samostatně definované metody. Verze 3.0 jazyka C# představila výrazy lambda jako přesnější způsob psaní bloků vloženého kódu. Anonymní metody i výrazy lambda (v určitých kontextech) se kompilují na typy delegátů. Tyto funkce se souhrnně označují jako anonymní funkce. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../language-reference/operators/lambda-expressions.md).
  
## <a name="in-this-section"></a>V tomto oddílu  
  
- [Použití delegátů](./using-delegates.md)  
  
- [Kdy použít delegáty namísto rozhraní (Průvodce programováním v C#)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))  
  
- [Delegáti s pojmenovanými vs. Anonymní metody](./delegates-with-named-vs-anonymous-methods.md)  
  
- [Použití odchylek v delegátech](../concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
- [Postup kombinování delegátů (Delegáti vícesměrového vysílání)](./how-to-combine-delegates-multicast-delegates.md)  
  
- [Jak deklarovat, vytvořit instanci a používat delegáta](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [Delegáti](~/_csharplang/spec/delegates.md) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [C# 3,0 kuchařka, třetí edice: více než 250 řešení pro c# 3,0 programátory](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) v [kurzu C# 3,0: hlavní základy jazyka c# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Delegate>
- [Průvodce programováním v C#](../index.md)
- [Události](../events/index.md)
