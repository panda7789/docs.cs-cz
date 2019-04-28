---
title: Použití delegátů - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: eb5721d1c04ad761821bcdae03159f290a802ec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711158"
---
# <a name="using-delegates-c-programming-guide"></a>Použití delegátů (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) je typ, který zapouzdřuje bezpečně metodu, podobně jako ukazatel na funkci v jazyce C a C++. Na rozdíl od ukazatelů na funkce jazyka C Delegáti jsou objektově orientované, zadejte bezpečným a zabezpečeným. Podle názvu delegáta je definován typ delegátu. Následující příklad deklaruje delegáta s názvem `Del` , který může zapouzdřit metodu, která přijímá [řetězec](../../../csharp/language-reference/keywords/string.md) jako argument a vrátí [void](../../../csharp/language-reference/keywords/void.md):  
  
 [!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]  
  
 Objekt delegáta je obvykle vytvářený poskytující název metody delegáta pro obtékání, nebo se [anonymní metoda](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md). Jakmile je vytvořena instance delegáta, metoda volání delegáta se předá podle delegáta k této metodě. Parametry předané do delegáta volajícím jsou předány do metody a návratovou hodnotu, pokud existuje, metoda je vrátit zpět volajícímu delegátem. To se označuje jako vyvolání delegáta. Instance delegát lze vyvolat, jako by šlo zabalené metoda sama. Příklad:  
  
 [!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  
  
 [!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]  
  
 Typy delegátů jsou odvozeny z <xref:System.Delegate> třídy v rozhraní .NET Framework. Typy delegátů jsou [zapečetěné](../../../csharp/language-reference/keywords/sealed.md)– nemůže být odvozen od – a není možné vlastní odvozovat z <xref:System.Delegate>. Protože instance delegáta je objekt, může být předán jako parametr, nebo přidruženo k vlastnosti. Díky tomu metoda přijmout delegáta jako parametr a volání delegáta později. To se označuje jako asynchronního zpětného volání a se o běžnou metodu oznámit volajícím po dokončení dlouho procesu. Při použití delegáta tímto způsobem kódu pomocí delegáta není nutné žádnou znalost implementace metody se používají. Funkce je podobný zapouzdření poskytované rozhraní.  
  
 Dalším běžným způsobem použití zpětných volání je definování vlastní porovnávací metody a předáním delegátu metoda řazení. To umožňuje volajícího kódu se stanou součástí algoritmu řazení. Metoda následující příklad používá `Del` typ jako parametr:  
  
 [!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]  
  
 Můžete předat delegáta k této metodě vytvořili výše:  
  
 [!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]  
  
 a zobrazí následující výstup do konzoly:  
  
 `The number is: 3`  
  
 Pomocí delegáta jako o abstrakci `MethodWithCallback` není potřeba přímo volat konzole – není nutné navrhovat pomocí konzoly v úvahu. Co `MethodWithCallback` nemá je jednoduše Příprava řetězce a předat řetězec na jinou metodu. To je zvláště efektivní, protože delegované metodu můžete použít libovolný počet parametrů.  
  
 Při delegáta je vytvořen při zabalení metodu instance, odkazuje na instanci a metody delegáta. Delegát nezná žádný typ instance kromě metody, který ho zalamoval, tak delegát mohou odkazovat na libovolný typ objektu, za předpokladu, metoda je k tomuto objektu, který odpovídá signatuře delegátu. Když se zabalit statické metody delegáta, pouze odkazuje na metodu. Vezměte v úvahu následující deklarace:  
  
 [!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]  
  
 Spolu s statické `DelegateMethod` uvedenému výše, teď máme tři metody, které mohou být zabaleny třídou `Del` instance.  
  
 Delegát může volat více než jednu metodu při vyvolání. To se označuje jako vícesměrové vysílání. Přidat další metodu do seznamu delegáta z metody – v seznamu vyvolání – jednoduše vyžaduje přidání dvou delegátů pomocí přidání ani operátory přiřazení sčítání ('+' nebo '+'). Příklad:  
  
 [!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]  
  
 V tomto okamžiku `allMethodsDelegate` obsahuje tři metody v jeho vyvolávacím seznamu –`Method1`, `Method2`, a `DelegateMethod`. Původní tři delegáty `d1`, `d2`, a `d3`, zůstanou beze změny. Když `allMethodsDelegate` je vyvolána, všechny tři metody jsou volány v pořadí. Pokud delegát používá parametry odkazů, odkaz je předán postupně pro každý ze tří metod zase a jsou viditelné pro další metoda změny pomocí metod. Pokud některou z metod vyvolá výjimku, která není zachycena v metodě, že výjimka je předán volajícímu metody delegáta a žádné další metody v seznamu vyvolání jsou volány. Pokud delegát má návratovou hodnotu a/nebo výstupní parametry, vrátí se návratová hodnota a parametry poslední metody, vyvolala. Pokud chcete odebrat ze seznamu vyvolání metody, použijte snížení nebo snížení operátor přiřazení ("-" nebo "-=.). Příklad:  
  
 [!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]  
  
 Protože typy delegátů jsou odvozeny z `System.Delegate`, metody a vlastnosti určené třídy lze volat delegátu. Například pokud chcete zjistit počet metod v seznamu vyvolání tohoto delegáta, můžete zadat:  
  
 [!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]  
  
 Delegáti s více než jednu metodu do svého seznamu vyvolání odvozovat <xref:System.MulticastDelegate>, která je podtřídou třídy `System.Delegate`. Výše uvedený kód funguje v obou případech, protože obě třídy podporují `GetInvocationList`.  
  
 Delegáti jsou často používány při zpracování událostí. Objekty zdroje událostí odesílání oznámení o událostech příjemce objekty, které jste zaregistrováni k odběru příslušné události. K registraci na událost, příjemce vytvoří metodu určený ke zpracování událostí, pak vytvoří delegáta pro danou metodu a předává delegáta zdroji události. Zdroj volání delegáta při výskytu události. Delegát pak zavolá metodu na straně příjemce, poskytování dat událostí zpracování událostí. Typ delegáta pro danou událost je definován ve zdroji události. Další informace najdete v tématu [události](../../../csharp/programming-guide/events/index.md).  
  
 Porovnání delegáti dva různé typy, které jsou přiřazeny v době kompilace způsobí chybu kompilace. Pokud instance delegátů jsou staticky typu `System.Delegate`, pak je povolené porovnání, spustí se však návratovou hodnotu false v čase. Příklad:  
  
 [!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
- [Použití odchylek v delegátech](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)
- [Odchylky v delegátech](../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Použití odchylek pro obecné delegáty Func a Action](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Události](../../../csharp/programming-guide/events/index.md)
