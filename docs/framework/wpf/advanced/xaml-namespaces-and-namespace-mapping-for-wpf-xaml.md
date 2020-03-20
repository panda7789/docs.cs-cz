---
title: Obory názvů XAML a mapování oborů názvů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
ms.openlocfilehash: 9b01643e8f8d77073595253580ebea60fabfd23b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186237"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Obor názvů XAML mapování oboru názvů pro WPF XAML
Toto téma dále vysvětluje přítomnost a účel dvou mapování oboru názvů XAML, které se často nacházejí v kořenové značce souboru WPF XAML. Také popisuje, jak vytvořit podobné mapování pro použití prvků, které jsou definovány ve vlastním kódu nebo v rámci samostatných sestavení.  

## <a name="what-is-a-xaml-namespace"></a>Co je obor názvů XAML?  
 Obor názvů XAML je ve skutečnosti rozšířením konceptu oboru názvů XML. Techniky určení oboru názvů XAML spoléhají na syntaxi oboru názvů XML, konvenci použití identifikátorů uris jako identifikátorů oboru názvů, použití předpon k poskytnutí prostředků pro odkaz ování více oborů názvů ze stejného zdroje značek a tak dále. Primární koncept, který je přidán do definice XAML oboru názvů XML je, že obor názvů XAML znamená jak rozsah jedinečnosti pro použití značek, tak také ovlivňuje, jak jsou značkovací entity potenciálně podporovány konkrétními obory názvů CLR a odkazovány Sestavení. Tato druhá úvaha je také ovlivněna konceptem kontextu schématu XAML. Ale pro účely fungování WPF s obory názvů XAML si obecně můžete myslet na obory názvů XAML z hlediska výchozího oboru názvů XAML, oboru názvů jazyka XAML a jakýchkoli dalších oborů názvů XAML mapovaných značkami XAML přímo na konkrétní záložní CLR obory názvů a odkazovaná sestavení.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>
## <a name="the-wpf-and-xaml-namespace-declarations"></a>Deklarace oboru názvů WPF a XAML  
 V rámci deklarací oboru názvů v kořenové značce mnoha souborů XAML uvidíte, že obvykle existují dvě deklarace oboru názvů XML. První deklarace mapuje celkový wpf klient / framework XAML obor názvů jako výchozí:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 Druhá deklarace mapuje samostatný obor názvů XAML a `x:` mapuje jej (obvykle) na předponu.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Vztah mezi těmito deklaracemi je, že mapování `x:` předpony podporuje vnitřní objekty, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou součástí definice jazyka XAML a je jedna implementace, která používá XAML jako jazyk a definuje slovník jeho objektů pro XAML. Vzhledem k tomu, že použití slovníku WPF bude mnohem běžnější než použití vnitřních prostorů XAML, je slovník WPF mapován jako výchozí.  
  
 Po `x:` konvenci předpony pro mapování podpory jazyka XAML následují šablony projektu, ukázkový kód a dokumentace funkcí jazyka v této sadě SDK. Obor názvů XAML definuje mnoho běžně používaných funkcí, které jsou nezbytné i pro základní aplikace WPF. Například chcete-li připojit libovolný kód na pozadí souboru XAML prostřednictvím částečné `x:Class` třídy, musíte pojmenovat tuto třídu jako atribut v kořenovém prvku příslušného souboru XAML. Nebo jakýkoli prvek, jak je definován na stránce XAML, které chcete `x:Key` získat přístup jako prostředek s klíčem by měl mít atribut nastavit na daný prvek. Další informace o těchto a dalších aspektech XAML naleznete v části [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) nebo [Syntaxe XAML podrobně .](xaml-syntax-in-detail.md)  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mapování na vlastní třídy a sestavení  
 Obory názvů XML můžete mapovat na sestavení pomocí `xmlns` řady tokenů v rámci deklarace předpony, podobně jako jsou standardní objekty názvů WPF a XAML-intrinsics XAML mapovány na předpony.  
  
 Syntaxe přebírá následující možné pojmenované tokeny a následující hodnoty:  
  
 `clr-namespace:`Clr obor názvů deklarované v rámci sestavení, který obsahuje veřejné typy vystavit jako prvky.  
  
 `assembly=`Sestavení, které obsahuje některé nebo všechny odkazované clr oboru názvů. Tato hodnota je obvykle pouze název sestavení, nikoli cesta a nezahrnuje rozšíření (například .dll nebo .exe). Cesta k tomuto sestavení musí být vytvořena jako odkaz na projekt v souboru projektu, který obsahuje xaml, který se pokoušíte mapovat. Chcete-li začlenit podepisování verzí `assembly` a podepisování silného názvu, může být hodnota řetězec definovaný písmenem <xref:System.Reflection.AssemblyName>a) spíše než jednoduchý název řetězce.  
  
 Všimněte si, že `clr-namespace` znak oddělující token od jeho hodnoty je dvojtečka (:) vzhledem k tomu, `assembly` že znak oddělující token od jeho hodnoty je znaménko rovná se (=). Znak, který chcete použít mezi těmito dvěma tokeny je středník. Také nezahrnejte žádné prázdné místo kdekoli v deklaraci.  
  
