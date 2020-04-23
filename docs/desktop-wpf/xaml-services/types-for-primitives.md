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
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071834"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Předdefinované typy pro běžné jazykové primitivy XAML

XAML 2009 zavádí podporu na jazykové úrovni XAML pro několik datových typů, které se často používají primitiva v cltime společného jazyka (CLR) a v jiných programovacích jazycích. XAML 2009 přidává podporu pro `x:Object` `x:Boolean`tyto `x:Char` `x:String`primitiva: , , , `x:Decimal` `x:Single` `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, , a`x:Array`

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Předchozí techniky pro jazykové primitivy v přeznačce XAML

 V jazyce XAML pro předchozí verze WPF můžete odkazovat na základní jazykCLR mapováním sestavení a oboru názvů, které obsahovaly třídu primitivní definice CLR pro rozhraní .NET Framework. Většina z nich jsou v sestavení <xref:System> mscorlib a oboru názvů. Chcete-li například použít <xref:System.Int32>, můžete deklarovat následující mapování (s příklad použití je uvedeno poté):

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a>Jazyková primitiva XAML 2009

Podle konvence jsou zobrazeny jazykové primitivy pro XAML a `x:` všechny ostatní prvky jazyka XAML, včetně předpony. To je, jak xAML prvky jazyka se obvykle používají v reálném světě značky. Tato konvence je dodržována v koncepční dokumentaci pro XAML v WPF a také ve specifikaci XAML.

### <a name="xobject"></a>x:Objekt

Pro podporu CLR `x:Object` primitivní odpovídá <xref:System.Object>.

Tento primitiv se obvykle nepoužívá v aplikaci značky, ale může být užitečné pro některé scénáře, jako je například kontrola přiřaditelnostva v systému typu XAML.

### <a name="xboolean"></a>x:Logická hodnota

Pro podporu CLR `x:Boolean` primitivní odpovídá <xref:System.Boolean>.

XAML analyzuje hodnoty `x:Boolean` jako malá a velká písmena. Všimněte `x:Bool` si, že není přijatou alternativou. Definice specifikace jazyka XAML viz [ \[oddíly 5.2.17 a 5.4.11 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xchar"></a>x:Znak

Pro podporu CLR `x:Char` primitivní odpovídá <xref:System.Char>.

Typy řetězců a znaků mají interakci s celkovým kódováním souboru na úrovni XML. Definice specifikace jazyka XAML viz [ \[oddíly 5.2.7 a 5.4.1 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xstring"></a>x:Řetězec

Pro podporu CLR `x:String` primitivní odpovídá <xref:System.String>.

Typy řetězců a znaků mají interakci s celkovým kódováním souboru na úrovni XML. Definice specifikace jazyka XAML naleznete [ \[v oddílech\] 5.2.6 jazyka MS-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdecimal"></a>x:Desetinné místo

Pro podporu CLR `x:Decimal` primitivní odpovídá <xref:System.Decimal>.

Analýza XAML se neodmyslitelně provádí v rámci `en-US` kultury. V `en-US` rámci jazykové verze je správný oddělovač pro součásti`.`desetinného místa vždy tečkou ( ) bez ohledu na nastavení jazykové verze vývojového prostředí nebo na případný cíl klienta, kde je xaml načten za běhu.

Definice specifikace jazyka XAML viz [ \[oddíly 5.2.14 a 5.4.8\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xsingle"></a>x:Jednoduché

Pro podporu CLR `x:Single` primitivní odpovídá <xref:System.Single>.

Kromě číselných hodnot umožňuje syntaxe `x:Single` textu také `Infinity` `-Infinity`tokeny `NaN`, a . Tyto tokeny jsou považovány za malá a velká písmena.

`x:Single`může podporovat hodnoty ve formuláři vědeckého zápisu, `e` `E`pokud je první znak v syntaxi textu nebo .

Definice specifikace jazyka XAML viz [ \[oddíly 5.2.8 a 5.4.2 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdouble"></a>x:Dvojitá

Pro podporu CLR `x:Double` primitivní odpovídá <xref:System.Double>.

Kromě číselných hodnot umožňuje syntaxi textu `Infinity`pro `-Infinity` `x:Double` tokeny , a `NaN`. Tyto tokeny jsou považovány za malá a velká písmena.

`x:Double`mohou podporovat hodnoty ve vědecké notační formě. Použijte znak `e` `E` nebo zavést exponenciální část.

Definice specifikace jazyka XAML viz [ \[oddíly 5.2.9 a 5.4.3 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint16"></a>x:Int16

Pro podporu CLR `x:Int16` primitivární odpovídá <xref:System.Int16> a `x:Int16` je považován za podepsané. V XAML je absence syntaxe textu přihlášení plus (`+`) implikována jako kladná podepsaná hodnota.

Definice specifikace jazyka XAML viz [ \[oddíly 5.2.11 a 5.4.5\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint32"></a>x:Int32

Pro podporu CLR `x:Int32` primitivní odpovídá <xref:System.Int32>. `x:Int32`považována za podepsanou. V XAML je absence syntaxe textu přihlášení plus (`+`) implikována jako kladná podepsaná hodnota.

Definice specifikace jazyka XAML viz [ \[oddíly 5.2.12 a 5.4.6\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint64"></a>x:Int64

Pro podporu CLR `x:Int64` primitivní odpovídá <xref:System.Int64>. `x:Int64`považována za podepsanou. V XAML je absence syntaxe textu přihlášení plus (`+`) implikována jako kladná podepsaná hodnota.

Definice specifikace jazyka XAML viz [ \[oddíly 5.2.13 a 5.4.7\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xtimespan"></a>x:Časový posun

Pro podporu CLR `x:TimeSpan` primitivní odpovídá <xref:System.TimeSpan>.

Analýza XAML pro formát časového data se `en-US` neodmyslitelně provádí v rámci jazykové verze.

Definice specifikace jazyka XAML naleznete [ \[v oddílech\] 5.2.16 a 5.4.10 ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xuri"></a>x:Uri

Pro podporu CLR `x:Uri` primitivní odpovídá <xref:System.Uri>.

Kontrola protokolů není součástí definice XAML `x:Uri`pro .

Definice specifikace jazyka XAML viz [ \[oddíly 5.2.15 a 5.4.9\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xbyte"></a>x:Bajt

Pro podporu CLR `x:Byte` primitivní odpovídá <xref:System.Byte>. <xref:System.Byte>  /  A `x:Byte` je považován za nepodepsané.

Definice specifikace jazyka XAML viz [ \[oddíly 5.2.10 a 5.4.4\] ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xarray"></a>x:Pole

Pro podporu CLR `x:Array` primitivní odpovídá <xref:System.Array>.

Pole v xaml 2006 můžete definovat pomocí syntaxe rozšíření značek; Syntaxe XAML 2009 je však jazykově definované primitivum, které nevyžaduje přístup k rozšíření značek. Další informace o podpoře XAML 2006 naleznete v [tématu x:Array Markup Extension](xarray-markup-extension.md).

Definice specifikace jazyka XAML naleznete [ \[v oddílech\] 5.2.18 jazyka MS-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="wpf-support"></a>Podpora WPF

V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není zkompilován značkami. XAML kompilované značkami pro WPF a formu BAML XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.

Scénář, kde můžete použít funkce XAML 2009 spolu s WPF je, pokud autor volné XAML a potom <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>načíst, že XAML do wpf runtime a objektový graf s . WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a <xref:System.Windows.Markup.XamlReader.Load%2A> jeho může zpracovat XAML 2009 jazyk klíčová slova a funkce do platného objektu grafu reprezentace.
