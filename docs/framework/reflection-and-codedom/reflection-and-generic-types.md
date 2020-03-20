---
title: Reflexe a obecné typy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic types
- reflection, generic types
- type arguments
- generics [.NET Framework], reflection
- viewing type information
- type information, viewing
- types, generic
- type parameters
ms.assetid: f7180fc5-dd41-42d4-8a8e-1b34288e06de
ms.openlocfilehash: 4894b5cc64dca431c8d05b638847dd6cb7017bde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180494"
---
# <a name="reflection-and-generic-types"></a>Reflexe a obecné typy
Z hlediska reflexe je rozdíl mezi obecným typem a běžným typem, že obecný typ má k němu přidruženou sadu parametrů typu (pokud se jedná o definici obecného typu) nebo argumenty typu (pokud se jedná o konstruovaný typ). Obecná metoda se liší od běžné metody stejným způsobem.  
  
 Existují dva klíče k pochopení, jak reflexe zpracovává obecné typy a metody:  
  
- Parametry typu definic obecných typů a definic obecných metod <xref:System.Type> jsou reprezentovány instancemi třídy.  
  
    > [!NOTE]
    > Mnoho vlastností <xref:System.Type> a metod mají <xref:System.Type> různé chování, když objekt představuje parametr obecného typu. Tyto rozdíly jsou popsány v tématech vlastností a metody. Viz například <xref:System.Type.IsAutoClass%2A> <xref:System.Type.DeclaringType%2A>a . Kromě toho některé členy jsou <xref:System.Type> platné pouze v případě, že objekt představuje parametr obecného typu. Například viz <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Pokud instance <xref:System.Type> představuje obecný typ, pak obsahuje pole typů, které představují parametry typu (pro definice obecných typů) nebo argumenty typu (pro konstruované typy). Totéž platí pro instanci třídy, <xref:System.Reflection.MethodInfo> která představuje obecnou metodu.  
  
 Reflexe poskytuje <xref:System.Type> <xref:System.Reflection.MethodInfo> metody a které umožňují přístup k poli parametrů typu a <xref:System.Type> určit, zda instance představuje parametr typu nebo skutečný typ.  
  
 Například kód demonstrující metody popsané zde naleznete v [tématu How to: Examine and Instantiate Generic Types with Reflection](how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Následující diskuse předpokládá znalost terminologie obecných typů, jako je například rozdíl mezi parametry typu a argumenty a otevřené nebo uzavřené konstruované typy. Další informace naleznete [v tématu Generics](../../standard/generics/index.md).  

## <a name="is-this-a-generic-type-or-method"></a>Jedná se o obecný typ nebo metodu?  
 Při použití reflexe zkoumat neznámý typ, reprezentované instance <xref:System.Type>, použijte <xref:System.Type.IsGenericType%2A> vlastnost k určení, zda neznámý typ je obecný. Vrátí, `true` pokud je typ obecný. Podobně při zkoumání neznámé metody, reprezentované <xref:System.Reflection.MethodInfo> instancí <xref:System.Reflection.MethodBase.IsGenericMethod%2A> třídy, použijte vlastnost k určení, zda je metoda obecná.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Jedná se o obecnou definici typu nebo metody?  
 Pomocí <xref:System.Type.IsGenericTypeDefinition%2A> vlastnosti určete, zda <xref:System.Type> objekt představuje definici <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> obecného typu, a pomocí metody určete, zda představuje <xref:System.Reflection.MethodInfo> definici obecné metody.  
  
 Obecné definice typů a metod jsou šablony, ze kterých jsou vytvářeny typy, ze kterých lze vytvořit. Obecné typy v knihovně tříd rozhraní <xref:System.Collections.Generic.Dictionary%602>.NET Framework, například , jsou definice obecných typů.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Je typ nebo metoda otevřená nebo uzavřená?  
 Obecný typ nebo metoda je uzavřena, pokud byly nahradit všechny jeho parametry typu, včetně všech parametrů typu všech ohraničujících typů. Instanci obecného typu lze vytvořit pouze v případě, že je uzavřena. Vlastnost <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> vrátí, `true` pokud je otevřený typ. Pro metody <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> metoda provádí stejnou funkci.

## <a name="generating-closed-generic-types"></a>Generování uzavřených obecných typů  
 Jakmile máte obecný typ nebo definici <xref:System.Type.MakeGenericType%2A> metody, použijte metodu <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> k vytvoření <xref:System.Reflection.MethodInfo> uzavřeného obecného typu nebo metodu k vytvoření pro uzavřenou obecnou metodu.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Získání obecného typu nebo definice metody  
 Pokud máte otevřený obecný typ nebo metodu, která není obecnýtyp nebo definice metody, nelze vytvořit instance a nelze zadat parametry typu, které chybí. Musíte mít obecný typ nebo definici metody. Pomocí <xref:System.Type.GetGenericTypeDefinition%2A> metody získáte definici obecného <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> typu nebo metodu k získání definice obecné metody.  
  
 Například pokud máte <xref:System.Type> objekt představující `Dictionary<int, string>` `Dictionary(Of Integer, String)` ( v jazyce Visual Basic) `Dictionary<string, MyClass>`a chcete <xref:System.Type.GetGenericTypeDefinition%2A> vytvořit typ <xref:System.Type> , `Dictionary<TKey, TValue>` můžete použít <xref:System.Type.MakeGenericType%2A> metodu získat <xref:System.Type> představující `Dictionary<int, MyClass>`a potom použít metodu k vytvoření představující .  
  
 Příklad otevřeného obecného typu, který není obecným typem, naleznete dále v tomto tématu v části Typ parametru nebo Argument typu.

## <a name="examining-type-arguments-and-type-parameters"></a>Zkoumání argumentů typu a parametrů typu  
 Pomocí <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> metody můžete získat <xref:System.Type> pole objektů, které představují parametry typu nebo argumenty <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> typu obecného typu, a použijte metodu k tomu, abyste totéž udělali pro obecnou metodu.  
  
 Jakmile víte, <xref:System.Type> že objekt představuje parametr typu, existuje mnoho dalších otázek reflexe může odpovědět. Můžete určit zdroj parametru typu, jeho umístění a jeho omezení.  
  
### <a name="type-parameter-or-type-argument"></a>Parametr typu nebo typ argument  
 Chcete-li zjistit, zda je určitý prvek pole parametrem <xref:System.Type.IsGenericParameter%2A> typu nebo argumentem typu, použijte vlastnost. Vlastnost <xref:System.Type.IsGenericParameter%2A> je, `true` pokud je prvek parametrem typu.  
  
 Obecný typ může být otevřen, aniž by byl definicí obecného typu, v takovém případě má kombinaci argumentů typu a parametrů typu. Například v následujícím kódu `D` je třída odvozena od typu vytvořeného nahrazením prvního parametru `D` typu `B`parametru druhého typu .  
  
```csharp  
class B<T, U> {}  
class D<V, W> : B<int, V> {}  
```  
  
```vb  
Class B(Of T, U)  
End Class  
Class D(Of V, W)  
    Inherits B(Of Integer, V)  
End Class  
```  
  
```cpp  
generic<typename T, typename U> ref class B {};  
generic<typename V, typename W> ref class D : B<int, V> {};  
```  
  
 Pokud získáte <xref:System.Type> objekt představující `D<V, W>` a <xref:System.Type.BaseType%2A> použít vlastnost k získání jeho `type B<int, V>` základní typ, výsledný je otevřen, ale není definice obecného typu.  
  
### <a name="source-of-a-generic-parameter"></a>Zdroj obecného parametru  
 Obecný parametr typu může pocházet z typu, který zkoumáte, z ohraničujícího typu nebo z obecné metody. Zdroj parametru obecného typu můžete určit následujícím způsobem:  
  
- Nejprve použijte <xref:System.Type.DeclaringMethod%2A> vlastnost k určení, zda parametr typu pochází z obecné metody. Pokud hodnota vlastnosti není nulový odkaz (`Nothing` v jazyce Visual Basic), pak zdroj je obecná metoda.  
  
- Pokud zdroj není obecná metoda, <xref:System.Type.DeclaringType%2A> použijte vlastnost k určení obecného typu, ke kterému patří parametr obecného typu.  
  
 Pokud parametr typu patří do obecné <xref:System.Type.DeclaringType%2A> metody, vlastnost vrátí typ, který deklaroval obecnou metodu, což je irelevantní.  
  
### <a name="position-of-a-generic-parameter"></a>Pozice obecného parametru  
 Ve výjimečných situacích je nutné určit pozici parametru typu v seznamu parametrů typu jeho deklarující třídy. Předpokládejme například, <xref:System.Type> že máte `B<int, V>` objekt představující typ z předchozího příkladu. Metoda <xref:System.Type.GetGenericArguments%2A> poskytuje seznam argumentů typu a při `V` kontrole můžete <xref:System.Type.DeclaringMethod%2A> použít <xref:System.Type.DeclaringType%2A> vlastnosti a zjistit, odkud pochází. Vlastnost pak můžete <xref:System.Type.GenericParameterPosition%2A> použít k určení její pozice v seznamu parametrů typu, kde byla definována. V tomto `V` příkladu je na pozici 0 (nula) v seznamu parametrů typu, kde byl definován.  
  
### <a name="base-type-and-interface-constraints"></a>Základní typ a omezení rozhraní  
 Pomocí <xref:System.Type.GetGenericParameterConstraints%2A> metody můžete získat omezení základního typu a omezení rozhraní parametru typu. Pořadí prvků pole není významné. Prvek představuje omezení rozhraní, pokud se jedná o typ rozhraní.  
  
### <a name="generic-parameter-attributes"></a>Atributy obecných parametrů  
 Vlastnost <xref:System.Type.GenericParameterAttributes%2A> získá <xref:System.Reflection.GenericParameterAttributes> hodnotu, která označuje odchylku (kovariance nebo contravariance) a zvláštní omezení parametru typu.  
  
#### <a name="covariance-and-contravariance"></a>Kovariance a kontravariance  
 Chcete-li zjistit, zda parametr typu je kovariantní <xref:System.Reflection.GenericParameterAttributes> nebo kontravariantní, <xref:System.Type.GenericParameterAttributes%2A> použijte masku <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> na hodnotu, která je vrácena vlastností. Pokud je <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>výsledek , parametr typu je invariantní. Viz [Kovariance a Contravariance](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Zvláštní omezení  
 Chcete-li určit zvláštní omezení parametru <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> typu, <xref:System.Reflection.GenericParameterAttributes> použijte masku na <xref:System.Type.GenericParameterAttributes%2A> hodnotu, která je vrácena vlastností. Pokud je <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>výsledek , neexistují žádná zvláštní omezení. Parametr typu může být omezen na typ odkazu, jako typ hodnoty s hodnotou, který nelze hodnotit a zda má konstruktor bez parametrů.

## <a name="invariants"></a>Invariants  
 Tabulka invariantních podmínek pro běžné termíny v <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>reflexi pro obecné typy naleznete v tématu . Další termíny týkající se obecných metod naleznete v tématu <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  

## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Ukazuje, jak používat vlastnosti <xref:System.Type> <xref:System.Reflection.MethodInfo> a metody a zkoumat obecné typy.|  
|[Obecné typy](../../standard/generics/index.md)|Popisuje funkci obecných typů a způsob, jakým je podporován v rozhraní .NET Framework.|  
|[Postupy: Definování obecného typu pomocí generování reflexe](how-to-define-a-generic-type-with-reflection-emit.md)|Ukazuje, jak použít odraz emitují generovat obecné typy v dynamických sestaveních.|  
|[Zobrazení informací o typu](viewing-type-information.md)|Popisuje třídu <xref:System.Type> a poskytuje příklady kódu, <xref:System.Type> které ilustrují, jak používat s různými třídami odrazu k získání informací o konstruktorech, metodách, polích, vlastnostech a událostech.|
