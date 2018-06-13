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
ms.openlocfilehash: 15c359a9a7f9797fc03ce20c453905af01f925d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564349"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Předdefinované typy obecných primitiv jazyka XAML
XAML 2009 zavádí podporu úroveň jazyka XAML pro několik typů dat, které jsou často používané základní prvky v common language runtime (CLR) a ostatní programovací jazyky. Přidává podporu pro tyto primitiv jazyka XAML 2009: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, a `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Předchozí techniky pro primitiva jazyka XAML značek  
 V jazyce XAML pro předchozí verze WPF může odkazovat primitiv jazyka CLR tak, že mapuje sestavení a obor názvů, který obsažené primitivní definice třídy CLR pro rozhraní .NET Framework. Většina z nich jsou v sestavení mscorlib a <xref:System> oboru názvů. Chcete-li například použít <xref:System.Int32>, může deklarovat následující mapování (s příklady použití, zobrazí po tomto datu):  
  
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
 Podle konvence, jsou zobrazeny primitiv jazyka XAML a všechny další elementy jazyka XAML, včetně `x:` předponu. Toto je, jak jsou obvykle používány elementů jazyka XAML v reálných značek. Touto konvencí je následovaný v rámcová dokumentace pro jazyk XAML v grafickém subsystému WPF a také ve specifikaci XAML.  
  
### <a name="xobject"></a>x: objekt  
 Pro zálohování CLR `x:Object` primitivní odpovídá <xref:System.Object>.  
  
 Tato primitivní není obvykle se používá v kódu aplikace, ale mohou být užitečné pro některé scénáře, jako je kontrola assignability typ systému XAML.  
  
### <a name="xboolean"></a>x: logická hodnota  
 Pro zálohování CLR `x:Boolean` primitivní odpovídá <xref:System.Boolean>.  
  
 XAML analyzuje hodnoty pro `x:Boolean` jako malá a velká písmena. Všimněte si, že `x:Bool` není alternativu přijala. Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.17 a 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x: Char  
 Pro zálohování CLR `x:Char` primitivní odpovídá <xref:System.Char>.  
  
 Typy řetězce a znak mají interakci s celkovou kódování souboru na úrovni XML. Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.7 a 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x: řetězec  
 Pro zálohování CLR `x:String` primitivní odpovídá <xref:System.String>.  
  
 Typy řetězce a znak mají interakci s celkovou kódování souboru na úrovni XML. Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] části 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x: Decimal  
 Pro zálohování CLR `x:Decimal` primitivní odpovídá <xref:System.Decimal>.  
  
 Všimněte si, že analýza XAML ze své podstaty probíhá v rámci `en-US` jazykovou verzi. V části `en-US` jazykové verzi, vždy období je správný oddělovač pro součásti desetinné číslo (`.`) bez ohledu na jazykové verzi nastavení vývojového prostředí nebo případné klienta cíle, kde je načtena XAML v době běhu.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.14 a 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x: jeden  
 Pro zálohování CLR `x:Single` primitivní odpovídá <xref:System.Single>.  
  
 Kromě číselné hodnoty textových syntaxi pro `x:Single` taky umožňuje tokeny `Infinity`, `-Infinity`, a `NaN`. Tyto tokeny jsou zpracovány jako malá a velká písmena.  
  
 `x:Single` ve formuláři exponenciální notace, může podporovat hodnoty, pokud je první znak v textových syntaxi `e` nebo `E`.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.8 a 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x: Double  
 Pro zálohování CLR `x:Double` primitivní odpovídá <xref:System.Double>.  
  
 Kromě číselné hodnoty textových syntaxi pro `x:Double` umožňuje tokeny `Infinity`, `-Infinity`, a `NaN`. Tyto tokeny jsou zpracovány jako malá a velká písmena.  
  
 `x:Double` ve formuláři vědecká notace může podporovat hodnoty. Použít znak `e` nebo `E` zavádět exponentu část.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.9 a 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x: Int16  
 Pro zálohování CLR `x:Int16` primitivní odpovídá <xref:System.Int16> a `x:Int16` je zpracovaná jako podepsané. V jazyce XAML, chybí znak plus (`+`) přihlášení syntaxe textu je implicitní jako podepsaný kladnou hodnotu.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.11 a 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x: Int32  
 Pro zálohování CLR `x:Int32` primitivní odpovídá <xref:System.Int32>. `x:Int32` je zpracovaná jako podepsané. V jazyce XAML, chybí znak plus (`+`) přihlášení syntaxe textu je implicitní jako podepsaný kladnou hodnotu.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.12 a 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x: Int64  
 Pro zálohování CLR `x:Int64` primitivní odpovídá <xref:System.Int64>. `x:Int64` je zpracovaná jako podepsané. V jazyce XAML, chybí znak plus (`+`) přihlášení syntaxe textu je implicitní jako podepsaný kladnou hodnotu.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.13 a 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x: časový interval  
 Pro zálohování CLR `x:TimeSpan` primitivní odpovídá <xref:System.TimeSpan>.  
  
 Upozorňujeme, že XAML analýza formátu čas datum je ze své podstaty pracujete v části `en-US` jazykovou verzi.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.16 a 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x: identifikátor Uri  
 Pro zálohování CLR `x:Uri` primitivní odpovídá <xref:System.Uri>.  
  
 Kontrola protokolů není součástí definici XAML pro `x:Uri`.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.15 a 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x: bajtů  
 Pro zálohování CLR `x:Byte` primitivní odpovídá <xref:System.Byte>. A <xref:System.Byte>  /  `x:Byte` považuje jako bez znaménka.  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] částech 5.2.10 a 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x: Array  
 Pro zálohování CLR `x:Array` primitivní odpovídá <xref:System.Array>.  
  
 Pole v jazyce XAML 2006 můžete definovat pomocí syntaxi rozšíření značek; Syntaxe jazyka XAML 2009 je však definován jazyk Primitivum, které nevyžaduje přístup k rozšíření značek. Další informace o podpoře XAML 2006 najdete v tématu [x: Array – rozšíření značek](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 Definici specifikace jazyka XAML najdete v části [ \[MS-XAML\] části 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Podpora WPF  
 V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009 ale jenom pro jazyk XAML, který zkompiluje značek není. Zkompilovaný kód XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.  
  
 Scénář, kde můžete použít funkce jazyka XAML 2009 společně s WPF je-li vytvořit přijít XAML a pak načtení tohoto XAML do grafu WPF runtime a objekt s <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a jeho <xref:System.Windows.Markup.XamlReader.Load%2A> může zpracovat klíčová slova jazyka XAML 2009 a funkcí do znázornění platný objekt grafu.
