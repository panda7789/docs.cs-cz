---
title: "Mezi běžné atributy (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e0a8912aa60e4c2918bb812963d83fae8d529f1
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="common-attributes-c"></a>Mezi běžné atributy (C#)
Toto téma popisuje atributy, které se běžně používají v C# programy.  
  
-   [Globální atributy](#Global)  
  
-   [Zastaralé atribut](#Obsolete)  
  
-   [Podmíněný atribut](#Conditional)  
  
-   [Volající – atributy s informacemi](#CallerInfo)  
  
##  <a name="Global"></a>Globální atributy  
 Většina atributy platí pro konkrétní jazyk prvky, jako jsou například třídy nebo metody; ale některé atributy jsou globální – se vztahují na modul nebo celý sestavení. Například <xref:System.Reflection.AssemblyVersionAttribute> atribut slouží k vložení informací o verzi do sestavení, například takto:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Globální atributy se zobrazí ve zdrojovém kódu po všech nejvyšší úrovně `using` direktivy a před všechny deklarace typu, modul nebo obor názvů. Globální atributy lze zobrazit v několika zdrojových souborů, ale soubory musí být zkompilovány při průchodu kompilace. V jazyce C# projekty jsou v souboru AssemblyInfo.cs uveďte globálními atributy.  
  
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
  
##  <a name="Obsolete"></a>Zastaralé atribut  
 `Obsolete` Atribut určí program entity jako ten, který již není doporučeno pro použití. Každý použijte entity označeny jako zastaralé následně vydá upozornění nebo chybu, v závislosti na konfiguraci atributu. Příklad:  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 V tomto příkladu `Obsolete` atribut se používá pro třídu `A` a metoda `B.OldMethod`. Protože druhý argument konstruktoru atributu aplikovat `B.OldMethod` je nastaven na `true`, tato metoda způsobí chybu kompilátoru, zatímco použití třídy `A` bude jenom produktu upozornění. Volání metody `B.NewMethod`, ale vytváří žádná upozornění ani chyby.  
  
 Daný řetězec jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby. Například pokud ji používáte s předchozí definice, generuje následující kód, dvě upozornění a jednu chybu:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Dva upozornění pro třídu `A` jsou generovány: jeden pro deklaraci referenci třídy a jeden pro konstruktoru třídy.  
  
 `Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení důvod, proč je zastaralé položky a doporučuje se co místo toho chcete použít.  
  
 `Obsolete` Atribut je jedno použití atribut a dají se použít k Každá entita, která umožňuje atributy. `Obsolete`je alias <xref:System.ObsoleteAttribute>.  
  
##  <a name="Conditional"></a>Podmíněný atribut  
 `Conditional` Atribut umožňuje provádění metody závisí na identifikátor předběžného zpracování. `Conditional` Atribut je alias <xref:System.Diagnostics.ConditionalAttribute>a dají se použít metody nebo třídy atributu.  
  
 V tomto příkladu `Conditional` je použitý na metodu, pokud chcete povolit nebo zakázat zobrazení diagnostické informace specifické pro aplikace:  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 Pokud `TRACE_ON` identifikátor není definován, nezobrazí se žádný výstup trasování.  
  
 `Conditional` Atribut se často používá u `DEBUG` identifikátor povolení trasování a protokolování funkce pro ladění ale není ve verzi sestavení, jako jsou to:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Při volání metody označené jako podmíněného existenci nebo neexistenci těchto zadaný symbol předběžného zpracování určuje, zda je volání zahrnuty nebo tento parametr vynechán. Pokud je definována symbol, volání je zahrnuté; volání, jinak je vynechán. Pomocí `Conditional` je je automaticky více elegantní a méně náchylný alternativa k uzavření metody uvnitř `#if…#endif` bloků, například takto:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Podmíněné metoda musí být metody ve třídě nebo struktuře prohlášení a nesmí mít návratovou hodnotu.  
  
### <a name="using-multiple-identifiers"></a>Použití více identifikátorů  
 Pokud metoda obsahuje více `Conditional` atributy, volání do metody je zahrnuta, pokud je definována alespoň jeden z podmíněného symboly (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR). V tomto příkladu přítomnost buď `A` nebo `B` bude výsledkem volání metody:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 K dosažení účinku logicky propojení symboly pomocí operátoru AND, můžete definovat sériové podmíněného metody. Například druhé metody níže spustí, pouze pokud obě `A` a `B` jsou definovány:  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a>Pomocí podmíněného třídy atributů  
 `Conditional` Atribut lze použít také k – třída definice atributu. V tomto příkladu vlastní atribut `Documentation` pouze přidá informace k metadatům Pokud je definována ladění.  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
##  <a name="CallerInfo"></a>Volající – atributy s informacemi  
 Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku v zdrojový kód a název člena volajícího.  
  
 Chcete-li získat informace o subjektu volajícím člen, použijte atributy, které se použijí pro volitelné parametry. Každý volitelný parametr určí výchozí hodnotu. Následující tabulka uvádí informace o volajícím atributy, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:  
  
|Atribut|Popis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Je to cesta ke v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku v souboru zdroj, ze kterého je volána metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo vlastnosti název volajícího. Další informace najdete v tématu [informace o subjektu volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).|`String`|  
  
 Další informace o atributech volající informace najdete v tématu [informace o subjektu volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Průvodce programováním v C#](../../../../csharp/programming-guide/index.md)  
 [Atributy](../../../../../docs/standard/attributes/index.md)  
 [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
