---
title: Předdefinované typy obecných primitiv jazyka XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: 85fd0c04a40b9de64979e4da1459dbf8953a93bf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053883"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Předdefinované typy obecných primitiv jazyka XAML
XAML 2009 zavádí podporu na úrovni jazyka XAML pro několik datových typů, které jsou často používány primitivními prvky v modulu CLR (Common Language Runtime) a v jiných programovacích jazycích. XAML 2009 přidává podporu pro tyto primitivní prvky: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, ,`x:TimeSpan` `x:Uri`, a`x:Byte``x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Předchozí techniky pro jazykové primitivy v kódu XAML  
 V jazyce XAML pro předchozí verze WPF můžete odkazovat na primitivní prvky jazyka CLR mapováním sestavení a oboru názvů, který obsahoval třídu primitivní definice CLR pro .NET Framework. Většina z nich je v sestavení a <xref:System> oboru názvů mscorlib. Například chcete-li použít <xref:System.Int32>, můžete deklarovat následující mapování (s příkladem použití zobrazeného po):  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>Primitiva jazyka XAML 2009  
 Podle konvence se zobrazí primitivní jazyky pro XAML a všechny ostatní prvky jazyka XAML, včetně `x:` předpony. Toto je způsob, jakým jsou obvykle použity prvky jazyka XAML ve značkách reálného světa. Tato konvence je následována v Koncepční dokumentaci pro jazyk XAML v subsystému WPF a také ve specifikaci jazyka XAML.  
  
### <a name="xobject"></a>x:Object  
 Pro zálohování `x:Object` CLR primitiva odpovídá <xref:System.Object>.  
  
 Tento primitivní kód se obvykle nepoužívá v kódu aplikace, ale může být užitečný pro některé scénáře, jako je například kontrola přiřazení v systému typů XAML.  
  
### <a name="xboolean"></a>x:Boolean  
 Pro zálohování `x:Boolean` CLR primitiva odpovídá <xref:System.Boolean>.  
  
 XAML analyzuje hodnoty pro `x:Boolean` nerozlišování velkých a malých písmen. Všimněte si `x:Bool` , že se nejedná o přijatou alternativu. Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.17 a 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x:Char  
 Pro zálohování `x:Char` CLR primitiva odpovídá <xref:System.Char>.  
  
 Typy řetězců a znaků mají v interakci s celkovým kódováním souboru na úrovni XML. Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.7 a 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x:String  
 Pro zálohování `x:String` CLR primitiva odpovídá <xref:System.String>.  
  
 Typy řetězců a znaků mají v interakci s celkovým kódováním souboru na úrovni XML. Definice specifikace jazyka XAML naleznete v [ \[části MS-\] XAML 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x:Decimal  
 Pro zálohování `x:Decimal` CLR primitiva odpovídá <xref:System.Decimal>.  
  
 Všimněte si, že analýza XAML je v podstatě provedena v rámci `en-US` kultury. V `en-US` rámci jazykové verze je správný oddělovač pro součásti desetinné čárky vždy tečka (`.`) bez ohledu na nastavení jazykové verze vývojového prostředí nebo na konečném cíli klienta, kde je XAML načten v době běhu.  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.14 a 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x:Single  
 Pro zálohování `x:Single` CLR primitiva odpovídá <xref:System.Single>.  
  
 Kromě `x:Single` číselných hodnot, syntaxe textu pro také povoluje tokeny `Infinity`, `-Infinity`a `NaN`. Tyto tokeny se považují za rozlišuje velká a malá písmena.  
  
 `x:Single`může podporovat hodnoty ve formě vědeckého zápisu, pokud je `e` první znak v syntaxi textu nebo. `E`  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.8 a 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x:Double  
 Pro zálohování `x:Double` CLR primitiva odpovídá <xref:System.Double>.  
  
 Kromě číselných hodnot, syntaxe `x:Double` textu pro povoluje tokeny `Infinity`, `-Infinity`a `NaN`. Tyto tokeny se považují za rozlišuje velká a malá písmena.  
  
 `x:Double`může podporovat hodnoty ve formě vědeckého zápisu. Použijte znak `e` nebo `E` k představení části exponentu.  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.9 a 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x:Int16  
 V `x:Int16` případě zálohování CLR primitiva odpovídá <xref:System.Int16> a `x:Int16` je považována za signed. V jazyce XAML není absence znaku plus (`+`) v syntaxi textu odvozena jako kladná podepsaná hodnota.  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.11 a 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x:Int32  
 Pro zálohování `x:Int32` CLR primitiva odpovídá <xref:System.Int32>. `x:Int32`je považován za podepsaný. V jazyce XAML není absence znaku plus (`+`) v syntaxi textu odvozena jako kladná podepsaná hodnota.  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.12 a 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x:Int64  
 Pro zálohování `x:Int64` CLR primitiva odpovídá <xref:System.Int64>. `x:Int64`je považován za podepsaný. V jazyce XAML není absence znaku plus (`+`) v syntaxi textu odvozena jako kladná podepsaná hodnota.  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.13 a 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x:TimeSpan  
 Pro zálohování `x:TimeSpan` CLR primitiva odpovídá <xref:System.TimeSpan>.  
  
 Analýza jazyka XAML pro formát data a času je v podstatě provedena v rámci `en-US` kultury.  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.16 a 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x:Uri  
 Pro zálohování `x:Uri` CLR primitiva odpovídá <xref:System.Uri>.  
  
 Kontrola protokolů není součástí definice XAML pro `x:Uri`.  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.15 a 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x:Byte  
 Pro zálohování `x:Byte` CLR primitiva odpovídá <xref:System.Byte>. Jepovažovánzanepodepsaný<xref:System.Byte>.  /  `x:Byte`  
  
 Definice specifikace jazyka XAML naleznete v [ \[částech MS-\] XAML 5.2.10 a 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x:Array  
 Pro zálohování `x:Array` CLR primitiva odpovídá <xref:System.Array>.  
  
 Pole v jazyce XAML 2006 můžete definovat pomocí syntaxe rozšíření značek; Syntaxe XAML 2009 však je jazykově definovaná primitiva, která nevyžaduje přístup k rozšíření značek. Další informace o podpoře XAML 2006 naleznete v tématu [X:Array Markup Extension](x-array-markup-extension.md).  
  
 Definice specifikace jazyka XAML naleznete v [ \[části MS-\] XAML 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Podpora WPF  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, které nejsou kompilovány pomocí značek. XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.  
  
 Scénář, ve kterém můžete použít funkce XAML 2009 společně s WPF, je, pokud vytvoříte volný kód XAML a potom tento kód XAML nahrajete do modulu runtime WPF <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>a grafu objektů pomocí. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a jeho <xref:System.Windows.Markup.XamlReader.Load%2A> aplikace mohou zpracovat klíčová slova a funkce jazyka XAML 2009 do platného reprezentace grafu objektu.
