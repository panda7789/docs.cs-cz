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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c50d79f402d55a2fb5e859da4d61b04eeeb6931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579740"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kovariance a kontravariance v obecných typech
<a name="top"></a> Kovariance a kontravariance jsou podmínky, které odkazují na možnost používat více odvozený typ (konkrétnější) nebo méně odvozený typ (méně konkrétní) než bylo původně zadáno. Parametry obecného typu podporují kovarianci a kontravarianci za účelem zvýšení flexibility při přiřazování a používání obecných typů. Pokud hovoříme o typu systému, pak jsou pojmy kovariance, kontravariance a invariance definovány následovně: Příklady předpokládají základní třídu s názvem `Base` a odvozené třídy s názvem `Derived`.  
  
-   `Covariance`  
  
     Umožňuje používat více odvozený typ, než bylo původně zadáno.  
  
     Můžete přiřadit instanci `IEnumerable<Derived>` (`IEnumerable(Of Derived)` v jazyce Visual Basic) proměnné typu `IEnumerable<Base>`.  
  
-   `Contravariance`  
  
     Umožňuje používat obecnější (méně odvozený) typ, než byl původně zadán.  
  
     Můžete přiřadit instanci `IEnumerable<Base>` (`IEnumerable(Of Base)` v jazyce Visual Basic) proměnné typu `IEnumerable<Derived>`.  
  
