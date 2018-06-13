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
ms.openlocfilehash: 94f09bdd3b6ee0b180e30bab0993f0b4e41730ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566857"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments – direktiva
Předává chovaly zadejte argumenty obecného do konstruktoru objektu obecného typu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`object`|Deklarace objektu elementu XAML typu, který je zálohovaný díky obecného typu CLR. Pokud `object` odkazuje na typ jazyka XAML, který není z oboru názvů jazyka XAML výchozí `object` vyžaduje předpony oboru názvů jazyka XAML znamenat kde `object` existuje.|  
|`typeString`|Řetězec, který deklaruje jednu nebo více XAML zadejte názvy jako řetězce, který poskytuje argumenty typu pro obecný typ CLR. Poznámky k další syntaxi najdete v části poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 Ve většině případů XAML typy, které se používají jako položka informace `typeString` jsou předponu řetězec. Typické typy CLR obecná omezení (například <xref:System.Int32> a <xref:System.String>) pochází z knihovny základní třídy CLR. Tyto knihovny nejsou obory názvů jazyka XAML namapován na typické výchozí konkrétní rozhraní a proto vyžadovat mapování předpony pro použití XAML.  
  
 Můžete zadat více než jeden název typu XAML použitím oddělovače čárkami.  
  
 Pokud obecná omezení sami použít obecné typy, argumenty typu vnořené omezení může být obsažený ve závorky ().  
  
 Všimněte si, že tato definice `x:TypeArguments` je specifický pro rozhraní .NET Framework XAML Services a pomocí zálohování CLR. Definice úroveň jazyka najdete v [ \[MS-XAML\] části 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Příklady použití  
 Tyto příklady předpokládejme, že jsou deklarovány následující definice oboru názvů jazyka XAML:  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Seznam\<řetězec >  
 `<scg:List x:TypeArguments="sys:String" ...>` Vytvoří nový <xref:System.Collections.Generic.List%601> s <xref:System.String> argument typu.  
  
### <a name="dictionarystringstring"></a>Slovník\<řetězec, řetězec >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` Vytvoří nový <xref:System.Collections.Generic.Dictionary%602> se dvěma <xref:System.String> argumenty typů.  
  
### <a name="queuekeyvaluepairstringstring"></a>Fronty < KeyValuePair\<řetězec, řetězec >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` Vytvoří nový <xref:System.Collections.Generic.Queue%601> s omezením na <xref:System.Collections.Generic.KeyValuePair%602> s argumenty typu vnitřní omezení <xref:System.String> a <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>Použití obecné XAML XAML 2006 a WPF  
 Pro použití XAML 2006 a XAML, který se používá pro aplikace WPF, existují následující omezení `x:TypeArguments` a použití obecného typu z XAML v obecné:  
  
-   Kořenový element souboru XAML může podporovat použití obecné XAML, který odkazuje na obecného typu.  
  
-   Kořenový element musí být mapována obecného typu pomocí alespoň jeden typ argumentu. Příkladem je <xref:System.Windows.Navigation.PageFunction%601>. Stránka funkce jsou primární scénář pro obecné použití podporu XAML v grafickém subsystému WPF.  
  
-   Element object kořenový element XAML pro obecné musí také deklarovat třídu pomocí `x:Class`. To platí i v případě, že definování WPF akce sestavení.  
  
-   `x:TypeArguments` nemůže odkazovat na vnořené obecná omezení.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 nebo XAML 2006 bez grafického subsystému WPF 3.0 nebo WPF 3.5 závislostí  
 V rozhraní .NET Framework XAML Services pro XAML 2006 nebo XAML 2009 jsou mírnější omezení týkající se subsystému WPF pro obecné použití XAML. Můžete vytvořit instanci obecné objekt elementu všechny pozice v jazyce XAML kódu, které může podporovat základní typ systému a objekt modelu.  
  
 Pokud používáte XAML 2009 místo mapování modulu CLR základní typy získat běžné primitiv jazyka XAML typy, můžete použít [předdefinované typy obecných primitiv jazyka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) jako položky informace v `typeString`. Je třeba deklarovat následující (mapování předpony není vidět, ale x je obor názvů jazyka XAML XAML pro XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 V grafickém subsystému WPF a pokud je cílem [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít funkce jazyka XAML 2009 společně s `x:TypeArguments` , ale pouze u přijít XAML (XAML, který zkompiluje značek není). Zkompilovaný kód XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce. Pokud třeba chcete značek zkompilujete XAML, musí pracovat v rámci omezení uvedených v části "XAML 2006 a WPF obecného XAML použití".  
  
## <a name="see-also"></a>Viz také  
 [x:Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md)  
 [x:Type – rozšíření značek](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Předdefinované typy obecných primitiv jazyka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [Obecné typy v jazyku XAML](../../../docs/framework/xaml-services/generics-in-xaml.md)
