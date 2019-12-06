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
ms.openlocfilehash: c6af46fe2ea21d081e693ee83949651bd388a045
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837269"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Předdefinované typy obecných primitiv jazyka XAML
XAML 2009 zavádí podporu na úrovni jazyka XAML pro několik datových typů, které jsou často používány primitivními prvky v modulu CLR (Common Language Runtime) a v jiných programovacích jazycích. XAML 2009 přidává podporu pro tyto primitivní prvky: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`a `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Předchozí postupy pro primitivní prvky pro značky XAML  
 V jazyce XAML pro předchozí verze WPF může odkazovat základní prvky jazyka CLR mapováním sestavení a oboru názvů, který obsahuje třídy definice základních prvků CLR pro .NET Framework. Většina z nich jsou v sestavení mscorlib a oboru názvů <xref:System>. Můžete například použít <xref:System.Int32>, můžete deklarovat následující mapování (s následně zobrazeným příkladem použití):  
  
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
## <a name="xaml-2009-language-primitives"></a>XAML 2009 Language Primitives  
 Podle konvence jsou zobrazeny základy jazyka XAML a všechny ostatní prvky jazyka XAML, včetně předpony `x:`. Tímto způsobem se běžně používají elementy jazyka XAML ve značkách reálného světa. Tato konvence je uvedena v rámcové dokumentaci pro XAML ve WPF a také ve specifikaci jazyka XAML.  
  
### <a name="xobject"></a>x:Objekt  
 Pro CLR zálohování primitiva `x:Object` odpovídá <xref:System.Object>.  
  
 Tato primitiva se obvykle nepoužívá ve značce aplikace, ale může být užitečná pro některé scénáře, jako je například kontrola přiřaditelnosti v typu systému XAML.  
  
### <a name="xboolean"></a>x:Boolean  
 Pro CLR zálohování primitiva `x:Boolean` odpovídá <xref:System.Boolean>.  
  
 XAML analyzuje hodnoty pro `x:Boolean` bez rozlišení písma. Všimněte si, že `x:Bool` není přijatou alternativu. Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.17 a 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xchar"></a>x:Char  
 Pro CLR zálohování primitiva `x:Char` odpovídá <xref:System.Char>.  
  
 Typy řetězce a znaku provádí interakci s celkovým kódováním souboru na úrovni XML. Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.7 a 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xstring"></a>x:Řetězec  
 Pro CLR zálohování primitiva `x:String` odpovídá <xref:System.String>.  
  
 Typy řetězce a znaku provádí interakci s celkovým kódováním souboru na úrovni XML. Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xdecimal"></a>x:Desetinné číslo  
 Pro CLR zálohování primitiva `x:Decimal` odpovídá <xref:System.Decimal>.  
  
 Všimněte si, že analýza XAML je ze své podstaty provedená v jazykové kultuře `en-US`. V části jazyková verze `en-US` je správný oddělovač pro součásti desetinného čísla vždy tečka (`.`) bez ohledu na nastavení jazykové verze vývojového prostředí nebo případného cíle klienta, kde XAML je načten v době běhu.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.14 a 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xsingle"></a>x:Jednoduché  
 Pro CLR zálohování primitiva `x:Single` odpovídá <xref:System.Single>.  
  
 Kromě číselných hodnot, textová syntaxe pro `x:Single` také umožňuje tokeny `Infinity`, `-Infinity` a `NaN`. Tyto tokeny jsou zpracovány s rozlišováním malých a velkých písmen.  
  
 `x:Single` podporuje hodnoty ve formátu matematického zápisu, pokud je první znak v textu syntaxe `e` nebo `E`.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.8 a 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xdouble"></a>x:Double  
 Pro CLR zálohování primitiva `x:Double` odpovídá <xref:System.Double>.  
  
 Kromě číselných hodnot, textová syntaxe pro `x:Double` umožňuje tokeny `Infinity`, `-Infinity` a `NaN`. Tyto tokeny jsou zpracovány s rozlišováním malých a velkých písmen.  
  
 `x:Double` může podporovat hodnoty ve formuláři pro matematický zápis. Znak `e` nebo `E` použijte k zavedení části exponentu.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.9 a 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint16"></a>x:Int16  
 Pro zálohování CLR základ `x:Int16` odpovídající <xref:System.Int16> a `x:Int16` je považován za podepsaný. V jazyce XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.11 a 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint32"></a>x:Int32  
 Pro CLR zálohování primitiva `x:Int32` odpovídá <xref:System.Int32>. `x:Int32` je považován za se znaménkem. V jazyce XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.12 a 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint64"></a>x:Int64  
 Pro CLR zálohování primitiva `x:Int64` odpovídá <xref:System.Int64>. `x:Int64` je považován za se znaménkem. V jazyce XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.13 a 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xtimespan"></a>x:TimeSpan  
 Pro CLR zálohování primitiva `x:TimeSpan` odpovídá <xref:System.TimeSpan>.  
  
 Všimněte si, že analýza XAML pro formát data a času je ze své podstaty provedená v jazykové kultuře `en-US`.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.16 a 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xuri"></a>x:Uri  
 Pro CLR zálohování primitiva `x:Uri` odpovídá <xref:System.Uri>.  
  
 Kontrola protokolů není součástí definice XAML pro `x:Uri`.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.15 a 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xbyte"></a>x:Byte  
 Pro CLR zálohování primitiva `x:Byte` odpovídá <xref:System.Byte>. <xref:System.Byte> / `x:Byte` se považuje za nepodepsaný.  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.10 a 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xarray"></a>x:Pole  
 Pro CLR zálohování primitiva `x:Array` odpovídá <xref:System.Array>.  
  
 Pole v jazyce XAML 2006 můžete definovat pomocí syntaxe rozšíření značek; Syntaxe XAML 2009 však je jazykově definovaná primitiva, která nevyžaduje přístup k rozšíření značek. Další informace o podpoře XAML 2006 naleznete v tématu [X:Array Markup Extension](x-array-markup-extension.md).  
  
 Definice specifikace jazyka XAML naleznete v tématu [\[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Podpora WPF  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, které nejsou kompilovány pomocí značek. XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.  
  
 Scénář, ve kterém můžete použít funkce XAML 2009 společně s WPF, je, pokud vytvoříte volný kód XAML a potom tento XAML navedete do modulu runtime WPF a grafu objektů pomocí <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a její <xref:System.Windows.Markup.XamlReader.Load%2A> mohou zpracovat klíčová slova a funkce jazyka XAML 2009 do platného reprezentace grafu objektu.
