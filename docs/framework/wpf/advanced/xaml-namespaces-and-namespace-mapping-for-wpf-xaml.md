---
title: "Obor názvů XAML mapování oboru názvů pro WPF XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80f152f8cdf459f920d723df66756af680b4bcea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Obor názvů XAML mapování oboru názvů pro WPF XAML
Dále toto téma vysvětluje přítomnosti a účel dvě mapování oboru názvů jazyka XAML tak často, nalézt ve značce kořenového souboru WPF XAML. Také popisuje, jak vytvořit podobná mapování pro používání prvky, které jsou definovány v kódu nebo v samostatné sestavení.  
  
  
## <a name="what-is-a-xaml-namespace"></a>Co je XAML Namespace?  
 Oboru názvů jazyka XAML je ve skutečnosti rozšíření konceptu oboru názvů XML. Techniky sloužící k určení oboru názvů jazyka XAML spoléhají na syntaxi obor názvů XML, konvence pomocí identifikátory URI jako identifikátory obor názvů, pomocí předpony použití prostředků z jednoho zdroje značek odkazovat více obory názvů a tak dále. Primární pojem, který je přidán do definice XAML obor názvů XML je, že znamená i na rozsah jedinečnosti pro použití značek oboru názvů jazyka XAML a také vliv jak jsou zajišťované konkrétní obory názvů CLR a odkazuje značek entit potenciálně sestavení. Tato tato podmínka je ovlivněny také koncepci kontext schématu XAML. Ale pro účely fungování WPF s obory názvů jazyka XAML, si můžete obecně představit obory názvů jazyka XAML z hlediska výchozí obor názvů jazyka XAML, obor názvů jazyka XAML a všechny další obory názvů jazyka XAML jako mapovat pomocí vašeho kódu XAML přímo na konkrétní základní typ CLR obory názvů a odkazované sestavení.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF a deklarace Namespace XAML  
 V rámci deklarace oboru názvů v kořenovou značku mnoho souborů XAML uvidíte, že nejsou obvykle dva deklarace oboru názvů XML. První deklaraci mapuje celkové WPF klienta nebo oboru názvů jazyka XAML framework jako výchozí:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 Druhý deklaraci mapuje samostatného oboru názvů jazyka XAML (obvykle) pro mapování `x:` předponu.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Vztah mezi tyto deklarace je, že `x:` mapování předpony podporuje vnitřní funkce, které jsou součástí definici jazyka XAML a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je jeden implementace, která používá jako jazyk XAML a definuje termínů z jeho objekty pro jazyk XAML. Vzhledem k použití WPF termínů budou mnohem častější než použití vnitřní funkce jazyka XAML, termínů WPF je namapovaný jako výchozí.  
  
 `x:` Předponu konvence pro mapování podporu vnitřní funkce jazyka XAML šablony projektů, následuje ukázkový kód a dokumentace jazyka funkce v rámci to [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Oboru názvů jazyka XAML definuje řadu běžně používané funkcí, které jsou nezbytné i pro základní aplikace WPF. Pro instanci, aby bylo možné připojit žádné kódu do souboru XAML prostřednictvím částečné třídy, je třeba zadat název třídy jako `x:Class` atribut v kořenovém elementu relevantní souboru XAML. Nebo libovolný element, jak jsou definovány v stránky XAML, který chcete pro přístup k jako prostředek s klíčem musí mít `x:Key` atribut nastavené u elementu. Další informace o těchto a dalších aspektů XAML najdete v části [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) nebo [XAML syntaxe v podrobností](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mapování na vlastní třídy a sestavení  
 Obory názvů XML můžete namapovat k sestavení s pomocí řady tokenů v rámci `xmlns` předpony deklarace, podobně jako jak jsou mapovány standardní WPF a XAML – vnitřní funkce obory názvů jazyka XAML na předpony.  
  
 Syntaxe trvá následující možné pojmenované tokeny a následující hodnoty:  
  
 `clr-namespace:`Obor názvů CLR deklarované v rámci sestavení, které obsahuje veřejné typy vystavit jako elementy.  
  
 `assembly=`Sestavení, které obsahuje některé nebo všechny odkazovaná [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] oboru názvů. Tato hodnota je obvykle jen název sestavení, ne cestu a nezahrnuje příponu (například .dll nebo .exe). Cesta k této sestavě je nutné vytvořit jako odkaz na projekt v souboru projektu, který obsahuje XAML chcete namapovat. Aby bylo možné začlenit správu verzí a podpis silného názvu `assembly` hodnota může být řetězec, podle definice <xref:System.Reflection.AssemblyName>, namísto názvu jednoduchým řetězcem.  
  
 Všimněte si, že znak oddělující `clr-namespace` tokenu z její hodnota je dvojtečkou (:), zatímco znak oddělení `assembly` token z její hodnota je znak rovná se (=). Znak, který má používat mezi tyto dvě tokeny je středníkem. Navíc nebudou obsahovat žádné prázdné kdekoli v deklaraci.  
  
### <a name="a-basic-custom-mapping-example"></a>Příklad základní vlastní mapování  
 Následující kód definuje třídu vlastní příklad:  
  
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
  
 Tato vlastní třída je pak zkompiluje do knihovny, který podle nastavení projektu (není vidět) je název `SDKSampleLibrary`.  
  
 Chcete-li odkazovat na tuto vlastní třídu, musíte taky zahrnout jako odkaz pro aktuální projekt, který by obvykle děláte pomocí uživatelského rozhraní Průzkumníka řešení v sadě Visual Studio.  
  
 Teď, když máte knihovny obsahující třídy a odkaz na jeho v nastavení projektu, můžete přidat následující mapování předpony v rámci vaší kořenový element v jazyce XAML:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Na všech součástí dohromady, následuje XAML, který obsahuje vlastní mapování společně s typický výchozí mapování x: v kořenovou značku a potom používá předponou odkaz k vytvoření instance `ExampleClass` v této uživatelského rozhraní:  
  
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
 `assembly`Pokud lze vynechat `clr-namespace` odkazované je definovaný v rámci stejného sestavení jako aplikační kód, který odkazuje na vlastní třídy. Nebo ekvivalentní syntaxe pro tento případ slouží k zadání `assembly=`, s tokenem žádné řetězce následující symbolem rovná se.  
  
 Vlastní třídy nelze použít jako kořenový element stránky, pokud definované ve stejném sestavení. Částečné třídy nemusíte mapovat; pouze třídy, které nejsou třídu stránky v vaše aplikace musí být mapován, pokud máte v úmyslu odkazujte na ně jako elementy v jazyce XAML.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Obory názvů CLR mapování na obory názvů XML v sestavení  
 WPF definuje atribut CLR, který procesory XAML při mapování více obory názvů CLR do jednoho oboru názvů jazyka XAML. Tento atribut <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, je umístěn na úrovni sestavení ve zdrojovém kódu, který produkuje sestavení. Zdrojový kód sestavení WPF používá tento atribut mapovat různé běžné obory názvů, jako například <xref:System.Windows> a <xref:System.Windows.Controls>do [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] oboru názvů.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Přebírá dva parametry: název oboru názvů XML nebo XAML a název oboru názvů CLR. Více než jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> může existovat více obory názvů CLR mapovat do stejného oboru názvů XML. Jakmile namapovány, členové obory názvů lze také odkazovat bez úplné kvalifikace v případě potřeby tím, že poskytuje odpovídající `using` příkaz na stránce částečné třídy kódu. Další podrobnosti najdete v tématu <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Návrhář obory názvů a dalšími předponami ze šablon XAML  
 Pokud pracujete s vývojových prostředí nebo nástrojů návrhu pro jazyk XAML WPF, můžete si všimnout, že jsou ostatní definované obory názvů jazyka XAML / předpony v rámci kód XAML.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]používá návrháře obor názvů, který je obvykle namapována na předponu `d:`. Novější šablony projektů pro grafický subsystém WPF předem namapovat, může tento obor názvů jazyka XAML pro podporu výměny XAML mezi [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] a dalších prostředích s návrhu. Tento obor názvů jazyka XAML návrhu se používá k perpetuate stav návrhu při vracení založených na XAML uživatelského rozhraní v návrháři. Používá se také pro funkce, jako `d:IsDataSource`, která umožňují zdroje dat modulu runtime v návrháře.  
  
 Může se zobrazit další předpona namapované je `mc:`. `mc:`je pro kompatibilitu značek a jsou využívány vzor kompatibility kód, který není nutně specifické pro jazyk XAML. Do určité míry kompatibility značek, které funkce lze použít k výměně XAML mezi architektury nebo bez ohledu na ostatní hranice základní implementace spolupráce mezi kontexty schématu XAML, zajišťují kompatibilitu pro omezené režimy v návrháři a tak dále. Další informace o konceptech kompatibility značek a jak se vztahují k WPF najdete v tématu [kompatibility značek (mc:) Jazykové funkce](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF a načtení sestavení  
 Kontext WPF schématu XAML integruje s modelem aplikace WPF, které dále používá koncept definované CLR <xref:System.AppDomain>. Následující text popisuje, jak interpretovat kontext schématu XAML jak načíst sestavení nebo najít typy v době běhu nebo návrhu, založené na použití WPF <xref:System.AppDomain> a dalších faktorů.  
  
1.  Iterace <xref:System.AppDomain>, hledá již načíst sestavení, která odpovídají všechny aspekty název, od naposledy načíst sestavení.  
  
2.  Pokud je kvalifikovaný název, volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
3.  Pokud krátký název + token veřejného klíče kvalifikovaný název odpovídá sestavení, které kód byl načten z, vrátí této položky assembly.  
  
4.  Použít krátký název + tokenu veřejného klíče pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
5.  Pokud neúplný název, volání <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Přijít XAML nepoužívá krok 3; neexistuje žádné sestavení načíst z.  
  
 Kompilované XAML pro grafický subsystém WPF (vygenerovaný prostřednictvím XamlBuildTask) nepoužívá sestavení již načten z <xref:System.AppDomain> (krok 1). Název by měl nikdy neúplné z výstupu XamlBuildTask tak nelze použít krok 5.  
  
 Kompilované BAML (vygenerovaný prostřednictvím PresentationBuildTask) používá všechny kroky, i když BAML také by neměly obsahovat názvy nekvalifikované sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Obory názvů XML](http://go.microsoft.com/fwlink/?LinkId=98069)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
