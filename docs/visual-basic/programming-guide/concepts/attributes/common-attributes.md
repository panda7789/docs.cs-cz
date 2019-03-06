---
title: Běžné atributy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 9c9e8ba886697b9306a89caed4944fd2752db835
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375399"
---
# <a name="common-attributes-visual-basic"></a>Běžné atributy (Visual Basic)
Toto téma popisuje atributy, které se běžně používají v aplikacích jazyka Visual Basic.  
  
-   [Globální atributy](#Global)  
  
-   [Zastaralé atribut](#Obsolete)  
  
-   [Atribut Conditional.](#Conditional)  
  
-   [Atributy informace o volajícím](#CallerInfo)  
  
-   [Visual Basic – atributy](#VB)  
  
## <a name="Global"></a> Globální atributy  
 Většina atributy se použijí na konkrétní jazykové prvky, jako jsou třídy nebo metody; Nicméně některé atributy jsou globální, se vztahují na celé sestavení nebo modulu. Například <xref:System.Reflection.AssemblyVersionAttribute> atribut lze použít k vložení informací o verzi do sestavení, například takto:  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 Globální atributy se zobrazí ve zdrojovém kódu po všech nejvyšší úrovně `Imports` příkazy a před všemi deklaracemi typu, modul nebo obor názvů. Globální atributy lze zobrazit ve více zdrojových souborech, ale soubory musí být zkompilovány při průchodu kompilace. Pro projekty jazyka Visual Basic jsou globálními atributy obecně umístěny v souboru AssemblyInfo.vb (soubor se vytvoří automaticky při vytvoření projektu v sadě Visual Studio).  
  
 Atributy sestavení jsou hodnoty, které obsahují informace o sestavení. Spadají do následujících kategorií:  
  
-   Atributy identity sestavení  
  
-   Informační atributy  
  
-   Atributy manifestu sestavení  
  
### <a name="assembly-identity-attributes"></a>Atributy Identity sestavení  
 Tři atributy (se silným názvem, pokud je k dispozici) určují identitu sestavení: název, verzi a jazykovou verzi. Tyto atributy tvoří úplný název sestavení, jsou povinné, když odkazujete v kódu. Můžete nastavit verzi a jazykovou verzi pomocí atributů sestavení. Je však nastavena hodnota názvu kompilátorem v sadě Visual Studio IDE [dialogové okno informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box), nebo Assembly Linker (Al.exe), když se vytvoří sestavení, na základě souboru, který obsahuje manifest sestavení. <xref:System.Reflection.AssemblyFlagsAttribute> Atribut určuje, zda mohou existovat vedle sebe více kopií daného sestavení.  
  
 V následující tabulce jsou uvedeny atributy identity.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Plně popisuje identity sestavení.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Určuje verzi sestavení.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Určuje, který jazyková verze sestavení podporuje.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Určuje, zda sestavení podporuje spuštění vedle sebe na stejném počítači, ve stejném procesu, nebo ve stejné doméně aplikace.|  
  
### <a name="informational-attributes"></a>Informační atributy  
 Informační atributy můžete zadat další společnosti nebo informace o produktu pro sestavení. V následující tabulce jsou uvedeny informační atributy definované ve <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Definuje vlastní atribut, který určuje název produktu pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Definuje vlastní atribut, který určuje ochranná známka pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Definuje vlastní atribut, který určuje informační verze pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definuje vlastní atribut, který určuje copyright pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instruuje kompilátor, aby používali konkrétní verzi pro prostředek verze souboru Win32.|  
|<xref:System.CLSCompliantAttribute>|Označuje, zda je sestavení kompatibilních s specifikace CLS (Common Language).|  
  
### <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení  
 Atributy manifestu sestavení můžete použít k zadání informací v manifestu sestavení. Jedná se o název, popis, výchozí aliasu a konfiguraci. V následující tabulce jsou uvedeny atributy manifestu sestavení definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Definuje vlastní atribut, který určuje nadpisech sestavení pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definuje vlastní atribut, který určuje konfiguraci služby sestavení (například prodejní nebo ladicí) pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definuje výchozí popisný alias pro manifest sestavení|  
  
## <a name="Obsolete"></a> Zastaralé atribut  
 `Obsolete` Atribut určí program entity jako ten, který už se nedoporučuje používat. Každé použití klíčového entity označený jako zastaralý. následně vygeneruje upozornění nebo chybu, v závislosti na konfiguraci atributu. Příklad:  
  
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
  
 V tomto příkladu `Obsolete` atribut aplikován na třídu `A` a metodě `B.OldMethod`. Protože druhý argument konstruktoru atributu pro `B.OldMethod` je nastavena na `true`, tato metoda způsobí chybu kompilátoru, že horizontálních oddílů pomocí třídy `A` se jen vytvoří upozornění. Volání `B.NewMethod`, ale vytváří žádná upozornění ani chyby.  
  
 Jako součást upozornění nebo chyby se zobrazí jako první argument pro konstruktor atributu v zadaném řetězci. Například když ji použijete s předchozí definice, následující kód vygeneruje dvě upozornění a jednu chybu:  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 Dvě upozornění pro třídu `A` jsou generovány: jeden pro deklaraci odkazech na třídy rozhraní a jeden pro konstruktor třídy.  
  
 `Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení, proč položky je zastaralá a co se má použít místo toho se doporučuje.  
  
 `Obsolete` Atribut je jedno použití atributu a lze použít u Každá entita, která umožňuje atributy. `Obsolete` je alias pro <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a> Atribut Conditional.  
 `Conditional` Atribut umožňuje provádění metody závislé na identifikátor předzpracování. `Conditional` Atribut je alias pro <xref:System.Diagnostics.ConditionalAttribute>a můžete použít u metody nebo třídy atributu.  
  
 V tomto příkladu `Conditional` je použít pro metodu k povolení nebo zakázání zobrazování diagnostické informace specifické pro aplikace:  
  
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
  
 `Conditional` Atribut se často používá s `DEBUG` identifikátor povolit trasování a protokolování funkce pro ladění ale není ve verzi sestavení, tímto způsobem:  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 Při volání metody označené jako podmíněný přítomnosti nebo nepřítomnosti zadaného symbolu předzpracování Určuje, jestli je volání zahrnuté nebo vynechán. Pokud je definován symbol, je součástí; volání v opačném případě je vynechána, volání. Pomocí `Conditional` je čistější, více elegantnímu a méně náchylný alternativou k nadřazené metody uvnitř `#if…#endif` bloků, například takto:  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít návratovou hodnotu.  
  
### <a name="using-multiple-identifiers"></a>Použití více identifikátorů  
 Pokud metoda má více `Conditional` atributy, volání metody je zahrnuta, pokud je definován alespoň jeden z podmíněné symboly (jinými slovy, symboly jsou logicky spojeny operátorem OR). V tomto příkladu přítomnost buď `A` nebo `B` bude výsledkem volání metody:  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 Pokud chcete dosáhnout logicky propojení symboly pomocí operátoru AND, můžete definovat sériového portu podmíněné metody. Například níže druhá metoda spustí, pouze pokud mají oba `A` a `B` jsou definovány:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Podmíněné pomocí třídy atributů  
 `Conditional` Atribut lze použít také pro třídy definice atributu. V tomto příkladu je vlastní atribut `Documentation` se přidat pouze informace metadat je definován DEBUG.  
  
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
  
## <a name="CallerInfo"></a> Atributy informace o volajícím  
 Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a členské jméno volajícího.  
  
 Pokud chcete získat informace o subjektu volajícím člen, použijte atributy, které jsou použity na volitelné parametry. Každý volitelný parametr určuje výchozí hodnotu. V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:  
  
|Atribut|Popis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo názvu vlastnosti volajícího. Další informace najdete v tématu [informace o volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|  
  
 Další informace o atributech informace o volajícím, naleznete v tématu [informace o volajícím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
## <a name="VB"></a> Visual Basic – atributy  
 V následující tabulce jsou uvedeny atributy, které jsou specifické pro Visual Basic.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Označuje kompilátoru, že jako objekt modelu COM by měly být vystaveny třídy.|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Umožňuje členům modulu přistupovat pomocí pouze kvalifikace potřebné pro modul.|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Určuje velikost řetězce pevné délky struktury pro použití se souborem vstupu a výstupu funkcí.|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Určuje velikost pole s pevnou struktury pro použití se souborem vstupu a výstupu funkcí.|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 Použití `COMClassAttribute` ke zjednodušení procesu vytváření komponent modelu COM z jazyka Visual Basic. Objekty COM se výrazně liší od sestavení rozhraní .NET Framework a bez `COMClassAttribute`, musíte použít celou řadou kroků vygenerujete objekt modelu COM z jazyka Visual Basic. Pro třídy označené `COMClassAttribute`, kompilátor provádí mnoho z těchto kroků automaticky.  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 Použití `HideModuleNameAttribute` umožníte členům modulu je přístupný pouze kvalifikace potřebné pro modul.  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 Použití `VBFixedStringAttribute` vynucení jazyka Visual Basic pro vytvoření řetězce pevné délky. Jsou řetězce proměnné délky ve výchozím nastavení, a tento atribut je užitečné při ukládání řetězců do souborů. Následující kód ukazuje toto:  
  
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
 Použití `VBFixedArrayAttribute` Chcete-li deklarovat pole, které mají pevnou velikost. Podobně jako řetězce jazyka Visual Basic jsou pole s proměnnou délkou ve výchozím nastavení. Tento atribut je užitečné při serializaci nebo zápis dat do souborů.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním v jazyce Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Přístup k atributům pomocí reflexe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
