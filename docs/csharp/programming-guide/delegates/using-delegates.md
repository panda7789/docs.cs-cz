---
title: "Použití delegátů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cef62448388299f310fa26ecb632485b6538c032
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-delegates-c-programming-guide"></a>Použití delegátů (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) je typu, který zapouzdřuje bezpečně metodu, podobně jako ukazatel na funkci jazyka C a C++. Na rozdíl od ukazatelů na funkce C Delegáti jsou objektově orientované, zadejte bezpečné a zabezpečení. Název delegát je definován typ delegáta. Následující příklad deklaruje delegáta s názvem `Del` který může zapouzdřit metody, která přijímá [řetězec](../../../csharp/language-reference/keywords/string.md) jako argument a vrátí [void](../../../csharp/language-reference/keywords/void.md):  
  
 [!code-csharp[csProgGuideDelegates#21](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_1.cs)]  
  
 Objekt delegáta normálně vytvořená pomocí Pokud budou zahrnovat název metody delegáta, nebo se [anonymní metoda](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md). Po vytvoření instance delegáta volání metody delegáta provedené se předá delegátem dané metody. Parametry delegátovi předaná volající funkcí je předaný metodě a návratovou hodnotu, pokud existuje, metoda vrátí volajícímu delegáta. To se označuje jako vyvolání delegáta. Delegáta instancí mohou být vyvolány, jako by šlo zabalené metoda sama. Příklad:  
  
 [!code-csharp[csProgGuideDelegates#22](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_2.cs)]  
  
 [!code-csharp[csProgGuideDelegates#23](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_3.cs)]  
  
 Delegát typy jsou odvozeny od <xref:System.Delegate> – třída v rozhraní .NET Framework. Delegát typy jsou [zapečetěné](../../../csharp/language-reference/keywords/sealed.md)– nemůže být odvozen od – a není možné vlastní odvozovat z <xref:System.Delegate>. Protože instancí delegát je objekt, může být předána jako parametr, nebo přiřadit k vlastnosti. To umožňuje metoda přijmout delegáta jako parametr a volání delegáta později. To se označuje jako asynchronní zpětné volání a je běžnou metodu, jak po dokončení dlouho proces upozornění volající. Při použití delegáta tímto způsobem kódu pomocí delegát nemusí vůbec dozvěděl o provádění použité metody. Funkce je podobná zapouzdření, které poskytují rozhraní.  
  
 Další běžné použití zpětná volání je definování vlastní porovnání metoda a předání přidělíte metoda řazení. To umožňuje volajícího kódu, který se stane součástí algoritmus řazení. Následující příklad metoda používá `Del` typ jako parametr:  
  
 [!code-csharp[csProgGuideDelegates#24](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_4.cs)]  
  
 Potom můžete předat delegáta vytvořili výše této metody:  
  
 [!code-csharp[csProgGuideDelegates#25](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_5.cs)]  
  
 a zobrazit následující výstup do konzoly:  
  
 `The number is: 3`  
  
 Použití delegáta jako abstrakci, `MethodWithCallback` není nutné volat přímo konzole – nemusí se měly navrhovat s konzolou v paměti. Co `MethodWithCallback` nemá je jednoduše Příprava řetězec a předejte řetězec na jinou metodu. To je zvláště efektivní, protože delegované metodu můžete použít libovolný počet parametrů.  
  
 Když se delegáta zabalit metody instance, odkazuje na instanci a metodu delegáta. Delegát nemá žádné informace o instanci typu bez ohledu na metodu, kterou se zabalí, proto delegáta může být jakéhokoli typu objektu, dokud je metodu na tento objekt, který odpovídá delegáta. Když se k zabalení statickou metodu delegáta, pouze odkazuje na metodu. Vezměte v úvahu následující deklarace:  
  
 [!code-csharp[csProgGuideDelegates#26](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_6.cs)]  
  
 Společně s statických `DelegateMethod` uvedený výše, nyní je k dispozici tři metody, které může být zabalen `Del` instance.  
  
 Delegát můžete volat více než jedna metoda po vyvolání. To se označuje jako vícesměrového vysílání. Můžete přidat další metodu do seznamu delegáta metod – seznamu vyvolání – jednoduše vyžaduje přidání dvě delegáti pomocí přidání nebo přidání operátory přiřazení ('+' nebo '+='). Příklad:  
  
 [!code-csharp[csProgGuideDelegates#27](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_7.cs)]  
  
 V tomto okamžiku `allMethodsDelegate` obsahuje tři metody, které ve svém seznamu volání –`Method1`, `Method2`, a `DelegateMethod`. Původní tři delegáty `d1`, `d2`, a `d3`, zůstanou beze změny. Když `allMethodsDelegate` je vyvolána, všechny tři metody se nazývají v pořadí. Pokud delegát používá parametry odkaz, odkaz je předán postupně všechny tři metody zase, a všechny změny pomocí jedné metody jsou viditelné pro další metodou. Pokud některou z metod vyvolá výjimku, která není zachycena v rámci metody, výjimka je předán volající delegát a žádná další metody v seznamu volání se nazývají. Pokud delegát má návratovou hodnotu a/nebo výstupní parametry, vrátí návratovou hodnotu a parametry poslední volaná metoda. Chcete-li odebrat ze seznamu volání metody, použijte snížení nebo snížení operátor přiřazení ('-' nebo ' '-=''). Příklad:  
  
 [!code-csharp[csProgGuideDelegates#28](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_8.cs)]  
  
 Protože delegáta typy jsou odvozeny od `System.Delegate`, lze volat metody a vlastnosti definované třídy u delegát. Například počet metod najdete v seznamu vyvolání tohoto delegáta může napíšete:  
  
 [!code-csharp[csProgGuideDelegates#29](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_9.cs)]  
  
 Delegáti s více než jedna metoda v jejich seznamu volání odvozena od <xref:System.MulticastDelegate>, což je podtřídou třídy `System.Delegate`. Ve výše uvedeném kódu funguje v obou případech, protože obě třídy podporují `GetInvocationList`.  
  
 Vícesměroví Delegáti jsou používány při zpracování událostí. Objekty zdroje událostí odesílání oznámení o událostech příjemce objekty, které mají registrovaná pro příjem tuto událost. Registrace pro událost, příjemce vytvoří metodu navržený tak, aby zpracovat událost, pak vytvoří delegáta pro danou metodu a předá delegát zdroj události. Zdroj vyvolá delegáta, dojde k události. Delegát pak zavolá metodu na straně příjemce doručování data události zpracování událostí. Typ delegáta pro danou událost je definována podle zdroje události. Další informace najdete v tématu [události](../../../csharp/programming-guide/events/index.md).  
  
 Porovnání delegáti dva různé typy přiřazen při kompilaci způsobí chybu kompilace. Pokud delegát instance jsou staticky typu `System.Delegate`, pak je povolené porovnání, spustí se však isfocusineditor hodnotu false na čas. Příklad:  
  
 [!code-csharp[csProgGuideDelegates#30](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_10.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Použití odchylek v delegátech](http://msdn.microsoft.com/library/e6acad03-93e0-4efb-a158-8696d5eb4ecf)  
 [Odchylky v delegátech](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)  
 [Použití odchylek pro Func a akce obecní delegáti](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290)  
 [Události](../../../csharp/programming-guide/events/index.md)
