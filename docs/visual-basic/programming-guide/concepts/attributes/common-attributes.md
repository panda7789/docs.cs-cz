---
title: Běžné atributy
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 2889411779a275baa8c91862d4cac2f820d660d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353532"
---
# <a name="common-attributes-visual-basic"></a>Společné atributy (Visual Basic)

Toto téma popisuje atributy, které se nejčastěji používají v Visual Basicch programech.

- [Globální atributy](#Global)

- [Zastaralý atribut](#Obsolete)

- [Podmíněný atribut](#Conditional)

- [Atributy informací o volajícím](#CallerInfo)

- [Atributy Visual Basic](#VB)

## <a name="Global"></a>Globální atributy

Většina atributů je aplikována na konkrétní prvky jazyka, jako jsou třídy nebo metody. Některé atributy jsou však globální – platí pro celé sestavení nebo modul. Například atribut <xref:System.Reflection.AssemblyVersionAttribute> lze použít k vložení informací o verzi do sestavení, například takto:

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

Globální atributy se zobrazí ve zdrojovém kódu po všech příkazech `Imports` nejvyšší úrovně a před všemi deklaracemi typu, modulu nebo oboru názvů. Globální atributy se mohou objevit ve více zdrojových souborech, ale soubory musí být kompilovány v rámci jedné kompilační fáze. U Visual Basic projektů jsou globální atributy obecně vloženy do souboru AssemblyInfo. vb (soubor je vytvořen automaticky při vytvoření projektu v aplikaci Visual Studio).

Atributy sestavení jsou hodnoty, které poskytují informace o sestavení. Spadají do následujících kategorií:

- Atributy identity sestavení

- Informativní atributy

- Atributy manifestu sestavení

### <a name="assembly-identity-attributes"></a>Atributy identity sestavení

Tři atributy (se silným názvem, pokud jsou k dispozici) určují identitu sestavení: název, verze a jazyková verze. Tyto atributy tvoří úplný název sestavení a jsou vyžadovány při odkazování v kódu. Můžete nastavit verzi a jazykovou verzi sestavení pomocí atributů. Hodnota name je však nastavena kompilátorem, rozhraním IDE sady Visual Studio v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box)nebo linker sestavení (Al. exe), když je sestavení vytvořeno, na základě souboru, který obsahuje manifest sestavení. Atribut <xref:System.Reflection.AssemblyFlagsAttribute> určuje, zda více kopií sestavení může existovat současně.

V následující tabulce jsou uvedeny atributy identity.

|Atribut|Účel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|Plně popisuje identitu sestavení.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Určuje verzi sestavení.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Určuje jazykovou verzi, kterou sestavení podporuje.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Určuje, zda sestavení podporuje souběžné spouštění ve stejném počítači, ve stejném procesu nebo ve stejné doméně aplikace.|

### <a name="informational-attributes"></a>Informativní atributy

Pomocí informativních atributů lze poskytnout další informace o společnosti nebo produktu pro sestavení. V následující tabulce jsou uvedeny informativní atributy definované v oboru názvů <xref:System.Reflection?displayProperty=nameWithType>.

|Atribut|Účel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Definuje vlastní atribut, který určuje název produktu pro manifest sestavení.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Definuje vlastní atribut, který určuje ochrannou známku pro manifest sestavení.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Definuje vlastní atribut, který určuje informační verzi manifestu sestavení.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definuje vlastní atribut, který určuje autorská práva pro manifest sestavení.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instruuje kompilátor, aby pro prostředek verze souboru Win32 použil konkrétní číslo verze.|
|<xref:System.CLSCompliantAttribute>|Určuje, zda je sestavení kompatibilní se specifikací CLS (Common Language Specification).|

### <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení

Atributy manifestu sestavení lze použít k poskytnutí informací v manifestu sestavení. Patří sem název, popis, výchozí alias a konfigurace. V následující tabulce jsou uvedeny atributy manifestu sestavení definované v oboru názvů <xref:System.Reflection?displayProperty=nameWithType>.

|Atribut|Účel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Definuje vlastní atribut, který určuje název sestavení pro manifest sestavení.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definuje vlastní atribut, který určuje konfiguraci sestavení (například maloobchodní nebo ladicí) pro manifest sestavení.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definuje popisný výchozí alias pro manifest sestavení.|

## <a name="Obsolete"></a>Zastaralý atribut

Atribut `Obsolete` označuje entitu programu jako tu, která se již nedoporučuje používat. Každé použití entity označené jako zastaralé bude následně generovat upozornění nebo chybu v závislosti na tom, jak je atribut nakonfigurován. Příklad:

```vb
<System.Obsolete("use class B")>
Class A
    Sub Method()
    End Sub
End Class

Class B
    <System.Obsolete("use NewMethod", True)>
    Sub OldMethod()
    End Sub

    Sub NewMethod()
    End Sub
End Class
```

V tomto příkladu je atribut `Obsolete` použit pro třídu `A` a na metodu `B.OldMethod`. Vzhledem k tomu, že druhý argument konstruktoru atributu použité pro `B.OldMethod` je nastaven na `true`, tato metoda způsobí chybu kompilátoru, zatímco použití třídy `A` bude pouze generovat upozornění. Volání `B.NewMethod`však negeneruje žádné upozornění nebo chybu.

Řetězec poskytnutý jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby. Například když použijete s předchozími definicemi, následující kód vygeneruje dvě upozornění a jednu chybu:

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

Pro třídu `A` jsou generována dvě upozornění: jedna pro deklaraci odkazu na třídu a druhá pro konstruktor třídy.

Atribut `Obsolete` lze použít bez argumentů, ale včetně vysvětlení, proč je položka zastaralá a co použít místo toho se doporučuje.

Atribut `Obsolete` je atributem s jedním použitím a lze jej použít pro libovolnou entitu, která povoluje atributy. `Obsolete` je alias pro <xref:System.ObsoleteAttribute>.

## <a name="Conditional"></a>Podmíněný atribut

Atribut `Conditional` provádí provedení metody závislé na identifikátoru předběžného zpracování. Atribut `Conditional` je aliasem pro <xref:System.Diagnostics.ConditionalAttribute>a lze jej použít na metodu nebo třídu atributu.

V tomto příkladu je `Conditional` použita na metodu pro povolení nebo zakázání zobrazení diagnostických informací specifických pro program:

```vb
#Const TRACE_ON = True
Imports System.Diagnostics

Module TestConditionalAttribute
    Public Class Trace
        <Conditional("TRACE_ON")>
        Public Shared Sub Msg(ByVal msg As String)
            Console.WriteLine(msg)
        End Sub

    End Class

    Sub Main()
        Trace.Msg("Now in Main...")
        Console.WriteLine("Done.")
    End Sub
End Module
```

Pokud není definován `TRACE_ON` identifikátor, nebude zobrazen žádný výstup trasování.

Atribut `Conditional` se často používá s identifikátorem `DEBUG` k povolení funkcí trasování a protokolování pro sestavení ladění, ale ne v sestaveních vydaných verzí, například:

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

Když je volána metoda označená jako podmíněná, přítomnost nebo absence zadaného symbolu předzpracování určuje, zda je volání zahrnuto nebo vynecháno. Pokud je symbol definován, volání je zahrnuto; v opačném případě je volání vynecháno. Použití `Conditional` je čistší, jasnější a méně náchylné k chybám, které lze použít k uzavření metod uvnitř `#if…#endif`ch bloků, například takto:

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít návratovou hodnotu.

### <a name="using-multiple-identifiers"></a>Použití více identifikátorů

Pokud má metoda více `Conditional` atributů, volání metody je zahrnuto, pokud je definován alespoň jeden z podmíněných symbolů (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR). V tomto příkladu přítomnost buď `A`, nebo `B`, bude výsledkem volání metody:

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

Chcete-li dosáhnout vlivu logického propojení symbolů pomocí operátoru AND, můžete definovat sériové podmíněné metody. Například druhá metoda níže se spustí pouze v případě, že jsou definovány obě `A` i `B`:

```vb
<Conditional("A")>
Shared Sub DoIfA()
    DoIfAandB()
End Sub

<Conditional("B")>
Shared Sub DoIfAandB()
    ' Code to execute when both A and B are defined...
End Sub
```

### <a name="using-conditional-with-attribute-classes"></a>Použití podmíněné s třídami atributů

Atribut `Conditional` lze také použít pro definici třídy atributu. V tomto příkladu vlastní atribut `Documentation` přidá do metadat informace pouze v případě, že je definován ladění.

```vb
<Conditional("DEBUG")>
Public Class Documentation
    Inherits System.Attribute
    Private text As String
    Sub New(ByVal doc_text As String)
        text = doc_text
    End Sub
End Class

Class SampleClass
    ' This attribute will only be included if DEBUG is defined.
    <Documentation("This method displays an integer.")>
    Shared Sub DoWork(ByVal i As Integer)
        System.Console.WriteLine(i)
    End Sub
End Class
```

## <a name="CallerInfo"></a>Atributy informací o volajícím

Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.

Chcete-li získat informace o volajícím členu, použijte atributy, které se použijí na volitelné parametry. Každý volitelný parametr určuje výchozí hodnotu. V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou definovány v oboru názvů <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:

|Atribut|Popis|Typ|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta v době kompilace.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ze kterého je metoda volána.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo název vlastnosti volajícího. Další informace najdete v tématu [informace o volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|

Další informace o atributech informace o volajícím naleznete v tématu [informace o volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).

## <a name="VB"></a>Atributy Visual Basic

V následující tabulce jsou uvedeny atributy, které jsou specifické pro Visual Basic.

|Atribut|Účel|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Určuje kompilátoru, že by měla být třída vystavena jako objekt modelu COM.|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Umožňuje, aby byly členy modulu dostupné pouze pomocí kvalifikace potřebné pro modul.|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Určuje velikost řetězce s pevnou délkou ve struktuře pro použití s funkcemi vstupu a výstupu souboru.|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Určuje velikost fixního pole ve struktuře pro použití s funkcemi vstupu a výstupu souboru.|

### <a name="comclassattribute"></a>COMClassAttribute

Použití `COMClassAttribute` ke zjednodušení procesu vytváření komponent modelu COM z Visual Basic. Objekty COM se výrazně liší od .NET Framework sestavení a bez `COMClassAttribute`, je nutné postupovat podle řady kroků pro vygenerování objektu COM z Visual Basic. Pro třídy označené `COMClassAttribute`kompilátor provede mnoho z těchto kroků automaticky.

### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute

Pomocí `HideModuleNameAttribute` můžete uživatelům modulu dovolit, aby měli k dispozici pouze kvalifikaci potřebnou pro modul.

### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute

K vynucení Visual Basic vytvoření řetězce s pevnou délkou použijte `VBFixedStringAttribute`. Řetězce mají ve výchozím nastavení proměnlivou délku a tento atribut je užitečný při ukládání řetězců do souborů. Následující kód demonstruje:

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a>VBFixedArrayAttribute

Použijte `VBFixedArrayAttribute` k deklaraci polí, která mají pevně danou velikost. Stejně jako řetězce Visual Basic, pole mají ve výchozím nastavení proměnlivou délku. Tento atribut je užitečný při serializaci nebo zápisu dat do souborů.

## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
