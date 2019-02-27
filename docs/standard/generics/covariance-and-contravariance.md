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
ms.openlocfilehash: 931edf3610d083f6821ec87d3e05db855e88c6f9
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836419"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kovariance a kontravariance v obecných typech
<a name="top"></a> Kovariance a kontravariance jsou pojmy, které označují schopnost používat více odvozeného typu (konkrétnější) nebo méně odvozeného typu (specifické pro less) než byl původně zadán. Parametry obecného typu podporují kovarianci a kontravarianci za účelem zvýšení flexibility při přiřazování a používání obecných typů. Pokud hovoříme o typu systému, pak jsou pojmy kovariance, kontravariance a invariance definovány následovně: V příkladech se předpokládá základní třídu s názvem `Base` a odvozenou třídu s názvem `Derived`.  
  
-   `Covariance`  
  
     Umožňuje použít více odvozený typ, než byl původně zadán.  
  
     Můžete přiřadit instanci `IEnumerable<Derived>` (`IEnumerable(Of Derived)` v jazyce Visual Basic) na proměnnou typu `IEnumerable<Base>`.  
  
-   `Contravariance`  
  
     Umožňuje používat obecnější (méně odvozený) typ, než byl původně zadán.  
  
     Můžete přiřadit instanci `Action<Base>` (`Action(Of Base)` v jazyce Visual Basic) na proměnnou typu `Action<Derived>`.  
  
