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
Z hlediska reflexe rozdíl mezi obecným typem a běžným typem je, že obecný typ je přidružen k sadě parametrů typu (Pokud se jedná o definici obecného typu) nebo k argumentům typu (Pokud se jedná o konstruovaný typ). Obecná metoda se od běžné metody liší stejným způsobem.  
  
 Existují dva klíče pro porozumění, jak reflexe zpracovává obecné typy a metody:  
  
- Parametry typu definic obecných typů a definice obecných metod jsou reprezentovány instancemi <xref:System.Type> třídy.  
  
    > [!NOTE]
    > Mnoho vlastností a metod <xref:System.Type> má jiné chování, pokud <xref:System.Type> objekt představuje parametr obecného typu. Tyto rozdíly jsou zdokumentovány v tématech vlastností a metod. Například viz <xref:System.Type.IsAutoClass%2A> a <xref:System.Type.DeclaringType%2A>. Kromě toho jsou některé členy platné pouze v případě, <xref:System.Type> že objekt představuje parametr obecného typu. Příklad naleznete v tématu <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Pokud instance <xref:System.Type> představuje obecný typ, obsahuje pole typů, které představují parametry typu (pro definice obecného typu), nebo argumenty typu (pro konstruované typy). Totéž platí pro instanci <xref:System.Reflection.MethodInfo> třídy, která představuje obecnou metodu.  
  
 Reflexe poskytuje <xref:System.Type> metody <xref:System.Reflection.MethodInfo> a, které umožňují přístup k poli parametrů typu a k určení, zda instance <xref:System.Type> představuje parametr typu nebo skutečný typ.  
  
 Příklad kódu, který demonstruje popsané metody, naleznete v tématu [How to: prozkoumávat and instance Generic Types with reflexe](how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Následující diskuze předpokládá znalost s terminologií generických typů, například rozdíl mezi parametry typu a argumenty a otevřenými nebo uzavřenými konstruovanými typy. Další informace najdete v tématu [Obecné typy](../../standard/generics/index.md).  

## <a name="is-this-a-generic-type-or-method"></a>Jedná se o obecný typ nebo metodu?  
 Použijete-li reflexi k prohlédnutí neznámého typu reprezentovaného instancí <xref:System.Type>, <xref:System.Type.IsGenericType%2A> použijte vlastnost k určení, zda je neznámý typ obecný. Vrátí `true` , pokud je typ obecný. Podobně při kontrole neznámé metody reprezentované instancí <xref:System.Reflection.MethodInfo> třídy použijte <xref:System.Reflection.MethodBase.IsGenericMethod%2A> vlastnost k určení, zda je metoda obecná.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Je tento obecný typ nebo definice metody?  
 Použijte <xref:System.Type.IsGenericTypeDefinition%2A> vlastnost k určení, zda <xref:System.Type> objekt představuje definici obecného typu, a použijte <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> metodu k určení, zda <xref:System.Reflection.MethodInfo> představuje definici obecné metody.  
  
 Definice obecného typu a metody jsou šablony, ze kterých jsou vytvářeny typy instantiable. Obecné typy v knihovně tříd .NET Framework, například <xref:System.Collections.Generic.Dictionary%602>, jsou definice obecného typu.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Je typ nebo metoda otevřená nebo uzavřená?  
 Obecný typ nebo metoda jsou uzavřeny, pokud byly nahrazeny typy instantiable pro všechny parametry typu, včetně všech typových parametrů všech nadřazených typů. Můžete vytvořit pouze instanci obecného typu, pokud je zavřena. <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Vlastnost vrátí `true` , zda je typ otevřen. Pro metody <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> metoda provádí stejnou funkci.

## <a name="generating-closed-generic-types"></a>Generování uzavřených obecných typů  
 Po definování obecného typu nebo definice metody použijte <xref:System.Type.MakeGenericType%2A> metodu pro vytvoření zavřeného obecného typu nebo <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> metody pro vytvoření <xref:System.Reflection.MethodInfo> pro uzavřenou obecnou metodu.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Získání obecného typu nebo definice metody  
 Pokud máte otevřený obecný typ nebo metodu, která není obecným typem nebo definicí metody, nemůžete vytvořit jejich instance a nemůžete zadat chybějící parametry typu. Je nutné mít definici obecného typu nebo metody. Použijte <xref:System.Type.GetGenericTypeDefinition%2A> metodu k získání definice obecného typu nebo <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> metody pro získání definice obecné metody.  
  
 Například pokud máte <xref:System.Type> objekt, `Dictionary<int, string>` který představuje (`Dictionary(Of Integer, String)` v Visual Basic) a chcete vytvořit typ `Dictionary<string, MyClass>`, můžete použít <xref:System.Type.GetGenericTypeDefinition%2A> metodu k získání <xref:System.Type> reprezentace `Dictionary<TKey, TValue>` a následné použití <xref:System.Type.MakeGenericType%2A> metody k vytvoření <xref:System.Type> reprezentace. `Dictionary<int, MyClass>`  
  
 Příklad otevřeného obecného typu, který není obecný typ, naleznete v části "parametr typu nebo argument typu" dále v tomto tématu.

## <a name="examining-type-arguments-and-type-parameters"></a>Zkoumání argumentů typu a parametrů typu  
 Použijte <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> metodu k získání pole <xref:System.Type> objektů, které reprezentují parametry typu nebo argumenty typu obecného typu, a použijte <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> metodu pro provedení stejné pro obecnou metodu.  
  
 Jakmile víte, že <xref:System.Type> objekt představuje parametr typu, může odpovědět mnoho dalších otázek. Můžete určit zdroj parametru typu, jeho umístění a jeho omezení.  
  
### <a name="type-parameter-or-type-argument"></a>Parametr typu nebo argument typu  
 Chcete-li určit, zda je konkrétní prvek pole parametr typu nebo argumentem typu, použijte <xref:System.Type.IsGenericParameter%2A> vlastnost. <xref:System.Type.IsGenericParameter%2A> Vlastnost je `true` , pokud je element parametrem typu.  
  
 Obecný typ může být otevřen bez definice obecného typu. v takovém případě má kombinaci typů argumentů a parametrů typu. Například v následujícím kódu je třída `D` odvozena z typu vytvořeného nahrazením prvního parametru typu `D` pro druhý parametr typu. `B`  
  
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
  
 Pokud získáte <xref:System.Type> objekt představující `D<V, W>` a použít <xref:System.Type.BaseType%2A> vlastnost k získání svého základního typu, je výsledek `type B<int, V>` otevřen, ale není to definice obecného typu.  
  
### <a name="source-of-a-generic-parameter"></a>Zdroj obecného parametru  
 Parametr obecného typu může pocházet z typu, který zkoumáte, z nadřazeného typu nebo z obecné metody. Zdroj parametru obecného typu můžete určit následujícím způsobem:  
  
- Nejprve použijte <xref:System.Type.DeclaringMethod%2A> vlastnost k určení, zda parametr typu pochází z obecné metody. Pokud hodnota vlastnosti není odkaz s hodnotou null (`Nothing` v Visual Basic), pak je zdrojem obecná metoda.  
  
- Pokud zdroj není obecná metoda, použijte <xref:System.Type.DeclaringType%2A> vlastnost k určení obecného typu, ke kterému parametr obecného typu patří.  
  
 Pokud parametr typu patří do obecné metody, <xref:System.Type.DeclaringType%2A> vlastnost vrátí typ, který deklaruje obecnou metodu, která je nerelevantní.  
  
### <a name="position-of-a-generic-parameter"></a>Pozice obecného parametru  
 Ve vzácných situacích je nutné určit pozici parametru typu v seznamu parametrů typu své deklarované třídy. Předpokládejme například, že máte <xref:System.Type> objekt reprezentující `B<int, V>` typ z předchozího příkladu. <xref:System.Type.GetGenericArguments%2A> Metoda poskytuje seznam argumentů typu a při kontrole `V` můžete použít vlastnosti <xref:System.Type.DeclaringMethod%2A> a <xref:System.Type.DeclaringType%2A> k zjištění, odkud pochází. Pak můžete použít <xref:System.Type.GenericParameterPosition%2A> vlastnost k určení jeho pozice v seznamu parametrů typu, kde byl definován. V tomto příkladu je `V` na pozici 0 (nula) v seznamu parametrů typu, kde byl definován.  
  
### <a name="base-type-and-interface-constraints"></a>Základní typ a omezení rozhraní  
 Použijte <xref:System.Type.GetGenericParameterConstraints%2A> metodu pro získání omezení základního typu a omezení rozhraní parametru typu. Pořadí prvků pole není významné. Element představuje omezení rozhraní, pokud se jedná o typ rozhraní.  
  
### <a name="generic-parameter-attributes"></a>Obecné atributy parametru  
 <xref:System.Type.GenericParameterAttributes%2A> Vlastnost vrací <xref:System.Reflection.GenericParameterAttributes> hodnotu, která označuje odchylku (kovarianci nebo kontravariance) a zvláštní omezení parametru typu.  
  
#### <a name="covariance-and-contravariance"></a>Kovariance a kontravariance  
 Chcete-li určit, zda je parametr typu kovariantní nebo kontravariantní <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> , použijte masku <xref:System.Reflection.GenericParameterAttributes> na hodnotu, která je vrácena <xref:System.Type.GenericParameterAttributes%2A> vlastností. Pokud je <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>výsledek, parametr typu je invariantní. Viz [kovariance a kontravariance](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Speciální omezení  
 Chcete-li určit zvláštní omezení parametru typu, použijte <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> masku na <xref:System.Reflection.GenericParameterAttributes> hodnotu, která je vrácena <xref:System.Type.GenericParameterAttributes%2A> vlastností. Pokud je <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>výsledkem, neexistují žádná zvláštní omezení. Parametr typu může být omezen na typ odkazu, na typ hodnoty neumožňující hodnotu null a musí mít konstruktor bez parametrů.

## <a name="invariants"></a>Invariantní  
 Tabulka neutrálních podmínek pro běžné výrazy v reflexi pro obecné typy naleznete v tématu <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Další podmínky týkající se obecných metod naleznete v tématu <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  

## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Ukazuje, jak používat vlastnosti a metody <xref:System.Type> a <xref:System.Reflection.MethodInfo> k prozkoumávání obecných typů.|  
|[Obecné typy](../../standard/generics/index.md)|Popisuje funkci Generics a způsob jejího podporování v .NET Framework.|  
|[Postupy: Definování obecného typu pomocí generování reflexe](how-to-define-a-generic-type-with-reflection-emit.md)|Ukazuje, jak pomocí generování reflexe generovat obecné typy v dynamických sestaveních.|  
|[Zobrazení informací o typu](viewing-type-information.md)|Popisuje <xref:System.Type> třídu a poskytuje příklady kódu, které ilustrují, jak použít <xref:System.Type> s různými třídami reflexe k získání informací o konstruktorech, metodách, polích, vlastnostech a událostech.|
