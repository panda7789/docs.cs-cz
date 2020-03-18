---
title: Kovariance a kontravariance v obecných typech
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
ms.openlocfilehash: 909b03588d2a41f667bfa117a5cecb420b125088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708394"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kovariance a kontravariance v obecných typech
Kovariance a contravariance jsou termíny, které odkazují na schopnost používat více odvozený typ (konkrétnější) nebo méně odvozený typ (méně specifický) než původně zadaný. Parametry obecného typu podporují kovarianci a kontravarianci za účelem zvýšení flexibility při přiřazování a používání obecných typů. Pokud hovoříme o typu systému, pak jsou pojmy kovariance, kontravariance a invariance definovány následovně: Příklady předpokládají základní třídu s názvem `Base` `Derived`a odvozenou třídu s názvem .  
  
- `Covariance`  
  
     Umožňuje použít více odvozeného typu, než bylo původně zadáno.  
  
     Můžete přiřadit `IEnumerable<Derived>` instanci`IEnumerable(Of Derived)` ( v jazyce Visual `IEnumerable<Base>`Basic) proměnné typu .  
  
- `Contravariance`  
  
     Umožňuje používat obecnější (méně odvozený) typ, než byl původně zadán.  
  
     Můžete přiřadit `Action<Base>` instanci`Action(Of Base)` ( v jazyce Visual `Action<Derived>`Basic) proměnné typu .  
  
- `Invariance`  
  
     To znamená, že můžete použít pouze původně zadaný typ; parametr invariantního obecného typu není ani kovariantní, ani kontravariantní.  
  
     Nelze přiřadit `List<Base>` instanci`List(Of Base)` ( v jazyce Visual `List<Derived>` Basic) proměnné typu nebo naopak.  
  
 Parametry kovariantního typu umožňují provádět přiřazení, která vypadají podobně jako běžný [polymorfismus](../../csharp/programming-guide/classes-and-structs/polymorphism.md), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 Třída <xref:System.Collections.Generic.List%601> implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní, `List<Derived>` `List(Of Derived)` tak ( v `IEnumerable<Derived>`jazyce Visual Basic) implementuje . Parametr kovariantního typu dokončí zbývající úkoly.  
  
 Kontravariance se naopak zdá být neintuitivní. Následující příklad vytvoří delegáta `Action<Base>` `Action(Of Base)` typu ( v jazyce Visual Basic) a `Action<Derived>`potom přiřadí tohoto delegáta proměnné typu .  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Zdá se, že se jedná o zpětnou akci, jde však o typově bezpečný kód, který se zkompiluje a spustí. Výraz lambda odpovídá delegátovi, kterému je přiřazen, takže definuje metodu, která přebírá jeden parametr typu `Base` a která nemá žádnou vrácenou hodnotu. Výsledný delegát může být přiřazen proměnné `Action<Derived>` typu, protože `T` parametr <xref:System.Action%601> typu delegáta je kontravariantní. Kód je typově `T` bezpečný, protože určuje typ parametru. Pokud je delegát `Action<Base>` typu vyvolán, jako by byl `Action<Derived>`delegátem typu , `Derived`musí být jeho argument typu . Tento argument lze vždy bezpečně předat základní metodě, protože parametr `Base`metody je typu .  
  
 Obecně lze parametr konvariantního typu použít jako návratový typ delegátu a parametry kontravariantního typu mohou být použity jako typy parametrů. V případě konkrétního rozhraní mohou být parametry kovariantního typu použity jako návratové typy metod rozhraní a parametry kontravariantního typu mohou být použity jako typy parametrů metod rozhraní.  
  
 Kovariance a kontravariance se souhrnně označují jako *rozptyl*. Parametr obecného typu, který není označen jako kovariantní nebo kontravariantní, se označuje jako *invariantní*. Stručný souhrn faktů o varianci v modulu CLR (Common Language Runtime):  
  
- V rozhraní .NET Framework 4 jsou parametry typu variantomezeny na obecné rozhraní a obecné typy delegátů.  
  