-   `Invariance`  
  
     To znamená, že můžete použít pouze původně zadaný typ; parametr invariantního obecného typu není ani kovariantní, ani kontravariantní.  
  
     Nelze přiřadit instanci `IEnumerable<Base>` (`IEnumerable(Of Base)` v jazyce Visual Basic) proměnné typu `IEnumerable<Derived>` nebo naopak.  
  
 Parametry typu kovariantní umožňují provést přiřazení, které vypadají podobně jako v běžném provozu [polymorfismus](~/docs/csharp/programming-guide/classes-and-structs/polymorphism.md), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601> Třída implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní, tak `List<Derived>` (`List(Of Derived)` v jazyce Visual Basic) implementuje `IEnumerable<Derived>`. Parametr kovariantního typu dokončí zbývající úkoly.  
  
 Kontravariance se naopak zdá být neintuitivní. Následující příklad vytvoří delegáta typu `Action<Base>` (`Action(Of Base)` v jazyce Visual Basic) a poté tohoto delegáta přiřadí proměnné typu `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Zdá se, že se jedná o zpětnou akci, jde však o typově bezpečný kód, který se zkompiluje a spustí. Výraz lambda odpovídá delegáta, který je přiřazen, takže definuje metodu, která přijímá jeden parametr typu `Base` a který nemá žádnou návratovou hodnotu. Výsledný delegát může být přiřazen k proměnné typu `Action<Derived>` protože parametr typu `T` z <xref:System.Action%601> delegáta je kontravariant. Kód je bezpečnost typů protože `T` Určuje typ parametru. Pokud delegát typu `Action<Base>` je volána, jako by šlo o delegáta typu `Action<Derived>`, její argument musí být typu `Derived`. Tento argument můžete vždy předat bezpečně základní metoda, protože parametr metody je typu `Base`.  
  
 Obecně lze parametr konvariantního typu použít jako návratový typ delegátu a parametry kontravariantního typu mohou být použity jako typy parametrů. V případě konkrétního rozhraní mohou být parametry kovariantního typu použity jako návratové typy metod rozhraní a parametry kontravariantního typu mohou být použity jako typy parametrů metod rozhraní.  
  
 Kovariance a kontravariance se souhrnně označují jako *odchylky*. Parametr obecného typu, který není označen jako kovariantní nebo kontravariant se označuje jako *invariantní*. Stručný souhrn faktů o varianci v modulu CLR (Common Language Runtime):  
  
-   V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], jsou omezeny na obecné rozhraní a obecný delegát typy parametrů typu variant.  
  
-   Obecná rozhraní nebo obecné typy delegátů mohou mít parametry kovariantního i kontravariantního typu.  
  
-   Variance platí pouze pro odkazované typy. Pokud zadáte typ hodnoty pro parametr variantního typu, je tento parametr typu pro výsledný konstruovaný typ invariantní.  
  
-   Variance se nevztahuje na kombinaci delegátů. To znamená, daných dvou delegátů typů `Action<Derived>` a `Action<Base>` (`Action(Of Derived)` a `Action(Of Base)` v jazyce Visual Basic), druhá delegáta nelze kombinovat s první, i když výsledkem bude typově bezpečný. Odchylky umožňuje druhého delegáta pro přiřazení k proměnné typu `Action<Derived>`, ale delegáti můžete kombinovat pouze v případě, že jejich typy přesně shodují.  
  
 Následující pododdíly obsahují podrobný popis parametrů kovariantního a kontravariantního typu:  
  
-   [Obecná rozhraní s kovariantní parametry typu](#InterfaceCovariantTypeParameters)  
  
-   [Obecná rozhraní s kontravariant obecné parametry typu](#InterfaceCovariantTypeParameters)  
  
-   [Obecní delegáti s Variant parametry typu](#DelegateVariantTypeParameters)  
  
-   [Definování variantních obecných rozhraní a delegáti](#DefiningVariantTypeParameters)  
  
-   [Seznam variantních obecných rozhraní a typů delegátů.](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Obecná rozhraní s parametry kovariantního typu  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], několik obecných rozhraní má kovariantní parametry typu; například: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, a <xref:System.Linq.IGrouping%602>. Všechny parametry typu těchto rozhraní jsou kovariantní. Parametry typu se tedy používají pouze pro návratové typy členů.  
  
 Následující příklad znázorňuje parametry kovariantního typu. V příkladu definuje dva typy: `Base` má statickou metodu s názvem `PrintBases` , která má `IEnumerable<Base>` (`IEnumerable(Of Base)` v jazyce Visual Basic) a vytiskne prvky. `Derived` dědí z `Base`. V příkladu se vytváří prázdnou `List<Derived>` (`List(Of Derived)` v jazyce Visual Basic) a ukazuje, že tento typ se dá předat do `PrintBases` a přiřazený k proměnné typu `IEnumerable<Base>` bez přetypování. <xref:System.Collections.Generic.List%601> implementuje <xref:System.Collections.Generic.IEnumerable%601>, který má jeden kovariantní typ parametru. Kovariantní parametr typu je důvod, proč instanci `IEnumerable<Derived>` lze použít místo `IEnumerable<Base>`.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Zpět na začátek](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Obecná rozhraní s parametry obecného kontravariantního typu  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], několik obecných rozhraní má parametry typu kontravariant; například: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, a <xref:System.Collections.Generic.IEqualityComparer%601>. Tato rozhraní mají pouze parametry kontravariantního typu, takže parametry typu slouží pouze jako typy parametrů u členů rozhraní.  
  
 Následující příklad znázorňuje parametry kontravariantního typu. V příkladu definuje abstraktní (`MustInherit` v jazyce Visual Basic) `Shape` třídy s `Area` vlastnost. Tento příklad také definuje `ShapeAreaComparer` třídu, která implementuje `IComparer<Shape>` (`IComparer(Of Shape)` v jazyce Visual Basic). Implementace <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> metoda je založena na hodnotě `Area` vlastnost, takže `ShapeAreaComparer` lze použít k seřazení `Shape` objekty podle oblasti.  
  
 `Circle` Třída dědí `Shape` a přepíše `Area`. V příkladu se vytváří <xref:System.Collections.Generic.SortedSet%601> z `Circle` objekty, pomocí konstruktor, který přebírá `IComparer<Circle>` (`IComparer(Of Circle)` v jazyce Visual Basic). Ale namísto předávání `IComparer<Circle>`, předá tento příklad `ShapeAreaComparer` objekt, který implementuje `IComparer<Shape>`. V příkladu můžete předat srovnávání méně odvozený typ (`Shape`) při kód volá pro porovnání více odvozeného typu (`Circle`), protože parametr typu <xref:System.Collections.Generic.IComparer%601> obecné rozhraní je kontravariant.  
  
 Když nový `Circle` objekt přidá do `SortedSet<Circle>`, `IComparer<Shape>.Compare` – metoda (`IComparer(Of Shape).Compare` metody v jazyce Visual Basic) z `ShapeAreaComparer` objektu se říká pokaždé, když nového elementu je ve srovnání s existující elementu. Typ parametru metody (`Shape`) je menší odvozený než typ, který je předáván (`Circle`), takže volání je typ bezpečné. Umožňuje kontravariance `ShapeAreaComparer` seřadit kolekce všechny jeden typ, a také do smíšené kolekce typů, které jsou odvozeny od `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Zpět na začátek](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Obecné delegáty s parametry variantního typu  
 V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], `Func` obecní delegáti, jako například <xref:System.Func%602>, mají kovariantní návratové typy a typy parametrů kontravariant. `Action` Obecní delegáti, jako například <xref:System.Action%602>, mají typy parametrů kontravariant. To znamená, že delegáty může být přiřazen do proměnné, které mají více odvozené typy parametrů a (u `Func` obecní delegáti) méně odvozené návratové typy.  
  
