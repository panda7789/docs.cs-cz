---
title: "Reflexe a obecné typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 99d8da622b23a98b8a48ad6fcdb82c270d24ed22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="reflection-and-generic-types"></a>Reflexe a obecné typy
<a name="top"></a>Z hlediska reflexe, rozdíl mezi obecného typu a typ obyčejnou je, že obecného typu má přidruženo sadu parametrů typů (je-li definice obecného typu) nebo zadejte argumenty (Pokud je vytvořený typ). Obecná metoda se liší od metody obyčejnou stejným způsobem.  
  
 Existují dva klíče k pochopení, jak reflexe zpracovává obecné typy a metody:  
  
-   Parametry typu definice obecného typu a definice obecné metody jsou reprezentované pomocí instance <xref:System.Type> třídy.  
  
    > [!NOTE]
    >  Mnoho vlastností a metod <xref:System.Type> mají různé chování při <xref:System.Type> objekt představuje parametr obecného typu. Tyto rozdíly jsou popsané v tématech vlastnosti a metody. Například v tématu <xref:System.Type.IsAutoClass%2A> a <xref:System.Type.DeclaringType%2A>. Kromě toho někteří členové jsou platné pouze tehdy, když <xref:System.Type> objekt představuje parametr obecného typu. Například v tématu <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
