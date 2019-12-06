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
ms.openlocfilehash: 2e64c716ee85934bf02c016ee408b8e5f612a819
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837191"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments – direktiva
Předává omezující argumenty typu Obecné k konstruktoru obecného typu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`object`|Deklarace elementu objektu typu XAML, který je zálohovaný obecným typem CLR. Pokud `object` odkazuje na typ XAML, který není z výchozího oboru názvů jazyka XAML, `object` vyžaduje předponu k označení oboru názvů XAML, kde `object` existuje.|  
|`typeString`|Řetězec, který deklaruje jeden nebo více názvů typů XAML jako řetězců, které poskytuje argumenty typu pro obecný typ CLR. Další poznámky k syntaxi najdete v části poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 Ve většině případů jsou typy XAML, které jsou používány jako informační položka v řetězci `typeString`, předem opraveny. Typické typy obecných omezení CLR (například <xref:System.Int32> a <xref:System.String>) pocházejí z knihoven základních tříd CLR. Tyto knihovny nejsou namapovány na typické standardní obory názvů jazyka XAML specifické pro rozhraní, a proto vyžadují mapování předpony pro použití XAML.  
  
 Pomocí oddělovače čárky lze zadat více než jeden název typu XAML.  
  
 Pokud obecná omezení samy používají obecné typy, vnořené argumenty typu omezení mohou být obsaženy v závorkách ().  
  
 Všimněte si, že tato definice `x:TypeArguments` je specifická pro .NET Framework služby XAML a pomocí zálohování CLR. Definici na úrovni jazyka najdete v [\[MS-XAML\] oddílu 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="usage-examples"></a>Příklady použití  
 Pro tyto příklady Předpokládejme, že jsou deklarovány následující definice oboru názvů XAML:  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Seznam\<řetězců >  
 `<scg:List x:TypeArguments="sys:String" ...>` vytvoří instanci nového <xref:System.Collections.Generic.List%601> s argumentem <xref:System.String>ho typu.  
  
### <a name="dictionarystringstring"></a>Řetězec\<slovníku, řetězec >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` vytvoří instanci nového <xref:System.Collections.Generic.Dictionary%602> se dvěma argumenty <xref:System.String>ho typu.  
  
### <a name="queuekeyvaluepairstringstring"></a>Queue < nenašla\<řetězec, řetězec > >  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` vytvoří instanci nového <xref:System.Collections.Generic.Queue%601>, která má omezení <xref:System.Collections.Generic.KeyValuePair%602> s argumenty typu vnitřního omezení <xref:System.String> a <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>Obecná použití XAML XAML 2006 a WPF  
 Pro použití XAML 2006 a XAML, které se používají pro aplikace WPF, existují následující omezení pro `x:TypeArguments` a obecné typy použití z XAML obecně:  
  
- Pouze kořenový prvek souboru XAML může podporovat obecné použití XAML, které odkazuje na obecný typ.  
  
- Kořenový element musí být namapován na obecný typ s alespoň jedním argumentem typu. Příklad: <xref:System.Windows.Navigation.PageFunction%601>. Funkce stránky jsou primární scénář pro podporu obecného použití XAML v jazyce WPF.  
  
- Element objektu XAML kořenového elementu pro obecný musí také deklarovat částečnou třídu pomocí `x:Class`. To platí i v případě, že definujete akci sestavení WPF.  
  
- `x:TypeArguments` nemůže odkazovat na vnořená obecná omezení.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 nebo XAML 2006 bez závislosti WPF 3,0 nebo WPF 3,5  
 V jazyce .NET Framework XAML pro XAML 2006 nebo XAML 2009 jsou omezení související s WPF pro obecné použití XAML uvolněna. Můžete vytvořit instanci obecného prvku objektu na libovolné pozici v kódu XAML, který může podporovat systém back-Type a objektový model.  
  
 Použijete-li XAML 2009 namísto mapování základních typů CLR pro získání typů XAML pro společné jazykové primitivy, můžete použít [vestavěné typy pro běžné primitivní prvky jazyka XAML](built-in-types-for-common-xaml-language-primitives.md) jako informační položky v `typeString`. Například můžete deklarovat následující (mapování předpon není zobrazeno, ale x je obor názvů XAML jazyka XAML pro XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 V jazyce WPF a při cílení na .NET Framework 4 můžete použít funkce XAML 2009 společně s `x:TypeArguments`, ale pouze pro volné XAML (XAML bez kódu kompilováno). XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009. Pokud potřebujete kód zkompilovat do kódu XAML, je nutné pracovat s omezeními v části "XAML 2006 and WPF Generic XAML".  
  
## <a name="see-also"></a>Viz také:

- [x:Class – direktiva](x-class-directive.md)
- [x:Type – rozšíření značek](x-type-markup-extension.md)
- [Předdefinované typy obecných primitiv jazyka XAML](built-in-types-for-common-xaml-language-primitives.md)
- [Obecné typy v jazyku XAML](generics-in-xaml.md)
