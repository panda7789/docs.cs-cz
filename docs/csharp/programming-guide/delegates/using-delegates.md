---
title: Použití delegátů – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: dcc73aba738d6296a44c48aad8b66cd6fc7f4a7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77448436"
---
# <a name="using-delegates-c-programming-guide"></a>Použití delegátů (Průvodce programováním v C#)

[Delegát](../../language-reference/builtin-types/reference-types.md) je typ, který bezpečně zapouzdřuje metodu, podobně jako ukazatel funkce v jazyce C a C++. Na rozdíl od ukazatele funkce Jazyka C jsou delegáti objektově orientovaní, typově bezpečné a zabezpečené. Typ delegáta je definován jménem delegáta. Následující příklad deklaruje delegáta s názvem, `Del` který může zapouzdřit metodu, která bere [řetězec](../../language-reference/builtin-types/reference-types.md) jako argument a vrátí [void](../../language-reference/builtin-types/void.md):

[!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]

Objekt delegáta je obvykle vytvořen zadáním názvu metody, kterou delegát zalomí, nebo [s anonymní funkcí](../statements-expressions-operators/anonymous-functions.md). Jakmile delegát je vytvořena instance, volání metody delegáta bude předándelegát emitované této metody. Parametry předané delegátovi volajícím jsou předány metodě a vrácená hodnota, pokud existuje, z metody je vrácena volajícímu delegátem. To se označuje jako vyvolání delegáta. Instance delegáta může být vyvolána, jako kdyby se jednalo o zabalené metody samotné. Například:

[!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  

[!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]

Typy delegátů jsou odvozeny z třídy <xref:System.Delegate> v rozhraní .NET Framework. Typy delegátů jsou [zapečetěné](../../language-reference/keywords/sealed.md)– nelze je odvodit – <xref:System.Delegate>a není možné odvodit vlastní třídy z . Vzhledem k tomu, že instanciovaný delegát je objekt, může být předán jako parametr nebo přiřazen k vlastnosti. To umožňuje metodu přijmout delegáta jako parametr a volat delegáta později. To se označuje jako asynchronní zpětné volání a je běžnou metodou upozornění volajícího po dokončení dlouhého procesu. Při použití delegáta tímto způsobem kód pomocí delegáta nepotřebuje žádné znalosti o implementaci metody, která se používá. Funkce je podobná zapouzdření rozhraní poskytují.

Dalším běžným použitím zpětných volání je definování vlastní metody porovnání a předání tohoto delegáta metodě řazení. Umožňuje kódu volajícího, aby se stal součástí algoritmu řazení. Následující příklad metody `Del` používá typ jako parametr:

[!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]

Potom můžete předat delegáta vytvořenévýše této metodě:

[!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]

a obdržíte následující výstup do konzoly:

```console
The number is: 3
```

Použití delegáta jako `MethodWithCallback` abstrakce, není nutné volat konzoly přímo – nemusí být navržen s konzolou v mysli. Co `MethodWithCallback` dělá, je jednoduše připravit řetězec a předat řetězec do jiné metody. To je obzvláště výkonné, protože delegovaná metoda může použít libovolný počet parametrů.

Když delegát je vytvořen k obtékání metody instance, delegát odkazuje na instanci i metodu. Delegát nemá žádné znalosti typu instance kromě metody, kterou zabalí, takže delegát může odkazovat na libovolný typ objektu, pokud je metoda na tento objekt, který odpovídá podpisdelegáta. Když delegát je konstruována tak, aby zalamovala statickou metodu, odkazuje pouze na metodu. Vezměte v úvahu následující deklarace:

[!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]

Spolu s `DelegateMethod` dříve zobrazené statické, nyní máme tři metody, které mohou být zabaleny `Del` instance.

Delegát může volat více než jednu metodu při vyvolání. To se označuje jako vícesměrové vysílání. Chcete-li přidat další metodu do seznamu delegáta metody – seznam vyvolání – jednoduše vyžaduje přidání dvou delegátů pomocí operátory sčítání nebo sčítání přiřazení ('+' nebo '+='). Například:

[!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]

V tomto `allMethodsDelegate` okamžiku obsahuje tři metody`Method1`v `Method2`jeho `DelegateMethod`seznamu vyvolání– , , a . Původní tři delegáti `d2`, `d3` `d1`, a , zůstávají beze změny. Při `allMethodsDelegate` vyvolání jsou všechny tři metody volány v pořadí. Pokud delegát používá referenční parametry, odkaz je předán postupně na každou ze tří metod v pořadí a všechny změny jednou metodou jsou viditelné pro další metodu. Pokud některá z metod vyvolá výjimku, která není zachycena v rámci metody, tato výjimka je předána volajícímu delegáta a nejsou volány žádné následné metody v seznamu vyvolání. Pokud delegát má návratovou hodnotu nebo out parametry, vrátí vrácenou hodnotu a parametry poslední volanou metodu. Chcete-li odebrat metodu ze seznamu vyvolání, použijte`-` [operátory přiřazení odčítání nebo odčítání](../../language-reference/operators/subtraction-operator.md) ( nebo `-=`). Například:

[!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]

Vzhledem k tomu, `System.Delegate`že typy delegátů jsou odvozeny z , metody a vlastnosti definované této třídy lze volat na delegáta. Chcete-li například najít počet metod v seznamu vyvolání delegáta, můžete napsat:

[!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]

Delegáti s více než jednou metodou <xref:System.MulticastDelegate>v seznamu vyvolání `System.Delegate`jsou odvozeni z , což je podtřída . Výše uvedený kód funguje v obou `GetInvocationList`případech, protože obě třídy podporují .

Vícesměrové vysílání delegátů se používají ve velké míře v zpracování událostí. Objekty zdroje událostí odesílají oznámení o událostech příjemcům objektům, které se zaregistrovaly k přijetí této události. Chcete-li se zaregistrovat pro událost, příjemce vytvoří metodu určenou ke zpracování události, pak vytvoří delegáta pro tuto metodu a předá delegáta zdroji události. Zdroj volá delegáta, když dojde k události. Delegát pak volá metodu zpracování událostí na příjemce, doručení dat události. Typ delegáta pro danou událost je definován zdrojem události. Další informace naleznete v [tématu Události](../events/index.md).

Porovnání delegátů dvou různých typů přiřazených v době kompilace bude mít za následek chybu kompilace. Pokud instance delegáta jsou staticky `System.Delegate`typu , pak porovnání je povoleno, ale vrátí false za běhu. Například:

[!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Delegáty](./index.md)
- [Použití odchylek v delegátech](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Odchylky v delegátech](../concepts/covariance-contravariance/variance-in-delegates.md)
- [Použití odchylek pro obecné delegáty Func a Action](../concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Akce](../events/index.md)