> [!NOTE]
>  Poslední parametr obecného typu `Func` obecní delegáti Určuje typ vrácené hodnoty v hlavičce delegáta. Je kovariant (`out` – klíčové slovo), zatímco ostatní parametry obecného typu je kontravariant (`in` – klíčové slovo).  
  
 Následující kód to znázorňuje. První část kódu definuje třídu s názvem `Base`, třídy s názvem `Derived` , dědí `Base`a jinou třídu s `static` – metoda (`Shared` v jazyce Visual Basic) s názvem `MyMethod`. Tato metoda přebírá instanci `Base` a vrací instanci třídy `Derived`. (Pokud je argumentem instanci `Derived`, `MyMethod` ji vrátí; pokud je argument instance `Base`, `MyMethod` vrátí novou instanci třídy `Derived`.) V `Main()`, v příkladu se vytváří instance `Func<Base, Derived>` (`Func(Of Base, Derived)` v jazyce Visual Basic), která představuje `MyMethod`a ukládá v proměnné `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Druhá část kódu ukazuje, že delegát může být přiřazen k proměnné typu `Func<Base, Base>` (`Func(Of Base, Base)` v jazyce Visual Basic), protože návratového typu je kovariant.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Třetí část kódu ukazuje, že delegát může být přiřazen proměnné typu `Func<Derived, Derived>` (`Func(Of Derived, Derived)` v jazyce Visual Basic), protože parametr typu je kontravariant.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Poslední část kódu ukazuje, že delegát může být přiřazen k proměnné typu `Func<Derived, Base>` (`Func(Of Derived, Base)` v jazyce Visual Basic), kombinování důsledky kontravariant zadejte parametr a kovariant návratovým typem.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Variance obecných a neobecných delegátů  
 V předchozím kódu, podpis `MyMethod` přesně odpovídá podpis vytvořený obecný delegát: `Func<Base, Derived>` (`Func(Of Base, Derived)` v jazyce Visual Basic). Příklad ukazuje, že tento obecný delegát může být uložené v proměnné nebo parametru metody, které mají více odvozené typy parametrů a méně odvozené návratové typy tak dlouho, dokud všechny typy delegáta se vytvářejí na základě typu obecný delegát <xref:System.Func%602>.  
  
 Jedná se o důležitý fakt. Důsledky kovariance a kontravariance v parametrech typu obecných delegátů jsou podobné účinky kovariance a kontravariance v běžných vazbách delegátů (viz [odchylky v delegátech](https://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)). Variance ve vazbě delegátu však funguje se všemi typy delegátů, nejen s obecnými typy delegátu, které mají parametry variantního typu. Variance ve vazbách delegátů navíc umožňuje metodě vázat se na jakýkoli delegát, který má více omezující parametry typu a méně omezující návratový typ, zatímco přiřazení obecných delegátů funguje pouze v případě, že oba typy delegátů jsou konstruovány ze stejné definice obecného typu.  
  
 Následující příklad znázorňuje kombinované účinky variance ve vazbě delegátu a variance u parametrů obecného typu. V příkladu je definován typ hierarchie, která zahrnuje tři typy od nejméně odvozené (`Type1`) k nejvíce odvozenému (`Type3`). Odchylky v běžných delegátů vazby se používá k navázání metody s parametrem typu `Type1` a návratový typ `Type3` pro obecný delegát s parametrem typu `Type2` a návratový typ `Type2`. Výsledný obecný delegát je poté přiřazen jiné proměnné s typem obecný delegát má parametr typu `Type3` a návratový typ `Type1`, pomocí kovariance a kontravariance parametrů obecného typu. Druhé přiřazení vyžaduje typ proměnné a typ delegáta zkonstruovat z stejné definice obecného typu, v takovém případě <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Zpět na začátek](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definování variantních obecných rozhraní a delegátů  
 Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Visual Basic a C# mají klíčová slova, která vám umožní označit parametry obecného typu rozhraní a delegátů jako kovariantní nebo kontravariant.  
  
> [!NOTE]
>  Počínaje verzí 2.0 rozhraní .NET Framework podporuje modul CLR (Common Language Runtime) anotace variance v parametrech obecného typu. Před verzí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], jediný způsob, jak definovat obecné třídy, která má tyto poznámky se má používat Microsoft (MSIL intermediate language), kompilovat třídu s [Ilasm.exe (IL assembleru)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) nebo vydat v dynamický sestavení.  
  
 Kovariantní typ parametru je označené jako `out` – klíčové slovo (`Out` – klíčové slovo v jazyce Visual Basic `+` pro [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Parametr kovariantního typu můžete použít jako návratovou hodnotu metody, která patří do rozhraní, nebo jako návratový typ delegátu. Typ kovariantního parametru nelze použít jako omezení obecného typu pro metody rozhraní.  
  
> [!NOTE]
>  Pokud má metoda rozhraní parametr, který je typem obecného delegátu, může parametr kovariantního typu pro typ rozhraní být použit pro zadání parametru kontravariantního typu pro typ delegátu.  
  
 Parametr typu kontravariant je označené jako `in` – klíčové slovo (`In` – klíčové slovo v jazyce Visual Basic `-` pro [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Parametr kontravariantního typu můžete použít jako typ parametru metody, která patří do rozhraní, nebo jako typ parametru delegátu. Parametr kontravariantního typu lze použít jako omezení obecného typu pro metodu rozhraní.  
  
 Pouze typy rozhraní a typy delegátů mohou mít parametry variantního typu. Typy rozhraní nebo delegátů mohou mít parametry kovariantního i kontravariantního typu.  
  
 Jazyky Visual Basic a C# neumožňují porušení pravidel pro použití parametrů kovariantního a kontravariantního typu nebo přidání anotací kovariance a kontravariance parametrům typu pro jiné typy, než jsou typy rozhraní a delegátů. [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md) neprovádí tyto kontroly, ale <xref:System.TypeLoadException> je vyvolána, pokud se pokusíte načíst typ, který je v rozporu pravidla.  
  
 Informace a příklady kódu najdete v tématu [odchylky obecných rozhraní](https://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a).  
  
 [Zpět na začátek](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Seznam variantních obecných typů rozhraní a delegátů  
 V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], následující typy rozhraní a delegátů kovariantní nebo kontravariant parametry typu.  
  
|Typ|Parametry kovariantního typu|Parametry kontravariantního typu|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601> K <xref:System.Action%6016>||Ano|  
|<xref:System.Comparison%601>||Ano|  
|<xref:System.Converter%602>|Ano|Ano|  
|<xref:System.Func%601>|Ano||  
|<xref:System.Func%602> K <xref:System.Func%6017>|Ano|Ano|  
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
 [Kovariance a kontravariance (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
 [Kovariance a kontravariance (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)    
 [Odchylky v delegátech](https://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)