- Obecná rozhraní nebo obecné typy delegátů mohou mít parametry kovariantního i kontravariantního typu.  
  
- Variance platí pouze pro odkazované typy. Pokud zadáte typ hodnoty pro parametr variantního typu, je tento parametr typu pro výsledný konstruovaný typ invariantní.  
  
- Variance se nevztahuje na kombinaci delegátů. To znamená, že vzhledem `Action<Base>` `Action(Of Derived)` k `Action(Of Base)` tomu, dva delegáti typů `Action<Derived>` a ( a v jazyce Visual Basic), nelze kombinovat druhý delegát s prvním i když výsledek by byl typ bezpečný. Odchylka umožňuje druhému delegátovi přiřadit proměnnou typu `Action<Derived>`, ale delegáti mohou kombinovat pouze v případě, že jejich typy přesně odpovídají.

<a name="InterfaceCovariantTypeParameters"></a>
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Obecná rozhraní s parametry kovariantního typu  
 Počínaje rozhraním .NET Framework 4 má několik obecných rozhraní parametry kovariantního typu. například: <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, <xref:System.Linq.IGrouping%602>a . Všechny parametry typu těchto rozhraní jsou kovariantní. Parametry typu se tedy používají pouze pro návratové typy členů.  
  
 Následující příklad znázorňuje parametry kovariantního typu. Příklad definuje dva `Base` typy: má statickou metodu s názvem, `PrintBases` která trvá `IEnumerable<Base>` (`IEnumerable(Of Base)` v jazyce Visual Basic) a vytiskne prvky. `Derived`dědí `Base`od . Příklad vytvoří empty `List<Derived>` `List(Of Derived)` ( v jazyce Visual Basic) a `PrintBases` ukazuje, že tento `IEnumerable<Base>` typ může být předán a přiřazen k proměnné typu bez přetypování. <xref:System.Collections.Generic.List%601>implementuje <xref:System.Collections.Generic.IEnumerable%601>, který má jeden parametr kovariantního typu. Parametr covariant type je důvodem, `IEnumerable<Derived>` proč lze `IEnumerable<Base>`místo .  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Obecná rozhraní s parametry obecného kontravariantního typu  
 Počínaje rozhraním .NET Framework 4 má několik obecných rozhraní parametry typu contravariant; například: <xref:System.Collections.Generic.IComparer%601> <xref:System.IComparable%601>, <xref:System.Collections.Generic.IEqualityComparer%601>a . Tato rozhraní mají pouze parametry kontravariantního typu, takže parametry typu slouží pouze jako typy parametrů u členů rozhraní.  
  
 Následující příklad znázorňuje parametry kontravariantního typu. Příklad definuje abstraktní (`MustInherit` v jazyce Visual Basic) `Shape` třídy s vlastností. `Area` Příklad také definuje `ShapeAreaComparer` třídu, `IComparer<Shape>` která`IComparer(Of Shape)` implementuje (v jazyce Visual Basic). Implementace <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> metody je založena na hodnotě `Area` vlastnosti, takže `ShapeAreaComparer` lze `Shape` použít k řazení objektů podle oblasti.  
  
 Třída `Circle` dědí `Shape` a `Area`přepíše . Příklad vytvoří <xref:System.Collections.Generic.SortedSet%601> a `Circle` objekty, pomocí konstruktoru, který trvá `IComparer<Circle>` (`IComparer(Of Circle)` v jazyce Visual Basic). Však namísto `IComparer<Circle>`předání , příklad `ShapeAreaComparer` předá objekt, který implementuje `IComparer<Shape>`. Příklad může předat porovnávač méně odvozeného typu (`Shape`), když kód volá porovnávač odvozenějšího typu (`Circle`), protože parametr typu <xref:System.Collections.Generic.IComparer%601> obecného rozhraní je kontravariantní.  
  
 Při přidání `Circle` nového objektu `SortedSet<Circle>` `IComparer<Shape>.Compare` do`IComparer(Of Shape).Compare` , metoda (metoda `ShapeAreaComparer` v jazyce Visual Basic) objektu je volána při každém porovnání nového prvku s existujícím prvkem. Typ parametru metody`Shape`( ) je méně odvozen než typ, který je předáván (`Circle`), takže volání je typově bezpečné. Contravariance `ShapeAreaComparer` umožňuje seřadit kolekci libovolného typu, stejně jako smíšené `Shape`kolekce typů, které jsou odvozeny z .  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  

