---
title: x:TypeArguments – direktiva
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071351"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments – direktiva

Předá argumenty typu omezující typu obecného konstruktoru obecného typu.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`object`|Deklarace prvku objektu typu XAML, která je podpořena obecným typem CLR. Pokud `object` odkazuje na typ XAML, který není z výchozího `object` oboru názvů XAML, vyžaduje předponu k označení oboru názvů XAML, kde `object` existuje.|
|`typeString`|Řetězec, který deklaruje jeden nebo více názvů typů XAML jako řetězce, který poskytuje argumenty typu pro obecný typ CLR. Další poznámky k syntaxi naleznete v tématu Poznámky.|

## <a name="remarks"></a>Poznámky

Ve většině případů jsou předponou typy XAML, `typeString` které se používají jako informační položka v řetězci. Typické typy obecných omezení CLR <xref:System.Int32> (například a <xref:System.String>) pocházejí z knihoven základní třídy CLR. Tyto knihovny nejsou mapovány na typické výchozí prostory názvů XAML specifické pro architekturu, a proto vyžadují mapování předpony pro použití XAML.

Pomocí oddělovače čárky můžete zadat více než jeden název typu XAML.

Pokud samotná obecná omezení používají obecné typy, mohou být vnořené argumenty typu omezení obsaženy v závorcích ().

Všimněte si, `x:TypeArguments` že tato definice je specifická pro služby .NET XAML services a pomocí podpory CLR. Definici na úrovni jazyka naleznete v [ \[oddíle\] 5.3.11 MS-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="usage-examples"></a>Příklady použití

V těchto příkladech předpokládejme, že jsou deklarovány následující definice oboru názvů XAML:

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>>\<řetězce seznamu

`<scg:List x:TypeArguments="sys:String" ...>`kvituje <xref:System.Collections.Generic.List%601> nový <xref:System.String> s argumentem typu.

### <a name="dictionarystringstring"></a>Řetězec\<slovníku,>

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`kvituje <xref:System.Collections.Generic.Dictionary%602> nový <xref:System.String> se dvěma argumenty typu.

### <a name="queuekeyvaluepairstringstring"></a>Řetězec spáry\<KeyValue klíče fronty<,>> řetězce

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`konkretizovat <xref:System.Collections.Generic.Queue%601> nový, který <xref:System.Collections.Generic.KeyValuePair%602> má omezení s <xref:System.String> argumenty vnitřní holužní typ a <xref:System.String>.

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>Použití xaml 2006 a WPF obecné xaml

Pro použití XAML 2006 a XAML, který se používá pro `x:TypeArguments` aplikace WPF, existují následující omezení pro a obecné použití typu z XAML obecně:

- Pouze kořenový prvek souboru XAML může podporovat obecné použití XAML, které odkazuje na obecný typ.

- Kořenový prvek musí být mapován na obecný typ s alespoň jedním argumentem typu. Příklad: <xref:System.Windows.Navigation.PageFunction%601>. Funkce stránky jsou primární scénář pro podporu obecného využití XAML v WPF.

- Kořenový prvek XAML objektu element pro obecný `x:Class`musí také deklarovat částečné třídy pomocí . To platí i v případě, že definování akce sestavení WPF.

- `x:TypeArguments`Nelze odkazovat na vnořená obecná omezení.

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 nebo XAML 2006 bez wpf 3.0 nebo WPF 3.5 závislost

Ve službách .NET XAML pro XAML 2006 nebo XAML 2009 jsou uvolněná omezení týkající se WPF pro použití obecného xaml. Můžete vytvořit konstanci elementu obecného objektu na libovolné pozici ve značkách XAML, které může podporovat systém typu zálohování a objektový model.

Pokud používáte XAML 2009 namísto mapování clr základní typy získat xaml typy pro základní jazyk běžné jazykové primitivy, `typeString`můžete použít [vestavěné typy pro běžné xaml jazyk primitiv](types-for-primitives.md) y jako informační položky v . Můžete například deklarovat následující (mapování předpony nejsou zobrazena, ale x je jazyk XAML XAML pro XAML 2009):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

V WPF a při cílení na rozhraní .NET Framework 4 nebo .NET Core 3.0 (nebo novější) můžete používat funkce XAML 2009 společně s, `x:TypeArguments` ale pouze pro volné XAML (XAML, který není kompilován se značkami). XAML kompilované značkami pro WPF a formu BAML XAML aktuálně nepodporují klíčová slova a funkce XAML 2009. Pokud potřebujete označit kompilovat XAML, musíte pracovat pod omezeními uvedenými v části [XAML 2006 a WPF Generic XAML Usages.](#xaml-2006-and-wpf-generic-xaml-usages) BAML je podporován a podporuje se pouze v rozhraní .NET Framework.

## <a name="see-also"></a>Viz také

- [x:Class – direktiva](xclass-directive.md)
- [x:Type – rozšíření značek](xtype-markup-extension.md)
- [Předdefinované typy obecných primitiv jazyka XAML](types-for-primitives.md)
- [Obecné typy v jazyku XAML](generics.md)
