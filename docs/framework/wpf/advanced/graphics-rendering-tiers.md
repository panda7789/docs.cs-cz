---
title: Vrstvy vykreslování grafiky
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- rendering graphics [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
ms.openlocfilehash: b5bedae16a6c53aebf4d577b8cd812da992106f2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629893"
---
# <a name="graphics-rendering-tiers"></a>Vrstvy vykreslování grafiky
Vrstva vykreslování definuje úroveň grafického hardwaru a výkonu pro zařízení, na kterém běží [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  

<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Grafický hardware  
 Funkce grafického hardwaru, které mají největší vliv na úrovně vrstev vykreslování:  
  
- **Video RAM** Množství videopaměti v grafickém hardwaru určuje velikost a počet vyrovnávacích pamětí, které lze použít k skládání grafiky.  
  
- **Pixel shader** Pixel shader je funkce pro zpracování grafiky, která počítá efekty na základě jednotlivých pixelů. V závislosti na rozlišení zobrazené grafiky může být pro každý zobrazovací rámeček zpracováno několik milionů pixelů, které je třeba zpracovat.  
  
- **Vertex shader** Vertex shader je funkce pro zpracování grafiky, která provádí matematické operace s daty vrcholu objektu.  
  
- **Podpora více textur** Podpora více textur odkazuje na možnost použití dvou nebo více různých textur během operace prolnutí u objektu 3D grafiky. Úroveň podpory více textur je určena počtem jednotek s více texturami v grafickém hardwaru.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Definice vrstev vykreslování  
 Funkce grafického hardwaru určují schopnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování aplikace. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Systém definuje tři úrovně vykreslování:  
  
- **Vrstva vykreslování 0** Žádná hardwarová akcelerace grafiky Všechny grafické funkce používají akceleraci softwaru. Úroveň verze DirectX je nižší než verze 9,0.  
  
- **Vrstva vykreslování 1** Některé grafické funkce využívají hardwarovou akceleraci grafiky. Úroveň verze DirectX je větší nebo rovna verzi 9,0.  
  
- **Vrstva vykreslování 2** Většina grafických funkcí používá hardwarovou akceleraci grafiky. Úroveň verze DirectX je větší nebo rovna verzi 9,0.  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> Vlastnost umožňuje načíst úroveň vykreslování při běhu aplikace. Pomocí vrstvy vykreslování zjistíte, jestli zařízení podporuje určité grafické funkce akcelerované hardwarem. Aplikace pak může v době běhu v závislosti na vrstvě vykreslování, kterou zařízení podporuje, použít různé cesty kódu.  
  
### <a name="rendering-tier-0"></a>Vrstva vykreslování 0  
 Hodnota vrstvy vykreslování 0 znamená, že pro aplikaci na zařízení není k dispozici hardwarová akcelerace grafiky. Na této úrovni vrstvy byste měli předpokládat, že všechny grafiky budou vykresleny softwarem bez hardwarové akcelerace. Funkce této vrstvy odpovídají verzi rozhraní DirectX, která je menší než 9,0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Vrstva vykreslování 1 a vrstva vykreslování 2  
  
> [!NOTE]
>  Počínaje .NET Framework 4 byla vrstva vykreslování 1 Předefinovaná tak, aby obsahovala pouze grafický hardware, který podporuje rozhraní DirectX 9,0 nebo vyšší. Grafický hardware, který podporuje rozhraní DirectX 7 nebo 8, je nyní definován jako vrstva vykreslování 0.  
  
 Hodnota vrstvy vykreslování 1 nebo 2 znamená, že většina grafických funkcí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bude používat hardwarovou akceleraci, pokud jsou k dispozici potřebné systémové prostředky a nebyly vyčerpány. To odpovídá verzi rozhraní DirectX, která je větší nebo rovna 9,0.  
  
 V následující tabulce jsou uvedeny rozdíly v požadavcích na hardware grafiky pro vrstvu vykreslování 1 a vrstvu vykreslování 2:  
  
|Funkce|Úroveň 1|Úroveň 2|  
|-------------|------------|------------|  
|Verze DirectX|Musí být větší než nebo rovno 9,0.|Musí být větší než nebo rovno 9,0.|  
|Video RAM|Musí být větší než nebo rovno 60MB.|Musí být větší než nebo rovno 120MB.|  
|Pixel shader|Úroveň verze musí být větší než nebo rovna 2,0.|Úroveň verze musí být větší než nebo rovna 2,0.|  
|Vertex shader|Žádný požadavek.|Úroveň verze musí být větší než nebo rovna 2,0.|  
|Jednotky s více texturami|Žádný požadavek.|Počet jednotek musí být větší nebo roven 4.|  
  
 Následující funkce a možnosti jsou hardwarově urychlené pro vykreslování vrstvy 1 a vrstvu vykreslování 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|2D vykreslování|Je podporováno nejvíce 2D vykreslování.|  
|3D rastrování|Je podporována většina 3D rastrování.|  
|filtrování 3D anisotropního|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pokusí se použít filtrování anisotropního při vykreslování 3D obsahu. Filtrování anisotropního odkazuje na vylepšení kvality obrazu na površích, které jsou daleko od začátku do steeply, s ohledem na kameru.|  
|mapování 3D MIP|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Při vykreslování 3D obsahu se pokusí použít mapování MIP. Mapování MIP vylepšuje kvalitu vykreslování textury, když textura zabírá menší pole zobrazení v <xref:System.Windows.Controls.Viewport3D>.|  
|Paprskové přechody|I když se podporuje, vyhněte <xref:System.Windows.Media.RadialGradientBrush> se použití na velkých objektech.|  
|výpočty prostorového osvětlení|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]provádí osvětlení po vrcholu, což znamená, že se u každého vrcholu pro každý materiál aplikovaný na síť musí vypočítat intenzita světla.|  
|Vykreslování textu|Vykreslování písma v pixelech používá k grafickému hardwaru dostupné pixel shadery.|  
  
 Následující funkce a možnosti jsou hardwarově urychlené jenom pro vykreslování úrovně 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|vyhlazení 3D|vytváření koncových aliasů pro 3D se podporuje jenom v operačních systémech, které podporují WDDM (Windows Display Driver Model) [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] , [!INCLUDE[win7](../../../../includes/win7-md.md)]jako je a.|  
  
 Následující funkce a možnosti **nejsou hardwarově** urychleny:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|Vytištěný obsah|Veškerý tištěný obsah se vykreslí pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] softwarového kanálu.|  
