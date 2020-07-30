---
title: Použití delegátů – Průvodce programováním v C#
description: Naučte se používat delegáty. Delegáti jsou objektově orientovaný, typově bezpečný a zabezpečený typ, který bezpečně zapouzdřuje metodu.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: a9b625b8c0785ed2f446be27c11dc76108bc4bce
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302149"
---
# <a name="using-delegates-c-programming-guide"></a>Použití delegátů (Průvodce programováním v C#)

[Delegát](../../language-reference/builtin-types/reference-types.md) je typ, který bezpečně zapouzdřuje metodu, podobně jako ukazatel na funkci v jazyce C a C++. Na rozdíl od ukazatelů funkcí jazyka C jsou delegáti objektově orientovaný, typově bezpečný a zabezpečený. Typ delegáta je definován názvem delegáta. Následující příklad deklaruje delegáta s názvem `Del` , který může zapouzdřit metodu, která přijímá [řetězec](../../language-reference/builtin-types/reference-types.md) jako argument a vrací [typ void](../../language-reference/builtin-types/void.md):

[!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]

Objekt delegáta je obvykle vytvořen tak, že poskytuje název metody, které bude delegát zalamovat, nebo s [anonymní funkcí](../statements-expressions-operators/anonymous-functions.md). Po vytvoření instance delegáta bude do této metody předána volání metody provedené delegátem. Parametry předané delegátovi jsou předány metodě a návratová hodnota, pokud existuje, z metody se vrátí volajícímu delegátovi. Označuje se jako volání delegáta. Instanci delegáta lze vyvolat, jako by se jednalo o zabalenou metodu. Příklad:

[!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  

[!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]

Typy delegátů jsou odvozeny z <xref:System.Delegate> třídy v rozhraní .NET. Typy delegátů jsou [zapečetěné](../../language-reference/keywords/sealed.md)– nemůžou být odvozené od – a není možné odvodit vlastní třídy z <xref:System.Delegate> . Vzhledem k tomu, že konstruktor s vytvořeným instancemi je objekt, může být předán jako parametr nebo přiřazen vlastnosti. To umožňuje, aby metoda přijímala delegáta jako parametr a později volala delegáta. Tento postup se označuje jako asynchronní zpětné volání a je běžnou metodou upozorňování volajícího na dokončení dlouhého procesu. V případě použití delegáta tímto způsobem kód používající delegáta nepotřebuje žádné znalosti implementace používané metody. Funkčnost je podobná rozhraním zapouzdření.

Dalším běžným použitím zpětných volání je definování vlastní metody porovnání a předání tohoto delegáta metodě řazení. Umožňuje, aby se kód volajícího stal součástí algoritmu řazení. Následující příklad metody používá `Del` typ jako parametr:

[!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]

Potom můžete předat delegáta, který jste vytvořili výše, do této metody:

[!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]

a dostanete následující výstup do konzoly:

```console
The number is: 3
```

Použití delegáta jako abstrakce `MethodWithCallback` není nutné volat konzolu přímo – nemusí být navržena s ohledem na konzolu. Co `MethodWithCallback` je jednoduše Příprava řetězce a předání řetězce do jiné metody. To je obzvláště výkonné, protože delegovaná metoda může používat libovolný počet parametrů.

Když je delegát vytvořen k zabalení metody instance, delegát odkazuje jak na instanci, tak na metodu. Delegát nemá žádné znalosti o typu instance z metody, kterou zabalí, takže delegát může odkazovat na libovolný typ objektu, pokud existuje metoda, která odpovídá signatuře delegáta. Když je delegát vytvořen pro zabalení statické metody, odkazuje pouze na metodu. Vezměte v úvahu následující deklarace:

[!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]

Společně se statickým `DelegateMethod` uvedeným dříve máme tři metody, které mohou být zabaleny `Del` instancí.

Delegát může při vyvolání volat více než jednu metodu. Tato funkce se označuje jako vícesměrové vysílání. Chcete-li přidat další metodu do seznamu metod delegáta – seznam vyvolání – vyžaduje přidání dvou delegátů pomocí operátorů sčítání nebo sčítání (' + ' nebo ' + = '). Příklad:

[!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]

V tomto okamžiku `allMethodsDelegate` obsahuje tři metody v seznamu jeho vyvolání – `Method1` , `Method2` a `DelegateMethod` . Původní tři delegáti, `d1` , `d2` a `d3` , zůstávají beze změny. Když `allMethodsDelegate` je vyvolána, všechny tři metody jsou volány v pořadí. Pokud delegát používá referenční parametry, je odkaz předán postupně každé tři metody a všechny změny v jedné metodě jsou viditelné pro další metodu. Když kterákoli z metod vyvolá výjimku, která není zachycena v rámci metody, je tato výjimka předána volajícímu delegáta a žádné následné metody v seznamu volání nejsou volány. Pokud má delegát návratovou hodnotu nebo výstupní parametry, vrátí návratovou hodnotu a parametry poslední vyvolané metody. Chcete-li odebrat metodu ze seznamu vyvolání, použijte [operátory přiřazení odčítání nebo odčítání](../../language-reference/operators/subtraction-operator.md) ( `-` nebo `-=` ). Příklad:

[!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]

Vzhledem k tomu, že typy delegátů jsou odvozeny z `System.Delegate` , metody a vlastnosti definované touto třídou mohou být volány na delegáta. Pokud například chcete najít počet metod v seznamu volání delegáta, můžete napsat:

[!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]

Delegáti s více než jednou metodou v seznamu volání jsou odvozeni z <xref:System.MulticastDelegate> , což je podtřídou třídy `System.Delegate` . Výše uvedený kód funguje v obou případech, protože obě třídy podporují `GetInvocationList` .

Delegáti vícesměrového vysílání se často používají při zpracování událostí. Zdrojové objekty událostí odesílají oznámení o událostech do objektů příjemců, které jsou zaregistrované pro příjem této události. K registraci pro událost příjemce vytvoří metodu, která je navržena pro zpracování události, a pak vytvoří delegáta pro tuto metodu a předá delegáta zdroji události. Zdroj volá delegáta, když dojde k události. Delegát pak zavolá metodu zpracování události na příjemce a doručí data události. Typ delegáta pro danou událost je definován zdrojem události. Další informace najdete v tématu [události](../events/index.md).

Porovnání delegátů dvou různých typů přiřazených v době kompilace způsobí chybu kompilace. Pokud jsou instance delegátů staticky typu `System.Delegate` , je porovnávání povoleno, ale v době běhu vrátí hodnotu false. Příklad:

[!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Delegáti](./index.md)
- [Použití odchylek v delegátech](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Odchylky v delegátech](../concepts/covariance-contravariance/variance-in-delegates.md)
- [Použití odchylek pro obecné delegáty Func a Action](../concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Události](../events/index.md)