## <a name="generic-delegates-with-variant-type-parameters"></a>Obecné delegáty s parametry variantního typu  
 V rozhraní .NET Framework `Func` 4 mají <xref:System.Func%602>obecné delegáty, například , kovariantní návratové typy a typy parametrů contravariant. Obecné `Action` delegáty, <xref:System.Action%602>například , mají typy parametrů contravariant. To znamená, že delegáti mohou být přiřazeny proměnné, které mají více `Func` odvozené typy parametrů a (v případě obecných delegátů) méně odvozené návratové typy.  
  
> [!NOTE]
> Poslední obecný typ parametr `Func` u obecných delegátů určuje typ vrácené hodnoty v podpisu delegáta. Je kovariantní`out` ( klíčové slovo), zatímco ostatní parametry`in` generického typu jsou kontravariantní ( klíčové slovo).  
  
 Následující kód to znázorňuje. První část kódu definuje třídu `Base`s názvem `Derived` , `Base`třídu s názvem, která dědí , a jinou třídu `static` s metodou (v`Shared` jazyce Visual Basic) s názvem `MyMethod`. Metoda přebírá instanci `Base` a vrátí `Derived`instanci . (Pokud je argument instancí `Derived`třídy , `MyMethod` vrátí jej; pokud je argument instancí aplikace `Base`, `MyMethod` vrátí novou instanci `Derived`.) V `Main()`aplikaci example vytvoří `Func<Base, Derived>` `Func(Of Base, Derived)` instanci ( `MyMethod`instanci v jazyce Visual Basic , která představuje a uloží ji do proměnné `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Druhá část kódu ukazuje, že delegát může být `Func<Base, Base>` přiřazen`Func(Of Base, Base)` k proměnné typu ( v jazyce Visual Basic), protože návratový typ je kovariantní.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Třetí část kódu ukazuje, že delegát může být `Func<Derived, Derived>` přiřazen`Func(Of Derived, Derived)` k proměnné typu ( v jazyce Visual Basic), protože typ parametru je kontravariantní.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Poslední část kódu ukazuje, že delegát může být `Func<Derived, Base>` přiřazen`Func(Of Derived, Base)` k proměnné typu ( v jazyce Visual Basic), kombinující účinky typu parametru contravariant a kovariantní návratový typ.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Variance obecných a neobecných delegátů  
 V předchozím kódu podpis `MyMethod` přesně odpovídá podpisu vytvořeného obecného `Func<Base, Derived>` `Func(Of Base, Derived)` delegáta: ( v jazyce Visual Basic). Příklad ukazuje, že tento obecný delegát může být uložen v proměnných nebo parametrech metody, které mají více odvozených typů parametrů a <xref:System.Func%602>méně odvozených návratových typů, pokud jsou všechny typy delegátů vytvořeny z obecného typu delegáta .  
  
 Jedná se o důležitý fakt. Účinky kovariance a kontravariance v parametrech typu obecných delegátů jsou podobné účinkům kovariance a kontravariance v běžné vazbě delegáta (viz [Odchylka v delegátech (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [Odchylka v delegátech (Visual Basic).](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) Variance ve vazbě delegátu však funguje se všemi typy delegátů, nejen s obecnými typy delegátu, které mají parametry variantního typu. Variance ve vazbách delegátů navíc umožňuje metodě vázat se na jakýkoli delegát, který má více omezující parametry typu a méně omezující návratový typ, zatímco přiřazení obecných delegátů funguje pouze v případě, že oba typy delegátů jsou konstruovány ze stejné definice obecného typu.  
  
 Následující příklad znázorňuje kombinované účinky variance ve vazbě delegátu a variance u parametrů obecného typu. Příklad definuje hierarchii typů, která zahrnuje tři typy, od nejméně odvozených (`Type1`) až po nejvíce odvozené (`Type3`). Odchylka v běžné vazbě delegáta se používá `Type1` k vázání metody `Type3` s typem parametru `Type2` a návratového `Type2`typu obecného delegáta s typem parametru a návratovým typem . Výsledný obecný delegát je pak přiřazen jiné proměnné, jejíž `Type3` obecný typ delegáta má parametr typu a návratový `Type1`typ , pomocí kovariance a kontravariance parametrů obecného typu. Druhé přiřazení vyžaduje, aby byl typ proměnné i typ delegáta vytvořeny ze stejné <xref:System.Func%602>definice obecného typu, v tomto případě .  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  

## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definování variantních obecných rozhraní a delegátů
 Počínaje rozhraním .NET Framework 4 mají visual basic a c# klíčová slova, která umožňují označit parametry obecného typu rozhraní a delegátů jako kovariantní nebo kontravariantní.  
  
> [!NOTE]
> Počínaje verzí 2.0 rozhraní .NET Framework podporuje modul CLR (Common Language Runtime) anotace variance v parametrech obecného typu. Před rozhraním .NET Framework 4 je jediným způsobem, jak definovat obecnou třídu, která má tyto poznámky, použití zprostředkujícího jazyka Microsoft (MSIL), buď kompilací třídy pomocí [ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) nebo jeho vyzařováním v dynamickém sestavení.  
  
 Parametr covariant type je `out` označen`Out` klíčovým slovem `+` ( v jazyce Visual Basic pro [msil assembler).](../../../docs/framework/tools/ilasm-exe-il-assembler.md) Parametr kovariantního typu můžete použít jako návratovou hodnotu metody, která patří do rozhraní, nebo jako návratový typ delegátu. Typ kovariantního parametru nelze použít jako omezení obecného typu pro metody rozhraní.  
  
> [!NOTE]
> Pokud má metoda rozhraní parametr, který je typem obecného delegátu, může parametr kovariantního typu pro typ rozhraní být použit pro zadání parametru kontravariantního typu pro typ delegátu.  
  
 Parametr typu contravariant je `in` označen`In` klíčovým slovem `-` ( klíčové slovo v jazyce Visual Basic pro [msil assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Parametr kontravariantního typu můžete použít jako typ parametru metody, která patří do rozhraní, nebo jako typ parametru delegátu. Parametr kontravariantního typu lze použít jako omezení obecného typu pro metodu rozhraní.  
  
 Pouze typy rozhraní a typy delegátů mohou mít parametry variantního typu. Typy rozhraní nebo delegátů mohou mít parametry kovariantního i kontravariantního typu.  
  
 Jazyky Visual Basic a C# neumožňují porušení pravidel pro použití parametrů kovariantního a kontravariantního typu nebo přidání anotací kovariance a kontravariance parametrům typu pro jiné typy, než jsou typy rozhraní a delegátů. [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md) neprovádí takové kontroly, ale <xref:System.TypeLoadException> je vyvolána, pokud se pokusíte načíst typ, který porušuje pravidla.  
  
 Informace a ukázkový kód naleznete [v tématu Odchylka v obecných rozhraních (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [Odchylka v obecných rozhraních (Visual Basic).](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  

## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Seznam variantních obecných typů rozhraní a delegátů
 V rozhraní .NET Framework 4 mají následující typy rozhraní a delegáta parametry covariant a/nebo contravariant typu.  
  
|Typ|Parametry kovariantního typu|Parametry kontravariantního typu|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601>až<xref:System.Action%6016>||Ano|  
|<xref:System.Comparison%601>||Ano|  
|<xref:System.Converter%602>|Ano|Ano|  
|<xref:System.Func%601>|Ano||  
|<xref:System.Func%602>až<xref:System.Func%6017>|Ano|Ano|  
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
- [Kovariance a contravariance (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Odchylka v delegátech (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Odchylka v delegátech (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
