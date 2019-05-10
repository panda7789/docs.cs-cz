---
title: Reflexe a obecné typy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0536acbcc71ae7792ec668ac352e95e604bd979
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591367"
---
# <a name="reflection-and-generic-types"></a>Reflexe a obecné typy
<a name="top"></a> Z hlediska odrazu, rozdíl mezi obecného typu a běžný typ je, že obecného typu k němu má přidružené sady parametrů typu (Pokud je definice obecného typu) nebo zadejte argumenty (je-li konstruovaný typ). Obecné metody se liší od běžné metody stejným způsobem.  
  
 Existují dva klíče pro pochopení způsobu, jakým zpracovává reflexe obecné typy a metody:  
  
- Parametry typu definice obecného typu a definice obecné metody jsou reprezentovány instance <xref:System.Type> třídy.  
  
    > [!NOTE]
    >  Mnoho vlastností a metod <xref:System.Type> mít jiné chování při <xref:System.Type> objekt představuje parametr obecného typu. Tyto rozdíly jsou popsány v tématech vlastnosti a metody. Viz například <xref:System.Type.IsAutoClass%2A> a <xref:System.Type.DeclaringType%2A>. Navíc se někteří členové jsou platné pouze tehdy, když <xref:System.Type> objekt představuje parametr obecného typu. Viz například <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Pokud instance <xref:System.Type> reprezentuje obecný typ, a zahrnuje celou řadu typů, které představují parametry typu (pro definice obecného typu) nebo zadejte argumenty typu (pro sestavené typy). Totéž platí instance <xref:System.Reflection.MethodInfo> třídu, která představuje obecnou metodou.  
  
 Poskytuje metody reflexe <xref:System.Type> a <xref:System.Reflection.MethodInfo> , které umožňují pro přístup k poli parametrů typu a k určení, zda instance <xref:System.Type> reprezentuje parametr typu nebo skutečným typem.  
  
 Například kód ukázka metody popsané tady zobrazit [jak: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Následující diskuse předpokládá znalost terminologie obecných typů, jako je rozdíl mezi parametry typu a argumenty a typy konstrukcí otevřeno nebo Uzavřeno. Další informace najdete v tématu [obecných typů](../../../docs/standard/generics/index.md).  
  
 Tento přehled obsahuje následující části:  
  
- [Obecný typ nebo metoda, je to?](#is_this_a_generic_type_or_method)  
  
- [Generování uzavřených obecných typů](#generating_closed_generic_types)  
  
- [Zkoumání argumentů a parametrů typu](#examining_type_arguments)  
  
- [Výstupních podmínek](#invariants)  
  
- [Související témata](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>Obecný typ nebo metoda, je to?  
 Při použití reflexe prozkoumat neznámého typu, reprezentovaný instance <xref:System.Type>, použijte <xref:System.Type.IsGenericType%2A> a určí, zda je neznámý typ obecný. Vrátí `true` Pokud typ není obecný. Podobně při kontrole Neznámá metoda, reprezentovaný instancí <xref:System.Reflection.MethodInfo> třídy, použijte <xref:System.Reflection.MethodBase.IsGenericMethod%2A> a určí, zda metoda je obecná.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Je to obecného typu nebo metodě?  
 Použít <xref:System.Type.IsGenericTypeDefinition%2A> a určí, zda <xref:System.Type> objekt představuje definici obecného typu a použití <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> metodou ke zjištění, zda <xref:System.Reflection.MethodInfo> představuje definici obecné metody.  
  
 Definice obecného typu a metody jsou šablony, ze které se vytvářejí instantiable typy. Obecné typy v knihovně tříd rozhraní .NET Framework, jako <xref:System.Collections.Generic.Dictionary%602>, jsou definice obecného typu.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Tento typ nebo metoda je otevřeno nebo zavřeno?  
 Pokud byla nahrazena instantiable typy pro všechny její parametry typu, včetně všechny parametry typu všech ohraničujících typů, je uzavřen obecného typu nebo metody. Instance obecného typu lze vytvořit pouze pokud je uzavřený. <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Vrátí vlastnost `true` Pokud typ je otevřený. Pro metody <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> metoda provádí stejnou funkci.  
  
 [Zpět na začátek](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>Generování uzavřených obecných typů  
 Jakmile máte obecného typu nebo metodě, použijte <xref:System.Type.MakeGenericType%2A> metodu pro vytvoření uzavřený obecný typ nebo <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> metodu pro vytvoření <xref:System.Reflection.MethodInfo> uzavřené obecné metody.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Získávání obecného typu nebo metodě  
 Pokud máte otevřený obecný typ nebo metodu, která není obecného typu nebo metodě, nelze vytvořit instance a nelze zadat parametry typu, které nebyly nalezeny. Musíte mít definici obecného typu nebo metody. Použití <xref:System.Type.GetGenericTypeDefinition%2A> metodu k získání definice obecného typu nebo <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> metodu k získání definice obecné metody.  
  
 Pokud máte například <xref:System.Type> objekt představující `Dictionary<int, string>` (`Dictionary(Of Integer, String)` v jazyce Visual Basic) a rozhodli jste se vytvořit typ `Dictionary<string, MyClass>`, můžete použít <xref:System.Type.GetGenericTypeDefinition%2A> metodu k získání <xref:System.Type> představující `Dictionary<TKey, TValue>` a potom použijte <xref:System.Type.MakeGenericType%2A> metodu za účelem vytvoření <xref:System.Type> představující `Dictionary<int, MyClass>`.  
  
 Příklad otevřený obecný typ., který není obecný typ naleznete v tématu "Parametr typu nebo Argument typu" dále v tomto tématu.  
  
 [Zpět na začátek](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>Zkoumání argumentů a parametrů typu  
 Použít <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> metodu k získání pole <xref:System.Type> objekty, které představují parametry typu nebo typy argumentů obecného typu a použít <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> metoda škol obecné metody.  
  
 Jakmile budete vědět, že <xref:System.Type> reprezentuje parametr typu objektu, existuje mnoho další otázky, které dokáže odpovědět reflexe. Můžete určit parametr typu zdroje, jeho pozice a jeho omezení.  
  
### <a name="type-parameter-or-type-argument"></a>Parametr typu nebo Argument typu  
 Chcete-li zjistit, zda určitý element pole je parametr typu nebo typ argumentu, použijte <xref:System.Type.IsGenericParameter%2A> vlastnost. <xref:System.Type.IsGenericParameter%2A> Vlastnost `true` Pokud prvek je parametr typu.  
  
 Obecný typ může být otevřeno bez definice obecného typu, v takovém případě obsahuje kombinaci argumentů a parametrů typu. Například následující kód třídy `D` je odvozen z typu vytvořili nahrazením první parametr typu `D` pro druhý parametr typu `B`.  
  
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
  
 Pokud jste obdrželi <xref:System.Type> objekt představující `D<V, W>` a použít <xref:System.Type.BaseType%2A> vlastnost získat jeho základní typ, výsledná `type B<int, V>` je otevřený, ale není definice obecného typu.  
  
### <a name="source-of-a-generic-parameter"></a>Zdroj obecný parametr  
 Parametr obecného typu může pocházet z typu, který se, že zkoumáte, nadřazeného typu nebo obecné metody. Zdroj daného parametru obecného typu můžete zjistit takto:  
  
- Nejprve <xref:System.Type.DeclaringMethod%2A> a určí, zda je parametr typu pochází z obecné metody. Pokud hodnota vlastnosti není nulový odkaz (`Nothing` v jazyce Visual Basic), zdroj je obecná metoda.  
  
- Pokud zdroj není obecná metoda, použijte <xref:System.Type.DeclaringType%2A> patří vlastnosti k určení obecného typu parametru obecného typu.  
  
 Pokud parametr typu patří do obecné metody, <xref:System.Type.DeclaringType%2A> vlastnost vrátí typ, který deklarován obecné metody, která je relevantní.  
  
### <a name="position-of-a-generic-parameter"></a>Pozice obecný parametr  
 Ve výjimečných případech je potřeba určit pozici parametr typu v seznamu parametrů typu jeho deklarující třídy. Předpokládejme například, že máte <xref:System.Type> objekt představující `B<int, V>` typ z předchozího příkladu. <xref:System.Type.GetGenericArguments%2A> Metoda vám poskytne seznam argumentů typu, a při zkoumání `V` můžete použít <xref:System.Type.DeclaringMethod%2A> a <xref:System.Type.DeclaringType%2A> vlastnosti, které chcete zjišťovat, odkud. Pak můžete použít <xref:System.Type.GenericParameterPosition%2A> vlastnosti k určení jeho pozice v seznamu parametrů typu, kde byl definován. V tomto příkladu `V` je na pozici 0 (nula) v seznamu parametrů typu, kde byl definován.  
  
### <a name="base-type-and-interface-constraints"></a>Základní typ a Interface omezení  
 Použití <xref:System.Type.GetGenericParameterConstraints%2A> metodu k získání základního typu omezení a interface omezení parametru typu. Není důležité pořadí prvků pole. Element představuje omezení typu rozhraní, pokud je typ rozhraní.  
  
### <a name="generic-parameter-attributes"></a>Obecný parametr atributy  
 <xref:System.Type.GenericParameterAttributes%2A> Příkazy property Get <xref:System.Reflection.GenericParameterAttributes> hodnotu, která určuje rozptyl (kovariance a kontravariance) a zvláštní omezení parametru typu.  
  
#### <a name="covariance-and-contravariance"></a>Kovariance a kontravariance  
 Chcete-li zjistit, zda je parametr typu kovariantní nebo kontravariantní, použijte <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> maskování na <xref:System.Reflection.GenericParameterAttributes> hodnotu, která je vrácena <xref:System.Type.GenericParameterAttributes%2A> vlastnost. Pokud je výsledkem <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, parametr typu je neutrální. Zobrazit [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Zvláštní omezení  
 Chcete-li určit zvláštní omezení parametru typu, použijte <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> k maskování <xref:System.Reflection.GenericParameterAttributes> hodnotu, která je vrácena <xref:System.Type.GenericParameterAttributes%2A> vlastnost. Pokud je výsledkem <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, neexistují žádné zvláštní omezení. Parametr typu mohou být omezeny na odkaz na typ, typ hodnotu Null a mít výchozí konstruktor.  
  
 [Zpět na začátek](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>Výstupních podmínek  
 Tabulka obsahující neutrálních podmínek pro běžné výrazy v reflexi pro obecné typy, najdete v části <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Další podmínky týkající se obecné metody, naleznete v tématu <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Prozkoumání a vytvoření instancí obecných typů pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|Ukazuje, jak používat vlastnosti a metody <xref:System.Type> a <xref:System.Reflection.MethodInfo> prozkoumat obecných typů.|  
|[Obecné typy](../../../docs/standard/generics/index.md)|Popisuje funkci obecných typů a jak je podporován v rozhraní .NET Framework.|  
|[Postupy: Definování obecného typu pomocí reflexe generování](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Ukazuje, jak pomocí odrazu generování ke generování obecné typy v dynamickém sestavení.|  
|[Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Popisuje <xref:System.Type> třídy a poskytuje příklady kódu, které ukazují, jak používat <xref:System.Type> s různými třídami reflexe k získání informací o konstruktory, metody, pole, vlastnosti a události.|
