---
title: Společné atributy (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595457"
---
# <a name="common-attributes-c"></a>Společné atributy (C#)
Toto téma popisuje atributy, které se nejčastěji používají v C# programech.  
  
- [Globální atributy](#Global)  
  
- [Zastaralý atribut](#Obsolete)  
  
- [Podmíněný atribut](#Conditional)  
  
- [Atributy informací o volajícím](#CallerInfo)  
  
## <a name="Global"></a>Globální atributy  
 Většina atributů je aplikována na konkrétní prvky jazyka, jako jsou třídy nebo metody. Některé atributy jsou však globální – platí pro celé sestavení nebo modul. Například <xref:System.Reflection.AssemblyVersionAttribute> atribut lze použít k vložení informací o verzi do sestavení, jako je:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Globální atributy se zobrazí ve zdrojovém kódu za všemi direktivami `using` nejvyšší úrovně a před všemi deklaracemi typu, modulu nebo oboru názvů. Globální atributy se mohou objevit ve více zdrojových souborech, ale soubory musí být kompilovány v rámci jedné kompilační fáze. V C# projektech jsou globální atributy vloženy do souboru AssemblyInfo.cs.  
  
 Atributy sestavení jsou hodnoty, které poskytují informace o sestavení. Spadají do následujících kategorií:  
  
- Atributy identity sestavení  
  
- Informativní atributy  
  
- Atributy manifestu sestavení  
  
### <a name="assembly-identity-attributes"></a>Atributy identity sestavení  
 Tři atributy (se silným názvem, pokud jsou k dispozici) určují identitu sestavení: název, verze a jazyková verze. Tyto atributy tvoří úplný název sestavení a jsou vyžadovány při odkazování v kódu. Můžete nastavit verzi a jazykovou verzi sestavení pomocí atributů. Hodnota name je však nastavena kompilátorem, rozhraním IDE sady Visual Studio v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box)nebo linker sestavení (Al. exe), když je sestavení vytvořeno, na základě souboru, který obsahuje manifest sestavení. <xref:System.Reflection.AssemblyFlagsAttribute> Atribut určuje, zda více kopií sestavení může existovat současně.  
  
 V následující tabulce jsou uvedeny atributy identity.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Plně popisuje identitu sestavení.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Určuje verzi sestavení.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Určuje jazykovou verzi, kterou sestavení podporuje.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Určuje, zda sestavení podporuje souběžné spouštění ve stejném počítači, ve stejném procesu nebo ve stejné doméně aplikace.|  
  
### <a name="informational-attributes"></a>Informativní atributy  
 Pomocí informativních atributů lze poskytnout další informace o společnosti nebo produktu pro sestavení. V následující tabulce jsou uvedeny informativní atributy definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.  
  
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
 Atributy manifestu sestavení lze použít k poskytnutí informací v manifestu sestavení. Patří sem název, popis, výchozí alias a konfigurace. V následující tabulce jsou uvedeny atributy manifestu sestavení definované v <xref:System.Reflection?displayProperty=nameWithType> oboru názvů.  
  
|Atribut|Účel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Definuje vlastní atribut, který určuje název sestavení pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definuje vlastní atribut, který určuje popis sestavení pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definuje vlastní atribut, který určuje konfiguraci sestavení (například maloobchodní nebo ladicí) pro manifest sestavení.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definuje popisný výchozí alias pro manifest sestavení.|  
  
## <a name="Obsolete"></a>Zastaralý atribut  
 `Obsolete` Atribut označuje entitu programu jako tu, která se už nedoporučuje používat. Každé použití entity označené jako zastaralé bude následně generovat upozornění nebo chybu v závislosti na tom, jak je atribut nakonfigurován. Příklad:  
  
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
  
 V tomto příkladu `Obsolete` je atribut použit pro třídu `A` a na metodu `B.OldMethod`. Vzhledem k tomu, že druhý argument konstruktoru atributu použité `B.OldMethod` pro je nastaven `true`na, tato metoda způsobí chybu kompilátoru, zatímco použití třídy `A` bude pouze generovat upozornění. Volání `B.NewMethod`však negeneruje žádné upozornění nebo chybu.  
  
 Řetězec poskytnutý jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby. Například když použijete s předchozími definicemi, následující kód vygeneruje dvě upozornění a jednu chybu:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Dvě upozornění pro třídu `A` jsou vygenerována: jedna pro deklaraci odkazu na třídu a druhá pro konstruktor třídy.  
  
 `Obsolete` Atribut lze použít bez argumentů, ale včetně vysvětlení, proč je položka zastaralá a co použít místo toho se doporučuje.  
  
 `Obsolete` Atribut je atribut s jedním použitím a lze jej použít pro libovolnou entitu, která povoluje atributy. `Obsolete`je alias pro <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a>Podmíněný atribut  
 `Conditional` Atribut provádí provádění metody závislé na identifikátoru předběžného zpracování. Atribut je alias pro <xref:System.Diagnostics.ConditionalAttribute>a lze jej použít pro metodu nebo třídu atributu. `Conditional`  
  
 V tomto příkladu se `Conditional` použije na metodu, která povolí nebo zakáže zobrazení diagnostických informací specifických pro program:  
  
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
  
 `TRACE_ON` Pokud identifikátor není definován, nebude zobrazen žádný výstup trasování.  
  
 Atribut se často používá `DEBUG` s identifikátorem pro povolení funkcí trasování a protokolování pro sestavení ladění, ale ne v sestaveních vydaných verzí, jako je: `Conditional`  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Když je volána metoda označená jako podmíněná, přítomnost nebo absence zadaného symbolu předzpracování určuje, zda je volání zahrnuto nebo vynecháno. Pokud je symbol definován, volání je zahrnuto; v opačném případě je volání vynecháno. Použití `Conditional` je čisticí, jasnější a méně náchylné k chybám, které lze použít jako alternativu k `#if…#endif` uzavření metod uvnitř bloků, například:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Podmíněná metoda musí být metoda v deklaraci třídy nebo struktury a nesmí mít návratovou hodnotu.  
  
### <a name="using-multiple-identifiers"></a>Použití více identifikátorů  
 Pokud má metoda více `Conditional` atributů, volání metody je zahrnuto, pokud je definován alespoň jeden z podmíněných symbolů (jinými slovy, symboly jsou logicky propojeny pomocí operátoru OR). V tomto příkladu přítomnost buď `A` nebo `B` , způsobí volání metody:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Chcete-li dosáhnout vlivu logického propojení symbolů pomocí operátoru AND, můžete definovat sériové podmíněné metody. Například druhá metoda níže se spustí pouze v případě, že jsou `A` definovány `B` obě i:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Použití podmíněné s třídami atributů  
 `Conditional` Atribut lze použít také pro definici třídy atributu. V tomto příkladu vlastní atribut `Documentation` přidá informace do metadat pouze v případě, že je definován ladění.  
  
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
 Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího.  
  
 Chcete-li získat informace o volajícím členu, použijte atributy, které se použijí na volitelné parametry. Každý volitelný parametr určuje výchozí hodnotu. V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> definovány v oboru názvů:  
  
|Atribut|Popis|type|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ze kterého je metoda volána.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo název vlastnosti volajícího. Další informace naleznete v tématu [informace o volajícímC#()](../caller-information.md).|`String`|  
  
 Další informace o atributech informace o volajícím naleznete v tématu [informaceC#o volajícím ()](../caller-information.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Průvodce programováním v jazyce C#](../../index.md)
- [Atributy](../../../../standard/attributes/index.md)
- [Reflexe (C#)](../reflection.md)
- [Přístup k atributům pomocí reflexe (C#)](./accessing-attributes-by-using-reflection.md)