-   `Invariance`  
  
     To znamená, že můžete použít pouze původně zadaný typ; parametr invariantního obecného typu není ani kovariantní, ani kontravariantní.  
  
     Nelze přiřadit instanci `List<Base>` (`List(Of Base)` v jazyce Visual Basic) na proměnnou typu `List<Derived>` nebo naopak.  
  
 Parametry kovariantního typu umožňují vytvářet přiřazení, které vypadají podobně jako běžný [polymorfismus](~/docs/csharp/programming-guide/classes-and-structs/polymorphism.md), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601> Implementuje třída <xref:System.Collections.Generic.IEnumerable%601> rozhraní, takže `List<Derived>` (`List(Of Derived)` v jazyce Visual Basic) implementuje `IEnumerable<Derived>`. Parametr kovariantního typu dokončí zbývající úkoly.  
  
 Kontravariance se naopak zdá být neintuitivní. Následující příklad vytvoří delegát typu `Action<Base>` (`Action(Of Base)` v jazyce Visual Basic) a poté tento delegát přiřadí k proměnné typu `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Zdá se, že se jedná o zpětnou akci, jde však o typově bezpečný kód, který se zkompiluje a spustí. Výraz lambda se shoduje s delegátem je přiřazen, takže definuje metodu, která přijímá jeden parametr typu `Base` a, který nemá žádnou návratovou hodnotu. Výsledný delegát může být přiřazen proměnné typu `Action<Derived>` protože parametr typu `T` z <xref:System.Action%601> delegát je kontravariantní. Kód je typově bezpečné protože `T` Určuje typ parametru. Pokud delegát typu `Action<Base>` je vyvolána, jako kdyby se jednalo o delegát typu `Action<Derived>`, její argument musí být typu `Derived`. Tento argument lze vždy předat bezpečně základní metodě, protože parametr metody je typu `Base`.  
  
 Obecně lze parametr konvariantního typu použít jako návratový typ delegátu a parametry kontravariantního typu mohou být použity jako typy parametrů. V případě konkrétního rozhraní mohou být parametry kovariantního typu použity jako návratové typy metod rozhraní a parametry kontravariantního typu mohou být použity jako typy parametrů metod rozhraní.  
  
 Kovariance a kontravariance se souhrnně označují jako *variance*. Parametr obecného typu, který není označen jako kovariantní nebo kontravariantní se označuje jako *invariantní*. Stručný souhrn faktů o varianci v modulu CLR (Common Language Runtime):  
  
-   V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], parametry variantního typu omezeny na obecná rozhraní a obecné typy delegátů.  
  
-   Obecná rozhraní nebo obecné typy delegátů mohou mít parametry kovariantního i kontravariantního typu.  
  
-   Variance platí pouze pro odkazované typy. Pokud zadáte typ hodnoty pro parametr variantního typu, je tento parametr typu pro výsledný konstruovaný typ invariantní.  
  
-   Variance se nevztahuje na kombinaci delegátů. To znamená, že u daných dvou delegátů typů `Action<Derived>` a `Action<Base>` (`Action(Of Derived)` a `Action(Of Base)` v jazyce Visual Basic), nelze kombinovat druhý delegát s prvním Ačkoli výsledek by byl typově bezpečný. Variance umožňuje druhého delegátu má být přiřazena k proměnné typu `Action<Derived>`, delegáty lze však kombinovat pouze v případě přesné shody typů.  
  
 Následující pododdíly obsahují podrobný popis parametrů kovariantního a kontravariantního typu:  
  
-   [Obecná rozhraní s parametry kovariantního typu](#InterfaceCovariantTypeParameters)  
  
-   [Obecná rozhraní s parametry obecného kontravariantního typu](#InterfaceCovariantTypeParameters)  
  
-   [Parametry typu obecné delegáty s typ Variant](#DelegateVariantTypeParameters)  
  
-   [Definování variantních obecných rozhraní a delegátů](#DefiningVariantTypeParameters)  
  
-   [Seznam variantních obecných rozhraní a typy delegátů](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Obecná rozhraní s parametry kovariantního typu  
 Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], mají několik obecných rozhraní parametry kovariantního typu, třeba: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, a <xref:System.Linq.IGrouping%602>. Všechny parametry typu těchto rozhraní jsou kovariantní. Parametry typu se tedy používají pouze pro návratové typy členů.  
  
 Následující příklad znázorňuje parametry kovariantního typu. Příklad definuje dva typy: `Base` má statickou metodu s názvem `PrintBases` , která má `IEnumerable<Base>` (`IEnumerable(Of Base)` v jazyce Visual Basic) a tisk prvků. `Derived` dědí z `Base`. Tento příklad vytvoří prázdnou `List<Derived>` (`List(Of Derived)` v jazyce Visual Basic) a ukazuje, že tento typ může být předán `PrintBases` a přiřadit proměnné typu `IEnumerable<Base>` bez přetypování. <xref:System.Collections.Generic.List%601> implementuje <xref:System.Collections.Generic.IEnumerable%601>, který má jediný parametr kovariantního typu. Typ kovariantního parametru je důvod, proč instance `IEnumerable<Derived>` lze použít místo `IEnumerable<Base>`.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Zpět na začátek](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Obecná rozhraní s parametry obecného kontravariantního typu  
 Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], mají několik obecných rozhraní parametry kontravariantního typu; například: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, a <xref:System.Collections.Generic.IEqualityComparer%601>. Tato rozhraní mají pouze parametry kontravariantního typu, takže parametry typu slouží pouze jako typy parametrů u členů rozhraní.  
  
 Následující příklad znázorňuje parametry kontravariantního typu. Tento příklad definuje abstraktní (`MustInherit` v jazyce Visual Basic) `Shape` třídy s `Area` vlastnost. Příklad také definuje `ShapeAreaComparer` třídu, která implementuje `IComparer<Shape>` (`IComparer(Of Shape)` v jazyce Visual Basic). Provádění <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> metoda je založena na hodnotě `Area` vlastnosti, takže `ShapeAreaComparer` slouží k seřazení `Shape` objekty podle oblasti.  
  
 `Circle` Třída dědí `Shape` a přepíše `Area`. V příkladu se vytvoří <xref:System.Collections.Generic.SortedSet%601> z `Circle` pomocí konstruktoru, který přebírá `IComparer<Circle>` (`IComparer(Of Circle)` v jazyce Visual Basic). Namísto předání `IComparer<Circle>`, příklad předá `ShapeAreaComparer` objektu, který implementuje `IComparer<Shape>`. Příklad může předat porovnávací metodu méně odvozeného typu (`Shape`) když kód volá porovnávací metodu více odvozeného typu (`Circle`), protože parametr typu <xref:System.Collections.Generic.IComparer%601> obecného rozhraní je kontravariantní.  
  
 Když je nový `Circle` objekt přidán do `SortedSet<Circle>`, `IComparer<Shape>.Compare` – metoda (`IComparer(Of Shape).Compare` metody v jazyce Visual Basic) z `ShapeAreaComparer` objektu je volána pokaždé, když má nový element je ve srovnání s existujícího prvku. Typ parametru metody (`Shape`) je méně odvozený než předávaný typ (`Circle`), takže volání je typově bezpečný. Kontravariance umožní `ShapeAreaComparer` řazení kolekcí jakéhokoli jednotlivého typu a také kombinaci kolekcí typů odvozených z `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Zpět na začátek](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Obecné delegáty s parametry variantního typu  
 V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], `Func` obecné delegáty, jako například <xref:System.Func%602>, kovariantní návratové typy a kontravariantní typy parametru. `Action` Obecné delegáty, jako například <xref:System.Action%602>, mají kontravariantní typy parametru. To znamená, že delegáty lze přiřadit k proměnné, které mají více odvozené typy parametrů a (v případě třídy `Func` obecných delegátů) méně odvozené návratové typy.  
  
