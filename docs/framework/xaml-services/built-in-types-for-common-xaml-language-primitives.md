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
ms.openlocfilehash: f6225dfcc02b90da58ccafd5c70726b6f80f29d4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252165"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Předdefinované typy obecných primitiv jazyka XAML
XAML 2009 zavádí podporu na úrovni jazyka XAML pro několik typů dat, které jsou často používají primitivy v modulu common language runtime (CLR) a v jiných programovacích jazycích. XAML 2009 dodává podporu těchto primitivních hodnot: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, a `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Předchozí postupy pro primitivní v kódu XAML  
 V XAML pro předchozí verze WPF může odkazovat základní prvky jazyka CLR mapováním sestavení a oboru názvů, který obsahoval definice třídy CLR rozhraní .NET Framework. Většina z nich jsou v sestavení mscorlib a <xref:System> oboru názvů. Chcete-li například použít <xref:System.Int32>, můžete deklarovat následující mapování (s zobrazeným Příkladem použití):  
  
```  
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
 Podle konvence jsou zobrazeny základy jazyka XAML a všechny ostatní prvky jazyka XAML, včetně `x:` předponu. To je, jak se běžně používají elementy jazyka XAML ve značkách reálného světa. Tato konvence je uvedena v rámcové dokumentaci pro XAML v subsystému WPF a také ve specifikaci XAML.  
  
### <a name="xobject"></a>x: objekt  
 Pro zálohování CLR `x:Object` primitivní odpovídá <xref:System.Object>.  
  
 Tato primitiva se obvykle nepoužívá ve značce aplikace, ale může být užitečná pro některé scénáře, jako je například kontrola přiřaditelnosti v typu systému XAML.  
  
### <a name="xboolean"></a>x: Boolean  
 Pro zálohování CLR `x:Boolean` primitivní odpovídá <xref:System.Boolean>.  
  
 XAML analyzuje hodnoty pro `x:Boolean` jako malá a velká písmena. Všimněte si, že `x:Bool` není přijatou alternativu. Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.17 a 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x: Char  
 Pro zálohování CLR `x:Char` primitivní odpovídá <xref:System.Char>.  
  
 Máte typy řetězce a znaku provádí interakci s celkovým kódováním souboru na úrovni XML. Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.7 a 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x: String  
 Pro zálohování CLR `x:String` primitivní odpovídá <xref:System.String>.  
  
 Máte typy řetězce a znaku provádí interakci s celkovým kódováním souboru na úrovni XML. Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x: Decimal  
 Pro zálohování CLR `x:Decimal` primitivní odpovídá <xref:System.Decimal>.  
  
 Všimněte si, že analýza XAML je ze své podstaty provedená v `en-US` jazykovou verzi. V části `en-US` jazykovou verzi, je správný oddělovač pro součásti desetinného čísla vždy tečka (`.`) bez ohledu na nastavení jazykové verze vývojového prostředí nebo případného cíle klienta kde XAML je načten v době běhu.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.14 a 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x: jeden  
 Pro zálohování CLR `x:Single` primitivní odpovídá <xref:System.Single>.  
  
 Kromě číselných hodnot, textová syntaxe pro `x:Single` také umožňuje tokeny `Infinity`, `-Infinity`, a `NaN`. Tyto tokeny jsou zpracovány jako malá a velká písmena.  
  
 `x:Single` podporuje hodnoty ve formuláři pro matematický zápis, pokud je první znak v textu syntaxe `e` nebo `E`.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.8 a 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x: Double  
 Pro zálohování CLR `x:Double` primitivní odpovídá <xref:System.Double>.  
  
 Kromě číselných hodnot, textová syntaxe pro `x:Double` umožňuje tokeny `Infinity`, `-Infinity`, a `NaN`. Tyto tokeny jsou zpracovány jako malá a velká písmena.  
  
 `x:Double` může podporovat hodnoty ve formuláři pro matematický zápis. Použít znak `e` nebo `E` k zavedení části exponentu.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.9 a 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x: Int16  
 Pro zálohování CLR `x:Int16` primitivní odpovídá <xref:System.Int16> a `x:Int16` je považován za podepsaný. V XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.11 a 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x: Int32  
 Pro zálohování CLR `x:Int32` primitivní odpovídá <xref:System.Int32>. `x:Int32` je považován za podepsaný. V XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.12 a 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x: Int64  
 Pro zálohování CLR `x:Int64` primitivní odpovídá <xref:System.Int64>. `x:Int64` je považován za podepsaný. V XAML, neexistence znaku plus (`+`) v syntaxi textu je vyjádřena jako kladná hodnota se znaménkem.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.13 a 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x: časový interval  
 Pro zálohování CLR `x:TimeSpan` primitivní odpovídá <xref:System.TimeSpan>.  
  
 Upozorňujeme, že analýza XAML pro formát data a času je ze své podstaty provedená v `en-US` jazykovou verzi.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.16 a 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x: identifikátor Uri  
 Pro zálohování CLR `x:Uri` primitivní odpovídá <xref:System.Uri>.  
  
 Kontrola protokolů není součástí definice XAML pro `x:Uri`.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.15 a 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x: bajtů  
 Pro zálohování CLR `x:Byte` primitivní odpovídá <xref:System.Byte>. A <xref:System.Byte>  /  `x:Byte` považuje za bez znaménka.  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.10 a 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x: Array  
 Pro zálohování CLR `x:Array` primitivní odpovídá <xref:System.Array>.  
  
 V XAML 2006 můžete definovat pole pomocí syntaxe rozšíření značek; Syntaxe XAML 2009 je však jazykově definovaná primitivní, která nevyžaduje přístup k rozšíření značek. Další informace o podpoře XAML 2006 najdete v tématu [x: Array – rozšíření značek](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 Definice specifikace jazyka XAML, naleznete v tématu [ \[MS-XAML\] části 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Podpora WPF  
 V WPF můžete použít funkce XAML 2009 ale pouze pro XAML, který není kompilována značka. Kompilována značka XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova XAML 2009 a funkce.  
  
 Scénář, kde je možné použít funkce XAML 2009 spolu s WPF je, pokud vytvoříte volný XAML a pak načíst tento XAML do WPF runtime a grafu objektu s <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a jeho <xref:System.Windows.Markup.XamlReader.Load%2A> mohou zpracovávat klíčová slova jazyka XAML 2009 a funkce do platnou reprezentaci grafu objektů.