-   Pokud instance <xref:System.Type> představuje obecného typu, pak obsahuje pole typů, které představují parametry typu (pro definice obecného typu) nebo argumenty typu (pro sestavené typy). Totéž platí instance <xref:System.Reflection.MethodInfo> třídu, která představuje obecné metody.  
  
 Poskytuje metody reflexe <xref:System.Type> a <xref:System.Reflection.MethodInfo> máte přístup k poli parametrů typu a určení, zda instanci <xref:System.Type> představuje parametr typu nebo skutečným typem.  
  
 Například kód ukázka metody popsané v tomto poli, najdete v části [postup: Zkontrolujte a vytvořit instance obecných typů pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Následující diskusi předpokládá znalost terminologie obecných typů, jako je rozdíl mezi typ parametry a argumenty a otevřené nebo zavřené sestavené typy. Další informace najdete v tématu [obecné typy](../../../docs/standard/generics/index.md).  
  
 Tento přehled se skládá z následujících částí:  
  
-   [Obecný typ nebo metoda, je to?](#is_this_a_generic_type_or_method)  
  
-   [Generování uzavřené obecné typy](#generating_closed_generic_types)  
  
-   [Zkoumání argumenty Typ a parametry typu](#examining_type_arguments)  
  
-   [Výstupních podmínek](#invariants)  
  
-   [Související témata](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>Obecný typ nebo metoda, je to?  
 Při použití reflexe prozkoumat neznámého typu, reprezentována instanci <xref:System.Type>, použijte <xref:System.Type.IsGenericType%2A> vlastnosti k určení, zda je neznámý typ Obecné. Vrátí `true` Pokud typ je obecná. Podobně když zkontrolujte Neznámá metoda, reprezentována instanci <xref:System.Reflection.MethodInfo> třídy, použijte <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> vlastnosti k určení, zda je obecná metoda.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Obecný typ nebo metoda definice, je to?  
 Použít <xref:System.Type.IsGenericTypeDefinition%2A> vlastnosti k určení zda <xref:System.Type> objekt představuje obecného typu definice a používání <xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A> metoda k určení zda <xref:System.Reflection.MethodInfo> představuje definici obecná metoda.  
  
 Obecné metody a typu definice jsou šablony, ze kterých instantiable typy jsou vytvořeny. Obecné typy v knihovně tříd rozhraní .NET Framework, jako <xref:System.Collections.Generic.Dictionary%602>, jsou definice obecného typu.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Typ nebo metoda otevřené nebo zavřené?  
 Obecný typ nebo metoda je zavřený, pokud byla nahrazena instantiable typy pro všechny její parametry typu, včetně všech parametrů typu všech nadřazených typů. Instance obecného typu můžete vytvořit, pouze pokud je uzavřený. <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Vlastnost vrátí `true` Pokud typ je otevřený. Pro metody <xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A?displayProperty=nameWithType> metoda provádí stejnou funkci.  
  
 [Zpět na začátek](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>Generování uzavřené obecné typy  
 Jakmile máte na obecný typ nebo metoda definice, použijte <xref:System.Type.MakeGenericType%2A> metodu pro vytvoření uzavřené obecného typu nebo <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> metodu pro vytvoření <xref:System.Reflection.MethodInfo> pro uzavřená obecná metoda.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Získávání obecného typu nebo definice – metoda  
 Pokud máte otevřený obecný typ nebo metoda, která není obecný typ nebo metoda definice, nelze vytvořit její instance a není možné zadat parametry typu, které chybí. Musí mít obecný typ nebo metoda definice. Použití <xref:System.Type.GetGenericTypeDefinition%2A> metoda získat definice obecného typu nebo <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> metoda získat definici obecná metoda.  
  
 Pokud máte například <xref:System.Type> objekt reprezentující `Dictionary<int, string>` (`Dictionary(Of Integer, String)` v jazyce Visual Basic) a chcete vytvořit typ `Dictionary<string, MyClass>`, můžete použít <xref:System.Type.GetGenericTypeDefinition%2A> metodu za účelem získání <xref:System.Type> představující `Dictionary<TKey, TValue>` a potom pomocí <xref:System.Type.MakeGenericType%2A> metoda k vytvoření <xref:System.Type> představující `Dictionary<int, MyClass>`.  
  
 Příklad otevřete obecného typu, který není obecného typu naleznete v části "Parametr typu nebo Argument typu" dál v tomto tématu.  
  
 [Zpět na začátek](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>Zkoumání argumenty Typ a parametry typu  
 Použít <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> metoda získat pole <xref:System.Type> objekty, které představují parametry typu nebo typ argumenty obecného typu a použít <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> metoda provedete stejný pro obecné metody.  
  
 Jakmile víte, že <xref:System.Type> představuje parametr typu objektu, existuje mnoho další otázky reflexe dokáže odpovědět. Můžete určit zdrojový parametr typu, jeho pozice a jeho omezení.  
  
### <a name="type-parameter-or-type-argument"></a>Argument typu nebo parametr typu  
 K určení, zda je parametr typu nebo typ argument konkrétní element pole, použijte <xref:System.Type.IsGenericParameter%2A> vlastnost. <xref:System.Type.IsGenericParameter%2A> Vlastnost je `true` Pokud se element nachází parametr typu.  
  
 Obecný typ může být otevřete, aniž by musel být definice obecného typu, v takovém případě má směs typu argumentů a parametrů typu. Například v následujícím kódu třídy `D` je odvozen z typu vytvořené nahraďte první parametr typu `D` pro druhý parametr typu `B`.  
  
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
  
 Pokud získáte <xref:System.Type> objekt reprezentující `D<V, W>` a použít <xref:System.Type.BaseType%2A> vlastnost k získání jeho základní typ, výsledná `type B<int, V>` je otevřená, ale není definice obecného typu.  
  
### <a name="source-of-a-generic-parameter"></a>Zdroj obecný parametr  
 Parametr obecného typu může pocházet z typu, který je zkoumán, z vnějšího typu nebo z obecné metody. Můžete určit zdroj parametr obecného typu následujícím způsobem:  
  
-   Nejprve pomocí <xref:System.Type.DeclaringMethod%2A> vlastnosti k určení, zda parametr typu pochází z obecná metoda. Pokud hodnota vlastnosti není odkaz s hodnotou null (`Nothing` v jazyce Visual Basic), pak zdroj je obecná metoda.  
  
-   Pokud zdroj není obecná metoda, použijte <xref:System.Type.DeclaringType%2A> patří vlastnosti k určení obecného typu parametr obecného typu.  
  
 Pokud parametr typu patří do obecné metody <xref:System.Type.DeclaringType%2A> vlastnost vrací typ, který deklarovaný obecná metoda, která je důležité.  
  
### <a name="position-of-a-generic-parameter"></a>Pozice obecný parametr  
 Ve výjimečných případech je potřeba určit umístění parametr typu v seznamu parametrů typu jeho deklarující třídy. Předpokládejme například, že máte <xref:System.Type> objekt reprezentující `B<int, V>` typ z předchozího příkladu. <xref:System.Type.GetGenericArguments%2A> Metoda vám poskytne seznam argumentů typu a při kontrole `V` můžete použít <xref:System.Type.DeclaringMethod%2A> a <xref:System.Type.DeclaringType%2A> vlastnosti, které chcete zjistit, které pocházejí z. Pak můžete použít <xref:System.Type.GenericParameterPosition%2A> vlastnosti k určení pozici v seznamu parametrů typu kterých byla definována. V tomto příkladu `V` je na pozici 0 (nula) v seznamu Typ parametru, kde byl definován.  
  
### <a name="base-type-and-interface-constraints"></a>Základní typ a omezení rozhraní  
 Použití <xref:System.Type.GetGenericParameterConstraints%2A> metoda získat základní typ omezení a rozhraní omezení typu parametru. Pořadí prvků pole není důležité. Element reprezentuje omezení rozhraní, pokud je typ rozhraní.  
  
### <a name="generic-parameter-attributes"></a>Obecný parametr atributy  
 <xref:System.Type.GenericParameterAttributes%2A> Získá vlastnost <xref:System.Reflection.GenericParameterAttributes> hodnotu, která určuje odchylku (kovariance a kontravariance) a speciální omezení typu parametru.  
  
#### <a name="covariance-and-contravariance"></a>Kovariance a kontravariance  
 Pokud chcete zjistit, jestli se parametr typu je kovariant nebo kontravariant, použít <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> maskování na <xref:System.Reflection.GenericParameterAttributes> hodnotu, která je vrácený <xref:System.Type.GenericParameterAttributes%2A> vlastnost. Pokud je výsledek <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, parametr typu je neutrální. V tématu [kovariance a kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Zvláštní omezení  
 K určení speciálních omezení parametr typu, použít <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> maskování na <xref:System.Reflection.GenericParameterAttributes> hodnotu, která je vrácený <xref:System.Type.GenericParameterAttributes%2A> vlastnost. Pokud je výsledek <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, neexistují žádné zvláštní omezení. Parametr typu může být omezené být odkazového typu, musí být typu hodnot neumožňující hodnotu Null a mít výchozí konstruktor.  
  
 [Zpět na začátek](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>Výstupních podmínek  
 Tabulku invariantní podmínky pro běžné podmínky v reflexe pro obecné typy, najdete v části <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Další podmínky týkající se obecné metody, najdete v části <xref:System.Reflection.MethodInfo.IsGenericMethod%2A?displayProperty=nameWithType>.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: prozkoumání a vytvoření instancí obecných typů pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|Ukazuje, jak pomocí vlastnosti a metody <xref:System.Type> a <xref:System.Reflection.MethodInfo> prozkoumat obecné typy.|  
|[Obecné typy](../../../docs/standard/generics/index.md)|Popisuje funkce obecných typů a jak je podporována v rozhraní .NET Framework.|  
|[Postupy: definování obecného typu pomocí reflexe emitování](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Ukazuje, jak pomocí reflexe emitování ke generování obecné typy v dynamických sestavení.|  
|[Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Popisuje <xref:System.Type> třídy a poskytuje příklady kódu, které ukazují, jak používat <xref:System.Type> s různými třídami reflexe ke získání informací o konstruktory, metody, pole, vlastnosti a události.|