### <a name="a-basic-custom-mapping-example"></a>Příklad základního vlastního mapování  
 Následující kód definuje příklad vlastní třídy:  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 Tato vlastní třída je pak zkompilován do knihovny, která `SDKSampleLibrary`podle nastavení projektu (není zobrazena) je pojmenována .  
  
 Chcete-li odkazovat na tuto vlastní třídu, musíte ji také zahrnout jako referenci pro aktuální projekt, který byste obvykle udělali pomocí ui Průzkumníka řešení v sadě Visual Studio.  
  
 Nyní, když máte knihovnu obsahující třídu a odkaz na ni v nastavení projektu, můžete přidat následující mapování předpony jako součást kořenového prvku v XAML:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Chcete-li dát všechno dohromady, následující je XAML, který obsahuje vlastní mapování spolu s typické výchozí a x: mapování `ExampleClass` v kořenové značky, pak používá odkaz s předponou k vytvoření instance v tomto uživatelském prostředí:  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a>Mapování na aktuální sestavení  
 `assembly`lze vynechat, `clr-namespace` pokud je odkazovaný definován ve stejném sestavení jako kód aplikace, který odkazuje na vlastní třídy. Nebo ekvivalentní syntaxe pro tento `assembly=`případ je zadat , bez tokenu řetězce za znaménkem rovná se.  
  
 Vlastní třídy nelze použít jako kořenový prvek stránky, pokud je definován ve stejném sestavení. Částečné třídy není nutné mapovat; pouze třídy, které nejsou částečné třídy stránky v aplikaci je třeba mapovat, pokud máte v úmyslu odkazovat na ně jako prvky v XAML.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Mapování oborů názvů CLR na obory názvů XML v sestavení  
 WPF definuje atribut CLR, který je spotřebován procesory XAML za účelem mapování více oborů názvů CLR na jeden obor názvů XAML. Tento atribut <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, je umístěn na úrovni sestavení ve zdrojovém kódu, který vytváří sestavení. Zdrojový kód sestavení WPF používá tento atribut k mapování <xref:System.Windows> různých <xref:System.Windows.Controls>běžných `http://schemas.microsoft.com/winfx/2006/xaml/presentation` oborů názvů, například a , do oboru názvů.  
  
 Trvá <xref:System.Windows.Markup.XmlnsDefinitionAttribute> dva parametry: název oboru názvů XML/XAML a název oboru názvů CLR. Více než <xref:System.Windows.Markup.XmlnsDefinitionAttribute> jeden může existovat pro mapování více oborů názvů CLR na stejný obor názvů XML. Po namapování mohou být členové těchto oborů názvů také odkazováni `using` bez úplné kvalifikace, pokud je to žádoucí, poskytnutím příslušného příkazu na stránce s kódem částečné třídy. Další podrobnosti <xref:System.Windows.Markup.XmlnsDefinitionAttribute>naleznete v tématu .  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Návrhářoborů názvů a dalších předponek ze šablon XAML  
 Pokud pracujete s vývojovými prostředími a/nebo návrhovými nástroji pro WPF XAML, můžete si všimnout, že existují další definované obory názvů XAML / předpony v rámci značek XAML.  
  
 WPF Designer pro Visual Studio používá obor názvů návrháře, `d:`který je obvykle mapován na předponu . Novější šablony projektů pro WPF může předem mapovat tento obor názvů XAML pro podporu výměny XAML mezi WPF Designer pro Visual Studio a další chod návrhu. Tento obor názvů XAML se používá k zachování stavu návrhu při zaokrouhlování uživatelského rozhraní založeného na XAML v návrháři. Používá se také pro `d:IsDataSource`funkce, jako je například , které umožňují zdroje dat za běhu v návrháři.  
  
 Další předpona, která `mc:`se může zobrazit mapovaná, je . `mc:`je pro kompatibilitu značek a využívá vzor kompatibility značek, který není nutně specifický pro XAML. Do určité míry funkce kompatibility značek lze použít k výměně XAML mezi rámci nebo přes jiné hranice implementace zálohování, práce mezi kontexty schématu XAML, poskytují kompatibilitu pro omezené režimy v návrháři a tak dále. Další informace o konceptech kompatibility značek a jejich vztahu k WPF naleznete v [tématu Kompatibilita značek (mc:) Funkce jazyka](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF a načítání sestavy  
 Kontext schématu XAML pro WPF integruje s modelem aplikace WPF, který <xref:System.AppDomain>zase používá clr definovaný koncept . Následující sekvence popisuje, jak kontext schématu XAML interpretuje, jak buď načíst sestavení nebo najít typy v <xref:System.AppDomain> době běhu nebo návrhu, na základě WPF použití a další faktory.  
  
1. Iterát přes <xref:System.AppDomain>, hledá již načtené sestavení, které odpovídá všem aspektům názvu, počínaje naposledy načtené sestavení.  
  
2. Pokud je název kvalifikovaný, zavolejte <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
3. Pokud krátký název + token veřejného klíče kvalifikovaného názvu odpovídá sestavení, ze kterého byla načtena značka, vraťte toto sestavení.  
  
4. Použijte krátký název + token <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>veřejného klíče pro volání .  
  
5. Pokud název není úplný, <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>volejte .  
  
 Volný XAML nepoužívá krok 3; není žádné načtené z sestavení.  
  
 Kompilovaný XAML pro WPF (generovaný pomocí XamlBuildTask) nepoužívá <xref:System.AppDomain> již načtená sestavení z (krok 1). Název by také nikdy neměl být neúplný z výstupu XamlBuildTask, takže krok 5 se nevztahuje.  
  
 Kompilované BAML (generované prostřednictvím PresentationBuildTask) používá všechny kroky, i když BAML také by nemělobsahovat neúplné názvy sestavení.  
  
## <a name="see-also"></a>Viz také

- [Principy oborů názvů XML](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
