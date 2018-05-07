---
title: Mezi běžné atributy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 5a91b0aa48a22db4ea7fb56a9c632ff0cb44dce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="common-attributes-visual-basic"></a>Mezi běžné atributy (Visual Basic)
Toto téma popisuje atributy, které se běžně používají v aplikacích jazyka Visual Basic.  
  
-   [Globální atributy](#Global)  
  
-   [Zastaralé atribut](#Obsolete)  
  
-   [Podmíněný atribut](#Conditional)  
  
-   [Volající – atributy s informacemi](#CallerInfo)  
  
-   [Visual Basic – atributy](#VB)  
  
##  <a name="Global"></a> Globální atributy  
 Většina atributy platí pro konkrétní jazyk prvky, jako jsou například třídy nebo metody; ale některé atributy jsou globální – se vztahují na modul nebo celý sestavení. Například <xref:System.Reflection.AssemblyVersionAttribute> atribut slouží k vložení informací o verzi do sestavení, například takto:  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 Globální atributy se zobrazí ve zdrojovém kódu po všech nejvyšší úrovně `Imports` příkazy a před všechny deklarace typu, modul nebo obor názvů. Globální atributy lze zobrazit v několika zdrojových souborů, ale soubory musí být zkompilovány při průchodu kompilace. Pro projekty Visual Basic jsou obecně globálními atributy uveďte v souboru AssemblyInfo.vb (soubor se vytvoří automaticky při vytvoření projektu v sadě Visual Studio).  
  
 Atributů sestavení jsou hodnoty, které obsahují informace o sestavení. Spadají do následujících kategorií:  
  
-   Atributy identity sestavení  
  
-   Informační atributy  
  
-   Atributy manifestu sestavení  
  
### <a name="assembly-identity-attributes"></a>Atributy Identity sestavení  
 Zjistit identitu sestavení tři atributy (se silným názvem, pokud je k dispozici): název, verzi a jazykovou verzi. Tyto atributy tvoří úplný název sestavení a jsou povinné, pokud odkazujete v kódu. Můžete nastavit verze a jazykové verze pomocí atributů sestavení. Hodnota názvu je ale nastavená kompilátorem prostředí Visual Studio IDE v [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box), nebo na soubor, který obsahuje manifest sestavení na základě Linker sestavení (Al.exe) při vytváření sestavení. <xref:System.Reflection.AssemblyFlagsAttribute> Atribut určuje, zda více kopií sestavení mohou existovat vedle sebe.  
  
 V následující tabulce jsou uvedeny atributy identity.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Popisuje plně identitu sestavení.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Určuje verzi sestavení.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Určuje, které jazykovou verzi sestavení podporuje.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Určuje, zda sestavení podporuje spuštění vedle sebe na stejném počítači, v rámci jednoho procesu, nebo ve stejné doméně aplikace.|  
  
### <a name="informational-attributes"></a>Informační atributy  
 Informační atributy můžete zadat další společnosti nebo informace o produktu pro sestavení. V následující tabulce jsou definované v informační atributy <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Definuje vlastní atribut, který určuje název produktu manifest sestavení.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Definuje vlastní atribut, který určuje ochrannou známku pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Definuje vlastní atribut, který určuje informační verze pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definuje vlastní atribut, který určuje copyright pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Dá pokyn kompilátoru použít konkrétní verzi číslo pro prostředek verze souboru Win32.|  
|<xref:System.CLSCompliantAttribute>|Určuje, zda je sestavení kompatibilní s specifikace CLS (Common Language).|  
  
### <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení  
 Atributy manifestu sestavení můžete použít k poskytování informací v manifestu sestavení. To zahrnuje název, popis, výchozí alias a konfigurace. V následující tabulce jsou definované atributy manifestu sestavení v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Definuje vlastní atribut, který určuje název sestavení manifestu sestavení.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Manifest sestavení definuje vlastní atribut, který určuje konfigurace aplikace sestavení (například instalačních nebo ladicích).|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definuje výchozí popisný aliasu pro manifest sestavení|  
  
##  <a name="Obsolete"></a> Zastaralé atribut  
 `Obsolete` Atribut určí program entity jako ten, který již není doporučeno pro použití. Každý použijte entity označeny jako zastaralé následně vydá upozornění nebo chybu, v závislosti na konfiguraci atributu. Příklad:  
  
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
  
 V tomto příkladu `Obsolete` atribut se používá pro třídu `A` a metoda `B.OldMethod`. Protože druhý argument konstruktoru atributu aplikovat `B.OldMethod` je nastaven na `true`, tato metoda způsobí chybu kompilátoru, zatímco použití třídy `A` bude jenom produktu upozornění. Volání metody `B.NewMethod`, ale vytváří žádná upozornění ani chyby.  
  
 Daný řetězec jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby. Například pokud ji používáte s předchozí definice, generuje následující kód, dvě upozornění a jednu chybu:  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 Dva upozornění pro třídu `A` jsou generovány: jeden pro deklaraci referenci třídy a jeden pro konstruktoru třídy.  
  
 `Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení důvod, proč je zastaralé položky a doporučuje se co místo toho chcete použít.  
  
 `Obsolete` Atribut je jedno použití atribut a dají se použít k Každá entita, která umožňuje atributy. `Obsolete` je alias <xref:System.ObsoleteAttribute>.  
  
##  <a name="Conditional"></a> Podmíněný atribut  
 `Conditional` Atribut umožňuje provádění metody závisí na identifikátor předběžného zpracování. `Conditional` Atribut je alias <xref:System.Diagnostics.ConditionalAttribute>a dají se použít metody nebo třídy atributu.  
  
 V tomto příkladu `Conditional` je použitý na metodu, pokud chcete povolit nebo zakázat zobrazení diagnostické informace specifické pro aplikace:  
  
```vb  
#Const TRACE_ON = True  
Imports System  
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
  
 Pokud `TRACE_ON` identifikátor není definován, nezobrazí se žádný výstup trasování.  
  
 `Conditional` Atribut se často používá u `DEBUG` identifikátor povolení trasování a protokolování funkce pro ladění ale není ve verzi sestavení, jako jsou to:  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 Při volání metody označené jako podmíněného existenci nebo neexistenci těchto zadaný symbol předběžného zpracování určuje, zda je volání zahrnuty nebo tento parametr vynechán. Pokud je definována symbol, volání je zahrnuté; volání, jinak je vynechán. Pomocí `Conditional` je je automaticky více elegantní a méně náchylný alternativa k uzavření metody uvnitř `#if…#endif` bloků, například takto:  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 Podmíněné metoda musí být metody ve třídě nebo struktuře prohlášení a nesmí mít návratovou hodnotu.  
  
### <a name="using-multiple-identifiers"></a>Použití více identifikátorů  
 Pokud metoda obsahuje více `Conditional` atributy, volání do metody je zahrnuta, pokud je definována alespoň jeden z podmíněného symboly (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR). V tomto příkladu přítomnost buď `A` nebo `B` bude výsledkem volání metody:  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 K dosažení účinku logicky propojení symboly pomocí operátoru AND, můžete definovat sériové podmíněného metody. Například druhé metody níže spustí, pouze pokud obě `A` a `B` jsou definovány:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Pomocí podmíněného třídy atributů  
 `Conditional` Atribut lze použít také k – třída definice atributu. V tomto příkladu vlastní atribut `Documentation` pouze přidá informace k metadatům Pokud je definována ladění.  
  
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
  
##  <a name="CallerInfo"></a> Volající – atributy s informacemi  
 Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku v zdrojový kód a název člena volajícího.  
  
 Chcete-li získat informace o subjektu volajícím člen, použijte atributy, které se použijí pro volitelné parametry. Každý volitelný parametr určí výchozí hodnotu. Následující tabulka uvádí informace o volajícím atributy, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:  
  
|Atribut|Popis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Je to cesta ke v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku v souboru zdroj, ze kterého je volána metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo vlastnosti název volajícího. Další informace najdete v tématu [informace o subjektu volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|  
  
 Další informace o atributech volající informace najdete v tématu [informace o subjektu volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
##  <a name="VB"></a> Visual Basic – atributy  
 Následující tabulka obsahuje seznam atributy, které jsou specifické pro Visual Basic.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Kompilátoru označuje, že jako objekt modelu COM by měly být vystaveny třídy.|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Umožňuje členům modul přístup k použití pouze kvalifikace potřebné pro modul.|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Určuje velikost řetězce pevné délky souborem vstup a výstup do struktury pro použití funkce.|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Určuje velikost pevné pole do struktury pro použití s souboru vstup a výstup funkce.|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 Použití `COMClassAttribute` zjednodušit proces vytváření komponenty modelu COM z jazyka Visual Basic. COM – objekty se podstatně liší od sestavení rozhraní .NET Framework a bez `COMClassAttribute`, je třeba provést několik kroků pro generování objektu COM z jazyka Visual Basic. Pro třídy označené jako `COMClassAttribute`, kompilátor nabízí mnoho z těchto kroků automaticky.  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 Použití `HideModuleNameAttribute` umožníte členům modulu nelze přistupovat pomocí pouze kvalifikace potřebné pro modul.  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 Použití `VBFixedStringAttribute` vynutit jazyka Visual Basic pro vytvoření řetězce pevné délky. S proměnnou délkou ve výchozím nastavení jsou řetězce, a tento atribut je užitečné, když ukládání řetězců do souborů. Následující kód ukazuje toto:  
  
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
 Použití `VBFixedArrayAttribute` deklarovat pole, které mají pevnou velikost. Pole jsou stejně jako Visual Basic – řetězce, s proměnnou délkou ve výchozím nastavení. Tento atribut je užitečný při serializaci nebo zápis dat do souborů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Atributy](../../../../standard/attributes/index.md)  
 [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
