---
title: Kovariance a kontravariance v obecných typech
description: Přečtěte si o kovarianci, která umožňuje použít více odvozený typ a kontravariance, což umožňuje použít méně odvozený typ v obecných typech .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics, covariance and contravariance
- generics, variance
- covariance and contravariance in generics
- generic type parameters
ms.assetid: 2678dc63-c7f9-4590-9ddc-0a4df684d42e
ms.openlocfilehash: 12de1554bb6e33b69d0d2bba24001e7e4c2d8a65
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663041"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kovariance a kontravariance v obecných typech
Kovariance a kontravariance jsou výrazy, které odkazují na schopnost použít více odvozeného typu (konkrétnější) nebo méně odvozený typ (méně specifické), než bylo původně určeno. Parametry obecného typu podporují kovarianci a kontravarianci za účelem zvýšení flexibility při přiřazování a používání obecných typů. Pokud hovoříme o typu systému, pak jsou pojmy kovariance, kontravariance a invariance definovány následovně: Příklady předpokládají základní třídu s názvem `Base` a odvozenou třídu s názvem `Derived` .  
  
- `Covariance`  
  
     Umožňuje použít více odvozený typ, než byl původně zadán.  
  
     Můžete přiřadit instanci `IEnumerable<Derived>` ( `IEnumerable(Of Derived)` v Visual Basic) proměnné typu `IEnumerable<Base>` .  
  
- `Contravariance`  
  
     Umožňuje používat obecnější (méně odvozený) typ, než byl původně zadán.  
  
     Můžete přiřadit instanci `Action<Base>` ( `Action(Of Base)` v Visual Basic) proměnné typu `Action<Derived>` .  
  
- `Invariance`  
  
     To znamená, že můžete použít pouze původně zadaný typ; parametr invariantního obecného typu není ani kovariantní, ani kontravariantní.  
  
     Instanci `List<Base>` (v Visual Basic) nemůžete přiřadit `List(Of Base)` proměnné typu `List<Derived>` nebo naopak.  
  
 Parametry kovariantního typu umožňují provádět přiřazení, která vypadají podobně jako obyčejné [polymorfismus](../../csharp/programming-guide/classes-and-structs/polymorphism.md), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601>Třída implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní, takže `List<Derived>` ( `List(Of Derived)` v Visual Basic) implementuje `IEnumerable<Derived>` . Parametr kovariantního typu dokončí zbývající úkoly.  
  
 Kontravariance se naopak zdá být neintuitivní. Následující příklad vytvoří delegát typu `Action<Base>` ( `Action(Of Base)` v Visual Basic) a potom přiřadí tento delegát k proměnné typu `Action<Derived>` .  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Zdá se, že se jedná o zpětnou akci, jde však o typově bezpečný kód, který se zkompiluje a spustí. Výraz lambda odpovídá delegátovi, ke kterému je přiřazen, takže definuje metodu, která přijímá jeden parametr typu `Base` a který nemá žádnou návratovou hodnotu. Výsledný delegát může být přiřazen proměnné typu, `Action<Derived>` protože parametr typu `T` <xref:System.Action%601> delegáta je kontravariantní. Kód je typově bezpečný, protože `T` Určuje typ parametru. Když `Action<Base>` je vyvolán delegát typu, jako by byl delegátem typu `Action<Derived>` , musí být jeho argument typu `Derived` . Tento argument lze vždy bezpečně předat základní metodě, protože parametr metody je typu `Base` .  
  
 Obecně lze parametr konvariantního typu použít jako návratový typ delegátu a parametry kontravariantního typu mohou být použity jako typy parametrů. V případě konkrétního rozhraní mohou být parametry kovariantního typu použity jako návratové typy metod rozhraní a parametry kontravariantního typu mohou být použity jako typy parametrů metod rozhraní.  
  
 Kovariance a kontravariance jsou souhrnně označovány jako *Variance*. Parametr obecného typu, který není označen jako kovariantní nebo kontravariantní, se označuje jako *invariantní*. Stručný souhrn faktů o varianci v modulu CLR (Common Language Runtime):  
  
- V .NET Framework 4 jsou parametry typu variant omezené na obecné rozhraní a obecné typy delegátů.  
  
- Obecná rozhraní nebo obecné typy delegátů mohou mít parametry kovariantního i kontravariantního typu.  
  
