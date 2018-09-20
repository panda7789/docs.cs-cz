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
ms.openlocfilehash: 28eda94914125f2c5849a471671c8e283475c82c
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46321389"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments – direktiva
Předá omezení argumentů obecného konstruktoru obecného typu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`object`|Deklarace elementu objektu XAML typu, který se zálohuje pomocí obecného typu CLR. Pokud `object` odkazuje na typ XAML, který nepochází od výchozí obor názvů XAML, `object` vyžaduje předpona k označení oboru názvů XAML kde `object` existuje.|  
|`typeString`|Řetězec, který deklaruje nejmíň jeden XAML zadejte názvy jako řetězce, který poskytuje argumentů typu pro obecný typ CLR. Viz poznámky pro další syntaxe poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 Ve většině případů XAML typy, které se používají jako položka informace `typeString` mají předponu řetězec. Obvyklé typy CLR obecná omezení (například <xref:System.Int32> a <xref:System.String>) pocházejí z knihovny základních tříd CLR. Tyto knihovny nejsou namapované na typické výchozí specifické pro architekturu obory názvů XAML a proto vyžadovat mapování předpony pro využití XAML.  
  
 S použitím oddělovače čárky můžete zadat více než jeden název typu XAML.  
  
 Obecná omezení sami použití obecných typů, typů argumentů vnořené omezení může být obsažený ve závorky ().  
  
 Všimněte si, že tato definice `x:TypeArguments` je specifická pro rozhraní .NET Framework XAML Services a pomocí CLR zálohování. Definice úrovni jazyka najdete v [ \[MS-XAML\] části 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Příklady použití  
 Tyto příklady předpokládají, že jsou deklarovány následující definice oboru názvů XAML:  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Seznam\<řetězec >  
 `<scg:List x:TypeArguments="sys:String" ...>` Vytvoří novou instanci <xref:System.Collections.Generic.List%601> s <xref:System.String> argument typu.  
  
### <a name="dictionarystringstring"></a>Slovník\<String, String >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` Vytvoří novou instanci <xref:System.Collections.Generic.Dictionary%602> se dvěma <xref:System.String> argumenty typu.  
  
### <a name="queuekeyvaluepairstringstring"></a>Fronty < nenašla\<String, String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` Vytvoří novou instanci <xref:System.Collections.Generic.Queue%601> , který má omezení <xref:System.Collections.Generic.KeyValuePair%602> s argumenty typu vnitřní omezení, které <xref:System.String> a <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 a WPF XAML obecné použití  
 Pro použití XAML 2006 a XAML, který se používá pro aplikace WPF, existují následující omezení pro `x:TypeArguments` a použití obecného typu z XAML v obecné:  
  
-   Kořenový element souboru XAML může podporovat obecný využití XAML, který odkazuje na obecném typu.  
  
-   Kořenový element musí být namapovaný na obecný typ s alespoň jeden argument typu. Příkladem je <xref:System.Windows.Navigation.PageFunction%601>. Funkce stránky jsou primární scénáře pro podporu obecných využití XAML v subsystému WPF.  
  
-   Kořenový prvek XAML objekt elementu obecné musí také deklarovat částečné třídy pomocí `x:Class`. To platí i v případě, že definice WPF akci sestavení.  
  
-   `x:TypeArguments` nemůže odkazovat na vnořených obecná omezení.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 nebo XAML 2006 bez WPF 3.0 nebo WPF 3.5 závislostí  
 V rozhraní .NET Framework XAML Services pro XAML 2006 nebo XAML 2009 jsou mírnější omezení související s WPF v použití obecného XAML. Generický objekt elementu v jakékoliv pozici v kódu XAML, které podporují základní typ systému a objekt modelu lze vytvořit instanci.  
  
 Pokud používáte XAML 2009 místo mapování CLR základní typy získat primitiv jazyka XAML typy, můžete použít [předdefinované typy obecných primitiv jazyka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) jako informačních položek v `typeString`. Například můžete deklarovat následující (mapování předpon, které nejsou uvedené, ale x je obor názvů jazyka XAML XAML pro XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 V grafickém subsystému WPF a při cílení na [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], je možné použít funkce XAML 2009 spolu s `x:TypeArguments` , ale pouze pro volný XAML (XAML, který není kompilována značka). Kompilována značka XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova XAML 2009 a funkce. Pokud třeba do kódu kompilaci XAML, musí pracovat v rámci omezení, které jste si poznamenali v části "XAML 2006 a WPF obecný XAML použití".  
  
## <a name="see-also"></a>Viz také  
 [x:Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md)  
 [x:Type – rozšíření značek](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Předdefinované typy obecných primitiv jazyka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [Obecné typy v jazyku XAML](../../../docs/framework/xaml-services/generics-in-xaml.md)