> [!NOTE]
>  Poslední parametr obecného typu `Func` obecné delegáty Určuje typ návratové hodnoty v signatuře delegátu. Jedná se o kovariantní (`out` – klíčové slovo), zatímco jiné parametry obecného typu jsou kontravariantní (`in` – klíčové slovo).  
  
 Následující kód to znázorňuje. První část kódu definuje třídu s názvem `Base`, třídu s názvem `Derived` , která dědí `Base`a další třídu s `static` – metoda (`Shared` v jazyce Visual Basic) s názvem `MyMethod`. Metoda použije instanci `Base` a vrátí instanci `Derived`. (Pokud je argument instancí `Derived`, `MyMethod` jej vrátí; pokud je argument instancí `Base`, `MyMethod` vrátí novou instanci třídy `Derived`.) V `Main()`, tento příklad vytvoří instanci `Func<Base, Derived>` (`Func(Of Base, Derived)` v jazyce Visual Basic), která představuje `MyMethod`a uloží jej do proměnné `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Druhá část kódu znázorňuje, delegát může být přiřazen proměnné typu `Func<Base, Base>` (`Func(Of Base, Base)` v jazyce Visual Basic), protože návratový typ je kovariantní.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Třetí část kódu znázorňuje, delegát může být přiřazen proměnné typu `Func<Derived, Derived>` (`Func(Of Derived, Derived)` v jazyce Visual Basic), protože typ parametru je kontravariantní.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Poslední část kódu znázorňuje, delegát může být přiřazen proměnné typu `Func<Derived, Base>` (`Func(Of Derived, Base)` v jazyce Visual Basic), kombinací vlivu kontravariantního typu parametru a kovariantního návratového typu.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Variance obecných a neobecných delegátů  
 V předchozím kódu podpis `MyMethod` přesně shoduje se signaturou konstruovaného obecného delegátu: `Func<Base, Derived>` (`Func(Of Base, Derived)` v jazyce Visual Basic). Příklad ukazuje, že tento obecný delegát může být uložen v proměnných nebo parametrech metod, které mají více odvozené typy parametrů a méně odvozené návratové typy tak dlouho, dokud všechny typy delegátů jsou konstruovány ze typu obecného delegátu <xref:System.Func%602>.  
  
 Jedná se o důležitý fakt. Účinky kovariance a kontravariance v parametrech typu obecných delegátů jsou podobné účinkům kovariance a kontravariance v běžných vazbách delegátů (viz [odchylky v delegátech (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [ Odchylky v delegátech (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)). Variance ve vazbě delegátu však funguje se všemi typy delegátů, nejen s obecnými typy delegátu, které mají parametry variantního typu. Variance ve vazbách delegátů navíc umožňuje metodě vázat se na jakýkoli delegát, který má více omezující parametry typu a méně omezující návratový typ, zatímco přiřazení obecných delegátů funguje pouze v případě, že oba typy delegátů jsou konstruovány ze stejné definice obecného typu.  
  
 Následující příklad znázorňuje kombinované účinky variance ve vazbě delegátu a variance u parametrů obecného typu. Příklad definuje hierarchie typů, která zahrnuje tři typy od nejméně odvozené (`Type1`) k nejvíce odvozenému (`Type3`). Odchylky v běžných vazbách delegátů se používá k navázání metody s parametrem typu `Type1` a návratový typ `Type3` k obecnému delegátu s parametrem typu `Type2` a návratový typ `Type2`. Výsledný obecný delegát je poté přiřazen jiné proměnné, jejíž typ obecného delegátu má parametr typu `Type3` a návratový typ `Type1`, použitím kovariance a kontravariance parametrů obecného typu. Druhé přiřazení vyžaduje typ proměnné i typ delegátu byly konstruovány ze stejné obecné definice typu, v tomto případě <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Zpět na začátek](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definování variantních obecných rozhraní a delegátů  
 Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Visual Basic a C# mít klíčová slova, která umožňují označit parametry obecného typu rozhraní a delegátů jako kovariantní nebo kontravariantní.  
  
> [!NOTE]
>  Počínaje verzí 2.0 rozhraní .NET Framework podporuje modul CLR (Common Language Runtime) anotace variance v parametrech obecného typu. Před verzí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], je jediný způsob, jak definovat obecné třídy, která má tyto anotace použít jazyk Microsoft intermediate language (MSIL) buď kompilováním třídy pomocí [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) anebo jejím v dynamické sestavení.  
  
 Typ kovariantního parametru je označen klíčovým `out` – klíčové slovo (`Out` – klíčové slovo v jazyce Visual Basic `+` pro [jazyk MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Parametr kovariantního typu můžete použít jako návratovou hodnotu metody, která patří do rozhraní, nebo jako návratový typ delegátu. Typ kovariantního parametru nelze použít jako omezení obecného typu pro metody rozhraní.  
  
> [!NOTE]
>  Pokud má metoda rozhraní parametr, který je typem obecného delegátu, může parametr kovariantního typu pro typ rozhraní být použit pro zadání parametru kontravariantního typu pro typ delegátu.  
  
 Parametr kontravariantního typu je označené `in` – klíčové slovo (`In` – klíčové slovo v jazyce Visual Basic `-` pro [jazyk MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Parametr kontravariantního typu můžete použít jako typ parametru metody, která patří do rozhraní, nebo jako typ parametru delegátu. Parametr kontravariantního typu lze použít jako omezení obecného typu pro metodu rozhraní.  
  
 Pouze typy rozhraní a typy delegátů mohou mít parametry variantního typu. Typy rozhraní nebo delegátů mohou mít parametry kovariantního i kontravariantního typu.  
  
 Jazyky Visual Basic a C# neumožňují porušení pravidel pro použití parametrů kovariantního a kontravariantního typu nebo přidání anotací kovariance a kontravariance parametrům typu pro jiné typy, než jsou typy rozhraní a delegátů. [Jazyk MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md) neprovádí tyto kontroly, ale <xref:System.TypeLoadException> je vyvolána, pokud se pokusíte načíst typ, který porušuje pravidla.  
  
 Informace a příklady kódu naleznete v tématu [odchylky obecných rozhraní (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [odchylky obecných rozhraní (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
 [Zpět na začátek](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Seznam variantních obecných typů rozhraní a delegátů  
 V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], následující typy rozhraní a delegátů kovariantního a/nebo parametry kontravariantního typu.  
  
|Typ|Parametry kovariantního typu|Parametry kontravariantního typu|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601> k <xref:System.Action%6016>||Ano|  
|<xref:System.Comparison%601>||Ano|  
|<xref:System.Converter%602>|Ano|Ano|  
|<xref:System.Func%601>|Ano||  
|<xref:System.Func%602> k <xref:System.Func%6017>|Ano|Ano|  
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
  
## <a name="see-also"></a>Viz také:

- [Kovariance a kontravariance (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kovariance a kontravariance (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Odchylky v delegátech (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Odchylky v delegátech (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