- Variance platí pouze pro odkazované typy. Pokud zadáte typ hodnoty pro parametr variantního typu, je tento parametr typu pro výsledný konstruovaný typ invariantní.  
  
- Variance se nevztahuje na kombinaci delegátů. To znamená, že dané dva Delegáti typů `Action<Derived>` a `Action<Base>` ( `Action(Of Derived)` a `Action(Of Base)` v Visual Basic) nelze kombinovat druhý delegát s prvním, přestože výsledek by byl typově bezpečný. Variance umožňuje přiřazení druhého delegáta proměnné typu `Action<Derived>` , ale delegáti mohou být kombinováni pouze v případě, že se jejich typy shodují přesně.

<a name="InterfaceCovariantTypeParameters"></a>
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Obecná rozhraní s parametry kovariantního typu  
 Počínaje .NET Framework 4 mají několik obecných rozhraní parametry kovariantního typu. například: <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.Generic.IEnumerator%601> , a <xref:System.Linq.IQueryable%601> <xref:System.Linq.IGrouping%602> . Všechny parametry typu těchto rozhraní jsou kovariantní. Parametry typu se tedy používají pouze pro návratové typy členů.  
  
 Následující příklad znázorňuje parametry kovariantního typu. Příklad definuje dva typy: `Base` má statickou metodu s názvem `PrintBases` , která přijímá `IEnumerable<Base>` ( `IEnumerable(Of Base)` v Visual Basic) a tiskne prvky. `Derived`dědí z `Base` . Příklad vytvoří prázdnou hodnotu `List<Derived>` ( `List(Of Derived)` v Visual Basic) a ukazuje, že tento typ lze předat `PrintBases` a přiřadit proměnné typu `IEnumerable<Base>` bez přetypování. <xref:System.Collections.Generic.List%601>implementuje <xref:System.Collections.Generic.IEnumerable%601> , který má jeden parametr kovariantního typu. Parametr kovariantního typu je důvodem, proč `IEnumerable<Derived>` lze instanci použít místo `IEnumerable<Base>` .  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Obecná rozhraní s parametry obecného kontravariantního typu  
 Počínaje .NET Framework 4 má několik obecných rozhraní parametry kontravariantního typu; například: <xref:System.Collections.Generic.IComparer%601> , <xref:System.IComparable%601> , a <xref:System.Collections.Generic.IEqualityComparer%601> . Tato rozhraní mají pouze parametry kontravariantního typu, takže parametry typu slouží pouze jako typy parametrů u členů rozhraní.  
  
 Následující příklad znázorňuje parametry kontravariantního typu. Příklad definuje abstraktní `MustInherit` třídu (v Visual Basic) `Shape` s `Area` vlastností. V příkladu je také definována `ShapeAreaComparer` třída, která implementuje `IComparer<Shape>` ( `IComparer(Of Shape)` v Visual Basic). Implementace <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> metody je založena na hodnotě `Area` vlastnosti, takže `ShapeAreaComparer` ji lze použít k řazení `Shape` objektů podle oblasti.  
  
 `Circle`Třída dědí `Shape` a Přepisuje `Area` . Příklad vytvoří objekt s <xref:System.Collections.Generic.SortedSet%601> `Circle` použitím konstruktoru, který přebírá `IComparer<Circle>` ( `IComparer(Of Circle)` v Visual Basic). Nicméně namísto předání `IComparer<Circle>` a, tento příklad předá `ShapeAreaComparer` objekt, který implementuje `IComparer<Shape>` . Příklad může předat porovnávací hodnotu méně odvozeného typu ( `Shape` ), pokud kód volá porovnávací metodu více odvozeného typu ( `Circle` ), protože parametr typu <xref:System.Collections.Generic.IComparer%601> obecného rozhraní je kontravariantní.  
  
 Při přidání nového `Circle` objektu do je `SortedSet<Circle>` `IComparer<Shape>.Compare` volána metoda ( `IComparer(Of Shape).Compare` metoda v Visual Basic) `ShapeAreaComparer` objektu pokaždé, když je nový prvek porovnán s existujícím prvkem. Typ parametru metody ( `Shape` ) je méně odvozený od typu, který se předává ( `Circle` ), takže volání je typově bezpečné. Kontravariance umožňuje `ShapeAreaComparer` Řadit kolekci libovolného typu a také smíšenou kolekci typů, které jsou odvozeny z `Shape` .  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  

