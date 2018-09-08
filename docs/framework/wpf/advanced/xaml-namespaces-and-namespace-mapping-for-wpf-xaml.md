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
ms.openlocfilehash: 9e93d3cd417d0d075fcebb8327ec51799884f8d6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178140"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Obor názvů XAML mapování oboru názvů pro WPF XAML
Dále toto téma vysvětluje přítomnost a účel dvě tak často, nenašla v kořenovém tagu souboru WPF XAML mapování oboru názvů XAML. Také popisuje, jak vytvořit podobná mapování pro elementy, které jsou definovány ve svém vlastním kódu a/nebo v rámci samostatné sestavení pomocí.  
  
  
## <a name="what-is-a-xaml-namespace"></a>Co je Namespace XAML?  
 Obor názvů XAML je ve skutečnosti rozšíření konceptu oboru názvů XML. Techniky pro určení oboru názvů XAML využívají syntaxi XML obor názvů, konvenci pomocí identifikátorů URI jako identifikátory oboru názvů pomocí předpony poskytují způsob odkazovat více oborů názvů z jednoho zdroje značek a tak dále. Primární pojem, který je přidán do XAML definici oboru názvů XML je, že obor názvů XAML zahrnuje obě obor jedinečnosti pro použití značek a také ovlivňuje, jak jsou značek entit potenciálně se opírá o konkrétních oborů názvů CLR a odkazované sestavení. Tento druhý faktor je také ovlivněno koncept kontext schématu XAML. Ale pro účely fungování WPF s obory názvů XAML, můžete obvykle představit obory názvů XAML z hlediska výchozí obor názvů XAML, oboru názvů jazyka XAML a všech dalších XAML názvových prostorů namapována ve vašem kódu XAML přímo na konkrétní základní typ CLR obory názvů a odkazovaných sestavení.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>Deklarace Namespace XAML ve WPF  
 V rámci deklarace oboru názvů v kořenovém tagu s mnoha soubory XAML zobrazí se, že jsou obvykle dvě deklarace oboru názvů XML. První deklarace mapuje celkové klienta WPF nebo obor názvů XAML framework jako výchozí:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 Druhý deklarace mapuje samostatný obor názvů XAML mapování (obvykle) na `x:` předponu.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Vztah mezi tyto deklarace je, že `x:` mapování předpony podporuje vnitřních objektů, které jsou součástí definice jazyka XAML a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je jedna implementace, která používá XAML jako jazyk a definuje slovník z jeho objekty pro XAML. Použití slovníku WPF bude mnohem častější než použití – vnitřní prvky XAML, proto slovníku WPF je mapován jako výchozí.  
  
 `x:` Předponu konvence pro mapování podpory – vnitřní prvky jazyka XAML je následována šablony projektů, ukázkový kód a dokumentace jazykové funkce v rámci této [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Obor názvů XAML definuje mnoho běžně používaných funkcí, které jsou nezbytné pro základní aplikace WPF i. Například, aby bylo možné připojit k žádné použití modelu code-behind do souboru XAML prostřednictvím částečné třídy, je nutné pojmenovat tuto třídu jako `x:Class` atribut v kořenovém prvku příslušný soubor XAML. Nebo libovolný element, jak jsou definovány v stránku XAML, který budete chtít získat přístup jako prostředek s klíčem by měla mít `x:Key` atribut nastaven pro element. Další informace o těchto a dalších aspektů XAML naleznete v tématu [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) nebo [syntaxe XAML v podrobnosti o](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mapování vlastní třídy a sestavení  
 Obory názvů XML můžete namapovat na sestavení pomocí řady tokenů v rámci `xmlns` předpony prohlášení, podobně jako standardní WPF a XAML – vnitřní funkce XAML obory názvů zpřístupněných předpony.  
  
 Přijímá syntaxi následující možné pojmenované tokeny a následující hodnoty:  
  
 `clr-namespace:` Obor názvů CLR deklarované v rámci sestavení, které obsahuje veřejné typy jsou elementy.  
  
 `assembly=` Sestavení, které obsahuje některé nebo všechny odkazované [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] oboru názvů. Tato hodnota je obvykle pouze název sestavení, ne cestu a nezahrnuje příponu (třeba .dll nebo .exe). Cesta k sestavení musí vytvořit jako odkaz na projekt v souboru projektu, který obsahuje XAML, který se pokoušíte mapování. Aby bylo možné začlenit správu verzí a podepisování se silným názvem, `assembly` hodnota může být řetězec, tak jak je definoval <xref:System.Reflection.AssemblyName>, místo názvu jednoduchým řetězcem.  
  
 Všimněte si, že znak oddělující `clr-namespace` token z jeho hodnota je dvojtečkou (:), zatímco znak oddělující `assembly` token z jeho hodnota je znak rovná se (=). Znak, který mezi těmito dvěma tokeny je středníkem. Také nezahrnujte žádné prázdné znaky. kdekoli v deklaraci.  
  
### <a name="a-basic-custom-mapping-example"></a>Příklad základního vlastní mapování  
 Následující kód definuje vlastní třídu příkladu:  
  
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
  
 Tato vlastní třída je kompilována potom do knihovny, který se nazývá podle nastavení projektu (není vidět) `SDKSampleLibrary`.  
  
 Aby bylo možné odkazovat tento vlastní třídu, musíte také zahrnout jako reference pro aktuální projekt, která by obvykle děláte přes uživatelské rozhraní Průzkumníka řešení v sadě Visual Studio.  
  
 Teď, když máte knihovnu obsahující třídu a na ni odkaz v nastavení projektu, můžete přidat následující mapování předpony jako součást kořenovém prvku v XAML:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Na všech součástí dohromady, následuje XAML, která obsahuje vlastní mapování spolu s typický výchozí a x: mapování v kořenovém tagu, a pak používá předponou odkaz pro vytvoření instance `ExampleClass` v toto uživatelské rozhraní:  
  
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
 `assembly` lze vynechat, pokud `clr-namespace` odkazované definuje se v rámci stejného sestavení jako kód aplikace, který odkazuje na vlastní třídy. Nebo ekvivalentní syntax pro tento případ je zadání `assembly=`, s žádný řetězec s tokenem za znaménko rovná se.  
  
 Vlastní třídy nelze použít jako kořenový element na stránce, pokud definována ve stejném sestavení. Částečné třídy není nutné mapovat; pouze třídy, které nejsou částečné třídy stránky v aplikaci potřeba namapovat, pokud chcete odkazovat na ně jako elementů v XAML.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Mapování oborů názvů CLR na obory názvů XML v sestavení  
 WPF definuje atribut CLR, která se využívá pomocí XAML procesorů, aby bylo možné mapovat více oborů názvů CLR do jednoho oboru názvů XAML. Tento atribut <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, je umístěn na úrovni sestavení ve zdrojovém kódu, který vytváří sestavení. Zdrojový kód WPF sestavení používá tento atribut mapovat různé běžné obory názvů, jako například <xref:System.Windows> a <xref:System.Windows.Controls>, možnosti [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] oboru názvů.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Přebírá dva parametry: název oboru názvů XML/XAML a název oboru názvů CLR. Více než jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> může existovat více oborů názvů CLR přiřadit stejný obor názvů XML. Jakmile mapován, členy z těchto oborů názvů lze také odkazovat bez úplné kvalifikace v případě potřeby tím, že poskytuje odpovídající `using` příkaz v kódu částečné třídy stránky. Další podrobnosti najdete v tématu <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Návrháře obory názvů a jiné předpony ze šablon XAML  
 Pokud pracujete s vývojářským prostředím a/nebo nástroje pro návrh pro WPF XAML, můžete si všimnout, že se ostatní definované obory názvů XAML / předpony adres v rámci značky XAML.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] pomocí návrháře, který je obvykle namapovaný na předponu oboru názvů `d:`. Tento obor názvů XAML pro podporu výměny XAML mezi předem namapovat novější šablony projektů pro WPF [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] a jiných prostředích návrhu. Tento obor názvů XAML návrhu slouží k perpetuate stav návrhu při vracení uživatelského rozhraní založeného na XAML v návrháři. Používá se i pro funkce, jako `d:IsDataSource`, která umožňují zdroje dat modulu runtime v návrháři.  
  
 Může se zobrazit jinou předponu namapované je `mc:`. `mc:` je z důvodu kompatibility značek a využívá vzor kompatibility značek, který není nutně specifické pro XAML. Do určité míry kompatibility značek, funkce se dá použít k výměně XAML mezi rozhraní nebo jiné hranice implementace základní práci mezi kontext schématu XAML, zajištění kompatibility pro omezené režimy v některém z návrhářů a tak dále. Další informace o konceptech kompatibility značek a jejich vzájemné vztahy k použití WPF v tématu [kompatibility značek (mc:) Funkce jazyka](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF a načítání sestavení  
 Kontext WPF schématu XAML se integruje s modelem aplikace WPF, která dále používá koncept CLR definované <xref:System.AppDomain>. Následující text popisuje, jak interpretovat kontext schématu XAML načtení sestavení nebo najít typy v době běhu nebo návrhu, založený na použití WPF <xref:System.AppDomain> a dalších faktorů.  
  
1.  Iterovat přes <xref:System.AppDomain>, hledání, který odpovídá všechny aspekty název sestavení již načtena, počínaje naposledy načteného sestavení.  
  
2.  Pokud je kvalifikovaný název, volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
3.  Pokud krátký název a token veřejného klíče úplný název odpovídá kódu načteného ze sestavení, vraťte se na toto sestavení.  
  
4.  Použít krátký název a token veřejného klíče pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
5.  Pokud neúplný název, volání <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Volný XAML nepoužívá kroku 3; neexistuje žádné načten ze sestavení.  
  
 Kompilované XAML pro WPF (vygenerovali přes XamlBuildTask) nepoužívá sestavení již načtena z <xref:System.AppDomain> (krok 1). Název by nikdy nekvalifikované z výstupu XamlBuildTask tak kroku 5 se nedá použít.  
  
 Kompilované BAML (vygenerovali přes PresentationBuildTask) používá všechny kroky, i když BAML také by neměly obsahovat názvy nekvalifikované sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Obory názvů XML](https://go.microsoft.com/fwlink/?LinkId=98069)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
