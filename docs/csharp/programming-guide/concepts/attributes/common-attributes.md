---
title: Běžné atributy (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: d5d56fff82fb552f42f72c18b8c3b907c5bc113c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702578"
---
# <a name="common-attributes-c"></a>Běžné atributy (C#)
Toto téma popisuje atributy, které se běžně používají v aplikacích jazyka C#.  
  
- [Globální atributy](#Global)  
  
- [Zastaralé atribut](#Obsolete)  
  
- [Atribut Conditional.](#Conditional)  
  
- [Atributy informace o volajícím](#CallerInfo)  
  
## <a name="Global"></a> Globální atributy  
 Většina atributy se použijí na konkrétní jazykové prvky, jako jsou třídy nebo metody; Nicméně některé atributy jsou globální, se vztahují na celé sestavení nebo modulu. Například <xref:System.Reflection.AssemblyVersionAttribute> atribut lze použít k vložení informací o verzi do sestavení, například takto:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Globální atributy se zobrazí ve zdrojovém kódu po všech nejvyšší úrovně `using` direktivy a před všemi deklaracemi typu, modul nebo obor názvů. Globální atributy lze zobrazit ve více zdrojových souborech, ale soubory musí být zkompilovány při průchodu kompilace. V projektech C# globální atributy jsou umístěny v souboru AssemblyInfo.cs.  
  
 Atributy sestavení jsou hodnoty, které obsahují informace o sestavení. Spadají do následujících kategorií:  
  
- Atributy identity sestavení  
  
- Informační atributy  
  
- Atributy manifestu sestavení  
  
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
  
 V tomto příkladu `Obsolete` atribut aplikován na třídu `A` a metodě `B.OldMethod`. Protože druhý argument konstruktoru atributu pro `B.OldMethod` je nastavena na `true`, tato metoda způsobí chybu kompilátoru, že horizontálních oddílů pomocí třídy `A` se jen vytvoří upozornění. Volání `B.NewMethod`, ale vytváří žádná upozornění ani chyby.  
  
 Jako součást upozornění nebo chyby se zobrazí jako první argument pro konstruktor atributu v zadaném řetězci. Například když ji použijete s předchozí definice, následující kód vygeneruje dvě upozornění a jednu chybu:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Dvě upozornění pro třídu `A` jsou generovány: jeden pro deklaraci odkazech na třídy rozhraní a jeden pro konstruktor třídy.  
  
 `Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení, proč položky je zastaralá a co se má použít místo toho se doporučuje.  
  
 `Obsolete` Atribut je jedno použití atributu a lze použít u Každá entita, která umožňuje atributy. `Obsolete` je alias pro <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a> Atribut Conditional.  
 `Conditional` Atribut umožňuje provádění metody závislé na identifikátor předzpracování. `Conditional` Atribut je alias pro <xref:System.Diagnostics.ConditionalAttribute>a můžete použít u metody nebo třídy atributu.  
  
 V tomto příkladu `Conditional` je použít pro metodu k povolení nebo zakázání zobrazování diagnostické informace specifické pro aplikace:  
  
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
  
 `Conditional` Atribut se často používá s `DEBUG` identifikátor povolit trasování a protokolování funkce pro ladění ale není ve verzi sestavení, tímto způsobem:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Při volání metody označené jako podmíněný přítomnosti nebo nepřítomnosti zadaného symbolu předzpracování Určuje, jestli je volání zahrnuté nebo vynechán. Pokud je definován symbol, je součástí; volání v opačném případě je vynechána, volání. Pomocí `Conditional` je čistější, více elegantnímu a méně náchylný alternativou k nadřazené metody uvnitř `#if…#endif` bloků, například takto:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít návratovou hodnotu.  
  
### <a name="using-multiple-identifiers"></a>Použití více identifikátorů  
 Pokud metoda má více `Conditional` atributy, volání metody je zahrnuta, pokud je definován alespoň jeden z podmíněné symboly (jinými slovy, symboly jsou logicky spojeny operátorem OR). V tomto příkladu přítomnost buď `A` nebo `B` bude výsledkem volání metody:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Pokud chcete dosáhnout logicky propojení symboly pomocí operátoru AND, můžete definovat sériového portu podmíněné metody. Například níže druhá metoda spustí, pouze pokud mají oba `A` a `B` jsou definovány:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Podmíněné pomocí třídy atributů  
 `Conditional` Atribut lze použít také pro třídy definice atributu. V tomto příkladu je vlastní atribut `Documentation` se přidat pouze informace metadat je definován DEBUG.  
  
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
  
## <a name="CallerInfo"></a> Atributy informace o volajícím  
 Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a členské jméno volajícího.  
  
 Pokud chcete získat informace o subjektu volajícím člen, použijte atributy, které jsou použity na volitelné parametry. Každý volitelný parametr určuje výchozí hodnotu. V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:  
  
|Atribut|Popis|Type|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo názvu vlastnosti volajícího. Další informace najdete v tématu [informace o volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).|`String`|  
  
 Další informace o atributech informace o volajícím, naleznete v tématu [informace o volajícím (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)
- [Atributy](../../../../../docs/standard/attributes/index.md)
- [Reflexe (C#)](../../../../csharp/programming-guide/concepts/reflection.md)
- [Přístup k atributům pomocí reflexe (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
