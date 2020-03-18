---
title: Běžné atributy (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399754"
---
# <a name="common-attributes-c"></a>Běžné atributy (C#)
Toto téma popisuje atributy, které se nejčastěji používají v programech jazyka C#.  
  
- [Globální atributy](#Global)  
  
- [Zastaralý atribut](#Obsolete)  
  
- [Podmíněný atribut](#Conditional)  
  
- [Atributy informací o volajícím](#CallerInfo)  
  
## <a name="Global"></a>Globální atributy  
 Většina atributů je použita pro určité jazykové prvky, jako jsou třídy nebo metody; některé atributy jsou však globální – platí pro celé sestavení nebo modul. <xref:System.Reflection.AssemblyVersionAttribute> Atribut lze například použít k vložení informací o verzi do sestavení, například takto:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Globální atributy se zobrazí ve zdrojovém kódu za všechny direktivy nejvyšší úrovně `using` a před jakýmkoli typem, modulem nebo deklaracemi oboru názvů. Globální atributy se mohou objevit ve více zdrojových souborech, ale soubory musí být zkompilovány v jednom průchodu kompilace. V projektech Jazyka C# jsou globální atributy vloženy do souboru AssemblyInfo.cs.  
  
 Atributy sestavení jsou hodnoty, které poskytují informace o sestavení. Spadají do následujících kategorií:  
  
- Atributy identity sestavení  
  
- Informační atributy  
  
- Atributy manifestu sestavení  
  
### <a name="assembly-identity-attributes"></a>Atributy identity sestavení  
 Identitu sestavení určují tři atributy (případně se silným názvem) název sestavení: název, verze a jazyková verze. Tyto atributy tvoří úplný název sestavení a jsou vyžadovány, když na něj odkazujete v kódu. Můžete nastavit verzi sestavení a jazykovou verzi pomocí atributů. Hodnota názvu je však nastavena kompilátorem, IDE sady Visual Studio v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box)nebo propojovací množinu sestavení (Al.exe) při vytvoření sestavení na základě souboru, který obsahuje manifest sestavení. Atribut <xref:System.Reflection.AssemblyFlagsAttribute> určuje, zda může existovat více kopií sestavení.  
  
 V následující tabulce jsou uvedeny atributy identity.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Plně popisuje identitu sestavení.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Určuje verzi sestavení.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Určuje, kterou jazykovou verzi sestavení podporuje.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Určuje, zda sestavení podporuje souběžné spuštění ve stejném počítači, ve stejném procesu nebo ve stejné doméně aplikace.|  
  
### <a name="informational-attributes"></a>Informační atributy  
 Informační atributy můžete použít k poskytnutí dalších informací o společnosti nebo produktu pro sestavení. V následující tabulce jsou uvedeny informační <xref:System.Reflection?displayProperty=nameWithType> atributy definované v oboru názvů.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Definuje vlastní atribut, který určuje název produktu pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Definuje vlastní atribut, který určuje ochrannou známku pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Definuje vlastní atribut, který určuje informační verzi manifestu sestavení.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Definuje vlastní atribut, který určuje název společnosti pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definuje vlastní atribut, který určuje autorská práva pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Dává kompilátoru pokyn, aby pro prostředek verze souboru Win32 použil konkrétní číslo verze.|  
|<xref:System.CLSCompliantAttribute>|Označuje, zda je sestavení kompatibilní se specifikací CLS (Common Language Specification).|  
  
### <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení  
 Atributy manifestu sestavení můžete použít k poskytnutí informací v manifestu sestavení. To zahrnuje název, popis, výchozí alias a konfiguraci. V následující tabulce jsou uvedeny atributy manifestu sestavení definované v oboru <xref:System.Reflection?displayProperty=nameWithType> názvů.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Definuje vlastní atribut, který určuje název sestavení pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definuje vlastní atribut, který určuje konfiguraci sestavení (například maloobchodní nebo ladicí) pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definuje popisný výchozí alias pro manifest sestavení.|  
  
## <a name="Obsolete"></a>Zastaralý atribut  
 Atribut `Obsolete` označí entitu programu jako entitu, která se již nedoporučuje používat. Každé použití entity označené jako zastaralé následně vygeneruje upozornění nebo chybu v závislosti na konfiguraci atributu. Například:  
  
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
  
 V tomto `Obsolete` příkladu je `A` atribut použit `B.OldMethod`pro třídu a metodu . Vzhledem k tomu, že druhý `B.OldMethod` argument `true`konstruktoru atributu aplikovaný na je `A` nastavena na , tato metoda způsobí chybu kompilátoru, vzhledem k tomu, že pomocí třídy pouze vytvoří upozornění. Volání `B.NewMethod`, však nevytváří žádné upozornění nebo chybu.  
  
 Řetězec zadaný jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby. Například při použití s předchozími definicemi, následující kód generuje dvě upozornění a jednu chybu:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Jsou generována `A` dvě upozornění pro třídu: jeden pro deklaraci odkazu třídy a jeden pro konstruktor třídy.  
  
 Atribut `Obsolete` lze použít bez argumentů, ale včetně vysvětlení, proč je položka zastaralá a co použít místo toho se doporučuje.  
  
 Atribut `Obsolete` je atribut na jedno použití a lze jej použít pro libovolnou entitu, která umožňuje atributy. `Obsolete`je alias <xref:System.ObsoleteAttribute>pro aplikaci .  
  
## <a name="Conditional"></a>Podmíněný atribut  
 Atribut `Conditional` umožňuje provádění metody závislé na identifikátor předběžného zpracování. Atribut `Conditional` je alias <xref:System.Diagnostics.ConditionalAttribute>pro aplikaci a lze jej použít na metodu nebo třídu atributu.  
  
 V tomto `Conditional` příkladu se používá metoda povolení nebo zakázání zobrazení diagnostických informací specifických pro program:  
  
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
  
 Pokud `TRACE_ON` identifikátor není definován, zobrazí se žádný výstup trasování.  
  
 Atribut `Conditional` se často používá `DEBUG` s identifikátorem povolit trasování a protokolování funkce pro ladění sestavení, ale ne ve verzi sestavení, takto:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Pokud je volána metoda označená jako podmíněná, přítomnost nebo nepřítomnost zadaného symbolu předběžného zpracování určuje, zda je volání zahrnuto nebo vynecháno. Pokud je definován symbol, je zahrnuto volání; v opačném případě je volání vynecháno. Použití `Conditional` je čistší, elegantnější a méně náchylná k chybám `#if…#endif` alternativa k ohraničování metod uvnitř bloků, jako je tento:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít vrácenou hodnotu.  
  
### <a name="using-multiple-identifiers"></a>Použití více identifikátorů  
 Pokud má metoda `Conditional` více atributů, je zahrnuto volání metody, pokud je definován alespoň jeden z podmíněných symbolů (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR). V tomto příkladu přítomnost `A` `B` buď nebo bude mít za následek volání metody:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Chcete-li dosáhnout efektu logického propojení symbolů pomocí operátoru AND, můžete definovat sériové podmíněné metody. Například druhá metoda níže bude spuštěna pouze v případě, že jsou definovány obě `A` a `B` jsou definovány:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Použití podmíněného s třídami atributů  
 Atribut `Conditional` lze také použít na definici třídy atributu. V tomto příkladu `Documentation` bude vlastní atribut přidávat informace pouze do metadat, pokud je definováno LADĚNÍ.  
  
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
  
## <a name="CallerInfo"></a>Atributy informací o volajícím  
 Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a jméno člena volajícího.  
  
 Chcete-li získat informace o volajícím člena, použijte atributy, které jsou použity pro volitelné parametry. Každý volitelný parametr určuje výchozí hodnotu. V následující tabulce jsou uvedeny atributy <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> Informace o volajícím, které jsou definovány v oboru názvů:  
  
|Atribut|Popis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ze kterého je metoda volána.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo název vlastnosti volajícího. Další informace naleznete v [tématu Informace o volajícím (C#)](../caller-information.md).|`String`|  
  
 Další informace o atributech Informace o volajícím naleznete v [tématu Informace o volajícím (C#).](../caller-information.md)  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Programovací příručka jazyka C#](../../index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (C#)](../reflection.md)
- [Přístup k atributům pomocí reflexe (C#)](./accessing-attributes-by-using-reflection.md)