|Rastrový obsah, který používá<xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Veškerý obsah vykreslený pomocí <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> <xref:System.Windows.Media.Imaging.RenderTargetBitmap>metody.|  
|Obsah v dlaždicích, který používá<xref:System.Windows.Media.TileBrush>|Veškerý obsah v dlaždicích, <xref:System.Windows.Media.TileBrush.TileMode%2A> ve kterém <xref:System.Windows.Media.TileBrush> je vlastnost nastavena na <xref:System.Windows.Media.TileMode.Tile>hodnotu.|  
|Plochy, které překračují maximální velikost textury grafického hardwaru|Pro většinu grafických hardwarových zařízení jsou velikosti velkých povrchů 2048x2048 nebo 4096x4096 pixelů.|  
|Jakákoli operace, jejíž požadavek na video RAM překračuje paměť hardwaru grafiky|Pomocí nástroje pro perforaci, který je součástí [sady Performance Suite WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) v Windows SDK, můžete monitorovat využití paměti aplikace video.|  
|Vrstvená okna|Vrstvená okna umožňují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacím vykreslovat obsah na obrazovku v neobdélníkovém okně. V operačních systémech, které podporují Windows Display Driver Model (WDDM), [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] jako jsou a [!INCLUDE[win7](../../../../includes/win7-md.md)], vrstvená okna jsou hardwarově urychlená. V jiných systémech, [!INCLUDE[winxp](../../../../includes/winxp-md.md)]jako je například, jsou vrstvená okna vykreslována softwarem bez hardwarové akcelerace.<br /><br /> Můžete povolit vrstvená okna v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nástroji nastavením následujících <xref:System.Windows.Window> vlastností:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Další zdroje  
 Následující prostředky vám pomohou analyzovat charakteristiky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výkonu aplikace.  
  
### <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, jestli má být povolená hardwarová akcelerace.|  
|**Maximální hodnota pro více vzorků**|Určuje stupeň vícenásobného vzorkování pro antialiasing 3D obsah.|  
|**Požadované nastavení data ovladače videa**|Určuje, jestli systém zakáže hardwarovou akceleraci pro ovladače vydané před listopadu 2004.|  
|**Použít možnost rastrového odkazu**|Určuje, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jestli se má použít rastrový rastrový odkaz.|  
  
 K těmto nastavením může mít přístup kterýkoli externí konfigurační nástroj, který ví, jak odkazovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na nastavení registru. Tato nastavení lze také vytvořit nebo upravit přístupem k hodnotám přímo pomocí [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] editoru registru. Další informace najdete v tématu [nastavení registru pro vykreslování grafiky](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Nástroje pro profilaci výkonu WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje sadu nástrojů pro profilaci výkonu, které umožňují analyzovat chování aplikace za běhu a určují typy optimalizací výkonu, které můžete použít. V následující tabulce jsou uvedeny nástroje pro profilaci výkonu, které jsou součástí [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] nástroje, sady Performance Suite WPF:  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Perforator|Slouží k analýze chování vykreslování.|  
|Visual Profiler|Slouží k profilaci použití [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] služeb, jako je například rozložení a zpracování událostí, podle prvků ve vizuálním stromu.|  
  
 Sada Performance Suite WPF poskytuje bohatou a grafickou zobrazení dat výkonu. Další informace o nástrojích výkonu WPF naleznete v tématu [sada Performance Suite WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Nástroj pro diagnostiku rozhraní DirectX  
 Nástroj Dxdiag. exe pro diagnostiku rozhraní DirectX je navržený tak, aby pomohl řešit problémy související s rozhraním DirectX. Výchozí instalační složka nástroje pro diagnostiku rozhraní DirectX:  
  
 `~\Windows\System32`  
  
 Když spustíte nástroj pro diagnostiku rozhraní DirectX, hlavní okno obsahuje sadu karet, které vám umožní zobrazit a diagnostikovat informace týkající se rozhraní DirectX. Například karta **systém** poskytuje systémové informace o počítači a určuje verzi rozhraní DirectX, která je nainstalována v počítači.  
  
 ![Screenhot: Nástroj]pro diagnostiku rozhraní DirectX(./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Hlavní okno nástroje pro diagnostiku rozhraní DirectX  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Sada Performance Suite WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Nastavení registru pro vykreslení grafiky](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Tipy a triky animace](../graphics-multimedia/animation-tips-and-tricks.md)