## <a name="generic-delegates-with-variant-type-parameters"></a>Obecné delegáty s parametry variantního typu  
 V .NET Framework 4 `Func` mají Obecné delegáty, jako například <xref:System.Func%602> , obsahovat kovariantní návratové typy a kontravariantní typy parametrů. `Action`Obecní delegáti, například <xref:System.Action%602> , mají kontravariantní typy parametrů. To znamená, že delegáty lze přiřadit proměnným, které mají více odvozené typy parametrů a (v případě `Func` generických delegátů) méně odvozené návratové typy.  
  
> [!NOTE]
> Poslední parametr obecného typu `Func` generických delegátů určuje typ návratové hodnoty v signatuře delegáta. Je kovariantní ( `out` klíčové slovo), zatímco ostatní parametry obecného typu jsou kontravariantní ( `in` klíčové slovo).  
  
 Následující kód to znázorňuje. První část kódu definuje třídu s názvem `Base` , třídu s názvem `Derived` , která dědí `Base` , a jinou třídu s `static` metodou ( `Shared` v Visual Basic) s názvem `MyMethod` . Metoda převezme instanci `Base` a vrátí instanci `Derived` . (Pokud je argumentem instance `Derived` , `MyMethod` vrátí jej. Pokud je argumentem instance `Base` , `MyMethod` vrátí novou instanci `Derived` .) V `Main()` je v příkladu vytvořena instance `Func<Base, Derived>` ( `Func(Of Base, Derived)` v Visual Basic), která představuje `MyMethod` a ukládá ji do proměnné `f1` .  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Druhá část kódu ukazuje, že delegát může být přiřazen proměnné typu `Func<Base, Base>` ( `Func(Of Base, Base)` v Visual Basic), protože návratový typ je kovariantní.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Třetí část kódu ukazuje, že delegát může být přiřazen proměnné typu `Func<Derived, Derived>` ( `Func(Of Derived, Derived)` v Visual Basic), protože typ parametru je kontravariantní.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Poslední část kódu ukazuje, že delegát může být přiřazen proměnné typu `Func<Derived, Base>` ( `Func(Of Derived, Base)` v Visual Basic), kombinování účinků kontravariantního typu parametru a kovariantního návratového typu.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Variance obecných a neobecných delegátů  
 V předchozím kódu signatura `MyMethod` přesně odpovídá signatuře vytvořeného obecného delegáta: `Func<Base, Derived>` ( `Func(Of Base, Derived)` v Visual Basic). Příklad ukazuje, že tento obecný delegát může být uložen v proměnných nebo parametrech metody, které mají více odvozené typy parametrů a méně odvozené návratové typy, pokud jsou všechny typy delegátů vyrobeny z obecného typu delegáta <xref:System.Func%602> .  
  
 Jedná se o důležitý fakt. Účinky kovariance a kontravariance v parametrech typu generických delegátů jsou podobné vlivům kovariance a kontravariance v normální vazbě delegátů (viz [Variance v delegátech (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [Variance v delegátech (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)). Variance ve vazbě delegátu však funguje se všemi typy delegátů, nejen s obecnými typy delegátu, které mají parametry variantního typu. Variance ve vazbách delegátů navíc umožňuje metodě vázat se na jakýkoli delegát, který má více omezující parametry typu a méně omezující návratový typ, zatímco přiřazení obecných delegátů funguje pouze v případě, že oba typy delegátů jsou konstruovány ze stejné definice obecného typu.  
  
 Následující příklad znázorňuje kombinované účinky variance ve vazbě delegátu a variance u parametrů obecného typu. Příklad definuje hierarchii typu, která obsahuje tři typy, od nejméně odvozeného ( `Type1` ) po nejvíce odvozené ( `Type3` ). Variance v běžných vazbách delegátů se používá k navázání metody s typem parametru `Type1` a návratovým typem `Type3` do obecného delegáta s typem parametru `Type2` a návratovým typem `Type2` . Výsledný obecný delegát je poté přiřazen jiné proměnné, jejíž typ obecného delegáta má parametr typu `Type3` a návratový typ `Type1` , s použitím kovariance a kontravariance parametrů obecného typu. Druhé přiřazení vyžaduje, aby typ proměnné i typ delegáta byly sestaveny ze stejné definice obecného typu, v tomto případě <xref:System.Func%602> .  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  

## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definování variantních obecných rozhraní a delegátů
 Počínaje .NET Framework 4 mají Visual Basic a C# klíčová slova, která umožňují označit parametry obecného typu rozhraní a delegátů jako kovariantní nebo kontravariantní.  
  
> [!NOTE]
> Počínaje verzí 2.0 rozhraní .NET Framework podporuje modul CLR (Common Language Runtime) anotace variance v parametrech obecného typu. Před .NET Framework 4 je jediným způsobem, jak definovat obecnou třídu, která má tyto poznámky, použít jazyk MSIL (Microsoft Intermediate Language), a to buď zkompilováním třídy s [Ilasm.exe (IL Assembler)](../../framework/tools/ilasm-exe-il-assembler.md) , nebo vygenerováním v dynamickém sestavení.  
  
 Parametr kovariantního typu je označený `out` klíčovým slovem ( `Out` klíčové slovo v Visual Basic `+` pro [Assembler MSIL](../../framework/tools/ilasm-exe-il-assembler.md)). Parametr kovariantního typu můžete použít jako návratovou hodnotu metody, která patří do rozhraní, nebo jako návratový typ delegátu. Typ kovariantního parametru nelze použít jako omezení obecného typu pro metody rozhraní.  
  
> [!NOTE]
> Pokud má metoda rozhraní parametr, který je typem obecného delegátu, může parametr kovariantního typu pro typ rozhraní být použit pro zadání parametru kontravariantního typu pro typ delegátu.  
  
 Parametr kontravariantního typu je označen `in` klíčovým slovem ( `In` klíčové slovo v Visual Basic `-` pro [Assembler MSIL](../../framework/tools/ilasm-exe-il-assembler.md)). Parametr kontravariantního typu můžete použít jako typ parametru metody, která patří do rozhraní, nebo jako typ parametru delegátu. Parametr kontravariantního typu lze použít jako omezení obecného typu pro metodu rozhraní.  
  
 Pouze typy rozhraní a typy delegátů mohou mít parametry variantního typu. Typy rozhraní nebo delegátů mohou mít parametry kovariantního i kontravariantního typu.  
  
 Jazyky Visual Basic a C# neumožňují porušení pravidel pro použití parametrů kovariantního a kontravariantního typu nebo přidání anotací kovariance a kontravariance parametrům typu pro jiné typy, než jsou typy rozhraní a delegátů. Rozhraní [MSIL Assembler](../../framework/tools/ilasm-exe-il-assembler.md) neprovede takové kontroly, ale <xref:System.TypeLoadException> je vyvolána, pokud se pokusíte načíst typ, který v rozporu s pravidly.  
  
 Informace a příklad kódu naleznete v tématu [Variance in Generic Interfaces (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [Variance in generic Interfaces (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  

## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Seznam variantních obecných typů rozhraní a delegátů
 V .NET Framework 4 mají následující typy rozhraní a delegátů parametry kovariantního nebo kontravariantního typu.  
  
|Typ|Parametry kovariantního typu|Parametry kontravariantního typu|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601>schopn<xref:System.Action%6016>||Ano|  
|<xref:System.Comparison%601>||Ano|  
|<xref:System.Converter%602>|Ano|Ano|  
|<xref:System.Func%601>|Ano||  
|<xref:System.Func%602>schopn<xref:System.Func%6017>|Ano|Ano|  
|<xref:System.IComparable%601>||Ano|  
|<xref:System.Predicate%601>||Ano|  
|<xref:System.Collections.Generic.IComparer%601>||Ano|  
|<xref:System.Collections.Generic.IEnumerable%601>|Ano||  
|<xref:System.Collections.Generic.IEnumerator%601>|Ano||  
|<xref:System.Collections.Generic.IEqualityComparer%601>||Ano|  
|<xref:System.Linq.IGrouping%602>|Ano||  
|<xref:System.Linq.IOrderedEnumerable%601>|Ano||  
|<xref:System.Linq.IOrderedQueryable%601>|Ano||  
|<xref:System.Linq.IQueryable%601>|Ano||  
  
## <a name="see-also"></a>Viz také

- [Kovariance a kontravariance (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kovariance a kontravariance (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Variance v delegátech (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Variance v delegátech (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
