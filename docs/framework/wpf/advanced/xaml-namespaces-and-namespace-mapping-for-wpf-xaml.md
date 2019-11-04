---
title: Obor názvů XAML mapování oboru názvů pro WPF XAML
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
ms.openlocfilehash: 6c06e18f7869f1b1041c4d5fb1608a87f2902d7b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460572"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Obor názvů XAML mapování oboru názvů pro WPF XAML
Toto téma dále vysvětluje přítomnost a účel dvou mapování oboru názvů XAML, jak se často nacházejí v kořenové značce souboru XAML WPF. Popisuje také, jak vydávat podobná mapování pro použití elementů, které jsou definovány ve vlastním kódu, a/nebo v samostatných sestaveních.  

## <a name="what-is-a-xaml-namespace"></a>Co je obor názvů XAML?  
 Obor názvů XAML je ve skutečnosti rozšíření konceptu oboru názvů XML. Techniky určení oboru názvů XAML spoléhají na syntaxi oboru názvů XML, konvence použití identifikátorů URI jako identifikátorů oboru názvů s použitím předpon k poskytnutí prostředků pro odkazování na více oborů názvů ze stejného zdroje kódu a tak dále. Primární koncept přidaný do definice XAML oboru názvů XML je, že obor názvů XAML předpokládá rozsah jedinečnosti pro použití značek a také ovlivňuje, jak jsou entity značek potenciálně zajištěny konkrétními obory názvů CLR a odkazovány shromáždění. Tato druhá úvaha je ovlivněna také konceptem kontextu schématu XAML. Pro účely toho, jak WPF funguje s obory názvů XAML, si obecně můžete představit obory názvů XAML v souvislosti s výchozím oborem názvů XAML, oborem názvů jazyka XAML a dalšími obory názvů XAML, jak jsou mapovány pomocí kódu jazyka XAML přímo na konkrétní modul CLR pro zálohování. obory názvů a odkazovaná sestavení.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>Deklarace oboru názvů WPF a XAML  
 V rámci deklarací oboru názvů v kořenové značce mnoha souborů XAML se zobrazí, že existují obvykle dvě deklarace oboru názvů XML. První deklarace mapuje celkový obor názvů klienta WPF/Framework XAML jako výchozí:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 Druhá deklarace namapuje samostatný obor názvů XAML, namapuje ho (obvykle) na předponu `x:`.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Vztah mezi těmito deklaracemi je, že mapování předpon `x:` podporuje vnitřní objekty, které jsou součástí definice jazyka XAML, a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je jedna implementace, která používá XAML jako jazyk a definuje slovní seznam svých objektů pro XAML. Vzhledem k tomu, že použití slovníku WPF bude mnohem běžnější než použití vnitřních objektů XAML, je slovník WPF namapovaný jako výchozí.  
  
 Konvence prefixu `x:` pro mapování podpory vnitřních kódů jazyka XAML je následována šablonami projektu, ukázkovým kódem a dokumentací funkcí jazyka v rámci této [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Obor názvů XAML definuje mnoho běžně používaných funkcí, které jsou nezbytné i pro základní aplikace WPF. Chcete-li například připojit jakýkoliv kód na pozadí k souboru XAML prostřednictvím částečné třídy, je nutné tuto třídu pojmenovat jako atribut `x:Class` v kořenovém elementu příslušného souboru XAML. Nebo jakýkoli element definovaný na stránce XAML, ke které chcete přistupovat jako prostředek s klíčem, by měl mít atribut `x:Key` nastaven na daném elementu. Další informace o těchto a dalších aspektech jazyka XAML naleznete v tématu detailed [XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) nebo [syntaxe jazyka XAML](xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mapování na vlastní třídy a sestavení  
 Můžete namapovat obory názvů XML na sestavení pomocí řady tokenů v rámci deklarace předpony `xmlns`, podobně jako standardní obory názvů jazyka WPF a XAML – vnitřní objekty XAML jsou mapovány na předpony.  
  
 Syntaxe přijímá následující možné pojmenované tokeny a následující hodnoty:  
  
 `clr-namespace:` obor názvů CLR deklarovaný v sestavení, které obsahuje veřejné typy k vystavení jako elementy.  
  
 `assembly=` sestavení, které obsahuje některé nebo všechny odkazované obory názvů CLR. Tato hodnota je obvykle pouze název sestavení, nikoli cesta a neobsahuje příponu (například. dll nebo. exe). Cesta k sestavení musí být vytvořena jako odkaz na projekt v souboru projektu, který obsahuje kód XAML, který se pokoušíte namapovat. Aby bylo možné začlenit správu verzí a podepisování silného názvu, `assembly` hodnota může být řetězec definovaný pomocí <xref:System.Reflection.AssemblyName>namísto jednoduchého názvu řetězce.  
  
 Všimněte si, že znak oddělující `clr-namespace` token od jeho hodnoty je dvojtečka (:) vzhledem k tomu, že znak oddělující `assembly` token od jeho hodnoty je znak rovná se (=). Znak, který se má použít mezi těmito dvěma tokeny, je středníkem. Také nezahrnujte prázdné znaky kdekoli v deklaraci.  
  
### <a name="a-basic-custom-mapping-example"></a>Příklad základního vlastního mapování  
 Následující kód definuje ukázkovou vlastní třídu:  
  
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
  
 Tato vlastní třída se pak zkompiluje do knihovny, která je na základě nastavení projektu (nezobrazená) pojmenována `SDKSampleLibrary`.  
  
 Aby bylo možné odkazovat na tuto vlastní třídu, je nutné ji také zahrnout jako referenci pro aktuální projekt, který byste obvykle použili Průzkumník řešení uživatelské rozhraní v aplikaci Visual Studio.  
  
 Teď, když máte knihovnu obsahující třídu a odkaz na ni v nastavení projektu, můžete přidat následující mapování předpony jako součást svého kořenového prvku v jazyce XAML:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Pro všechny dohromady je to XAML, který obsahuje vlastní mapování spolu s typickými výchozími a x: mapování v kořenové značce a pak používá předem pevný odkaz pro vytvoření instance `ExampleClass` v tomto uživatelském rozhraní:  
  
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
 `assembly` může být vynechána, pokud je `clr-namespace` odkaz definována v rámci stejného sestavení jako kód aplikace, který odkazuje na vlastní třídy. Nebo ekvivalentní syntaxe pro tento případ je zadání `assembly=`, bez řetězcového tokenu za znaménkem rovná se.  
  
 Vlastní třídy nelze použít jako kořenový element stránky, je-li definována ve stejném sestavení. Částečné třídy není nutné namapovat; Pokud máte v úmyslu odkazovat jako elementy v jazyce XAML, je nutné namapovat pouze třídy, které nejsou dílčí třídou stránky v aplikaci.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Mapování oborů názvů CLR na obory názvů XML v sestavení  
 WPF definuje atribut CLR, který používají procesory XAML za účelem mapování více oborů názvů CLR na jeden obor názvů XAML. Tento atribut, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, je umístěn na úrovni sestavení ve zdrojovém kódu, který vytváří sestavení. Zdrojový kód sestavení WPF používá tento atribut k mapování různých běžných oborů názvů, například <xref:System.Windows> a <xref:System.Windows.Controls>, na obor názvů [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)].  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> přebírá dva parametry: název oboru názvů XML/XAML a název oboru názvů CLR. Pro mapování více oborů názvů CLR na stejný obor názvů XML může existovat více než jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Po namapování můžou být členové těchto oborů názvů odkazováni bez plné kvalifikace, pokud je to žádoucí, poskytnutím odpovídajícího `using`ho příkazu na stránce s kódem na pozadí částečné třídy. Další podrobnosti najdete v tématu <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Obory názvů návrháře a jiné předpony ze šablon XAML  
 Pokud pracujete s vývojovým prostředím a/nebo návrhovými nástroji pro WPF XAML, můžete si všimnout, že v kódu XAML jsou jiné definované obory názvů nebo předpony XAML.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] používá obor názvů návrháře, který je obvykle namapován na předponu `d:`. Novější šablony projektů pro WPF mohou předem mapovat tento obor názvů XAML pro podporu výměny XAML mezi [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] a dalšími návrhovými prostředími. Tento návrh oboru názvů jazyka XAML slouží k perpetuateí stavu návrhu, zatímco v Návrháři roundtripping uživatelské rozhraní založené na jazyce XAML. Používá se také pro funkce, jako je `d:IsDataSource`, které povolují běhové zdroje dat v návrháři.  
  
 Další předpona, která se může zobrazit, je `mc:`. `mc:` je pro kompatibilitu značek a využívá vzor kompatibility značek, který není nutně specifický pro XAML. V některých případech se funkce kompatibility značek dají použít k výměně XAML mezi architekturami nebo napříč ostatními hranicemi implementace zálohování, práci mezi kontexty schématu XAML, zajištění kompatibility pro omezené režimy v návrhářích a tak dále. Další informace o konceptech kompatibility značek a o tom, jak se vztahují k platformě WPF, najdete v tématu [Kompatibilita značek (MC:). Jazykové funkce](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF a načítání sestavení  
 Kontext schématu XAML pro WPF se integruje s aplikačním modelem WPF, který zase používá koncept <xref:System.AppDomain>definovaný pro CLR. Následující text popisuje, jak kontext schématu XAML interpretuje jak načíst sestavení nebo najít typy v době běhu nebo v době návrhu, na základě použití <xref:System.AppDomain> a dalších faktorů.  
  
1. Iterujte pomocí <xref:System.AppDomain>a vyhledáte již načtené sestavení, které odpovídá všem aspektům názvu, počínaje od posledního načteného sestavení.  
  
2. Pokud je název kvalifikován, zavolejte <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> v kvalifikovaném názvu.  
  
3. Pokud se krátké jméno a token veřejného klíče kvalifikovaného názvu shodují se sestavením, ze kterého byl kód načten, vraťte toto sestavení.  
  
4. K volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>použijte krátký název a token veřejného klíče.  
  
5. Pokud je název neúplný, zavolejte <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Volný kód XAML nepoužívá krok 3; neexistuje žádné načtené sestavení.  
  
 Kompilovaný kód XAML pro WPF (generovaný přes XamlBuildTask) nepoužívá již načtená sestavení z <xref:System.AppDomain> (krok 1). Název by neměl být nikdy neúplný z výstupu XamlBuildTask, takže krok 5 se nepoužije.  
  
 Kompilovaný BAML (generovaný přes PresentationBuildTask) používá všechny kroky, i když BAML by neměl obsahovat také nekvalifikované názvy sestavení.  
  
## <a name="see-also"></a>Viz také:

- [Porozumění oborům názvů XML](https://go.microsoft.com/fwlink/?LinkId=98069)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
