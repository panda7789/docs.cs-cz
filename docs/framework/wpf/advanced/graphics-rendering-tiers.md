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
ms.openlocfilehash: c6856002288a46e78d1e1373201cf149407a814f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974019"
---
# <a name="graphics-rendering-tiers"></a>Vrstvy vykreslování grafiky
Vrstva vykreslování definuje úroveň grafických funkcí a výkonu grafického hardwaru pro zařízení, které spouští aplikaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Grafický hardware  
 Funkce grafického hardwaru, které mají největší vliv na úrovně vrstev vykreslování:  
  
- **Video RAM** Množství videopaměti v grafickém hardwaru určuje velikost a počet vyrovnávacích pamětí, které lze použít k skládání grafiky.  
  
- **Pixel shader** Pixel shader je funkce pro zpracování grafiky, která počítá efekty na základě jednotlivých pixelů. V závislosti na rozlišení zobrazené grafiky může být pro každý zobrazovací rámeček zpracováno několik milionů pixelů, které je třeba zpracovat.  
  
- **Vertex shader** Vertex shader je funkce pro zpracování grafiky, která provádí matematické operace s daty vrcholu objektu.  
  
- **Podpora více textur** Podpora více textur odkazuje na možnost použití dvou nebo více různých textur během operace prolnutí u objektu 3D grafiky. Úroveň podpory více textur je určena počtem jednotek s více texturami v grafickém hardwaru.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Definice vrstev vykreslování  
 Funkce grafického hardwaru určují schopnost vykreslování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém definuje tři úrovně vykreslování:  
  
- **Vrstva vykreslování 0** Žádná hardwarová akcelerace grafiky Všechny grafické funkce používají akceleraci softwaru. Úroveň verze DirectX je nižší než verze 9,0.  
  
- **Vrstva vykreslování 1** Některé grafické funkce využívají hardwarovou akceleraci grafiky. Úroveň verze DirectX je větší nebo rovna verzi 9,0.  
  
- **Vrstva vykreslování 2** Většina grafických funkcí používá hardwarovou akceleraci grafiky. Úroveň verze DirectX je větší nebo rovna verzi 9,0.  
  
 Vlastnost <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> umožňuje načíst úroveň vykreslování při běhu aplikace. Pomocí vrstvy vykreslování zjistíte, jestli zařízení podporuje určité grafické funkce akcelerované hardwarem. Aplikace pak může v době běhu v závislosti na vrstvě vykreslování, kterou zařízení podporuje, použít různé cesty kódu.  
  
### <a name="rendering-tier-0"></a>Vrstva vykreslování 0  
 Hodnota vrstvy vykreslování 0 znamená, že pro aplikaci na zařízení není k dispozici hardwarová akcelerace grafiky. Na této úrovni vrstvy byste měli předpokládat, že všechny grafiky budou vykresleny softwarem bez hardwarové akcelerace. Funkce této vrstvy odpovídají verzi rozhraní DirectX, která je menší než 9,0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Vrstva vykreslování 1 a vrstva vykreslování 2  
  
> [!NOTE]
> Počínaje .NET Framework 4 byla vrstva vykreslování 1 Předefinovaná tak, aby obsahovala pouze grafický hardware, který podporuje rozhraní DirectX 9,0 nebo vyšší. Grafický hardware, který podporuje rozhraní DirectX 7 nebo 8, je nyní definován jako vrstva vykreslování 0.  
  
 Hodnota vrstvy vykreslování 1 nebo 2 znamená, že většina grafických funkcí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bude používat hardwarovou akceleraci, pokud jsou k dispozici potřebné systémové prostředky a nebyly vyčerpány. To odpovídá verzi rozhraní DirectX, která je větší nebo rovna 9,0.  
  
 V následující tabulce jsou uvedeny rozdíly v požadavcích na hardware grafiky pro vrstvu vykreslování 1 a vrstvu vykreslování 2:  
  
|Funkce|Vrstva 1|Úroveň 2|  
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
|filtrování 3D anisotropního|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se při vykreslování 3D obsahu pokusí použít filtrování anisotropního. Filtrování anisotropního odkazuje na vylepšení kvality obrazu na površích, které jsou daleko od začátku do steeply, s ohledem na kameru.|  
|mapování 3D MIP|Při vykreslování 3D obsahu se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pokusí použít mapování MIP. Mapování MIP vylepšuje kvalitu vykreslování textury, když textura zabírá menší pole zobrazení ve <xref:System.Windows.Controls.Viewport3D>.|  
|Paprskové přechody|I když se podporuje, vyhněte se použití <xref:System.Windows.Media.RadialGradientBrush> u velkých objektů.|  
|výpočty prostorového osvětlení|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádí osvětlení na vrchol, což znamená, že se u každého vrcholu pro každý materiál aplikovaný na síť musí vypočítat intenzita světla.|  
|Vykreslování textu|Vykreslování písma v pixelech používá k grafickému hardwaru dostupné pixel shadery.|  
  
 Následující funkce a možnosti jsou hardwarově urychlené jenom pro vykreslování úrovně 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|vyhlazení 3D|Trojrozměrné vyhlazení se podporuje jenom v operačních systémech, které podporují WDDM (Windows Display Driver Model), jako je třeba Windows Vista a [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Následující funkce a možnosti **nejsou hardwarově** urychleny:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|Vytištěný obsah|Veškerý tištěný obsah se vykreslí pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho softwarového kanálu.|  
|Rastrový obsah, který používá <xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Veškerý obsah vykreslený pomocí metody <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.|  
|Obsah v dlaždicích, který používá <xref:System.Windows.Media.TileBrush>|Veškerý obsah v dlaždicích, ve kterém je vlastnost <xref:System.Windows.Media.TileBrush.TileMode%2A> <xref:System.Windows.Media.TileBrush> nastavena na <xref:System.Windows.Media.TileMode.Tile>.|  
|Plochy, které překračují maximální velikost textury grafického hardwaru|Pro většinu grafických hardwarových zařízení jsou velikosti velkých povrchů 2048x2048 nebo 4096x4096 pixelů.|  
|Jakákoli operace, jejíž požadavek na video RAM překračuje paměť hardwaru grafiky|Pomocí nástroje pro perforaci, který je součástí [sady Performance Suite WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) v Windows SDK, můžete monitorovat využití paměti aplikace video.|  
|Vrstvená okna|Vrstvená okna umožňují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacím vykreslovat obsah na obrazovku v neobdélníkovém okně. V operačních systémech, které podporují model WDDM (Windows Display Driver Model), jako je například Windows Vista a [!INCLUDE[win7](../../../../includes/win7-md.md)], jsou vrstvená okna hardwarově urychlená. V jiných systémech, například [!INCLUDE[winxp](../../../../includes/winxp-md.md)], se vrstvená okna vykreslují softwarem bez hardwarové akcelerace.<br /><br /> Můžete povolit vrstvená okna v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavením následujících vlastností <xref:System.Windows.Window>:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Další zdroje  
 Následující prostředky vám pomohou analyzovat výkonnostní charakteristiky vaší aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování:  
  
|Nastavením|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, jestli má být povolená hardwarová akcelerace.|  
|**Maximální hodnota pro více vzorků**|Určuje stupeň vícenásobného vzorkování pro antialiasing 3D obsah.|  
|**Požadované nastavení data ovladače videa**|Určuje, jestli systém zakáže hardwarovou akceleraci pro ovladače vydané před listopadu 2004.|  
|**Použít možnost rastrového odkazu**|Určuje, jestli má [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používat rastrový odkaz.|  
  
 K těmto nastavením může mít přístup kterýkoli externí konfigurační nástroj, který ví, jak odkazovat na nastavení registru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tato nastavení se dají vytvářet nebo upravovat taky tak, že se přistupují k hodnotám přímo pomocí Editoru registru Windows. Další informace najdete v tématu [nastavení registru pro vykreslování grafiky](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Nástroje pro profilaci výkonu WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje sadu nástrojů pro profilaci výkonu, které umožňují analyzovat chování aplikace za běhu a určují typy optimalizací výkonu, které můžete použít. V následující tabulce jsou uvedeny nástroje pro profilaci výkonu, které jsou součástí nástroje Windows SDK, sady Performance Suite WPF:  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Perforator|Slouží k analýze chování vykreslování.|  
|Visual Profiler|Slouží k profilaci použití [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Services, jako je například rozložení a zpracování událostí, podle prvků ve vizuálním stromu.|  
  
 Sada Performance Suite WPF poskytuje bohatou a grafickou zobrazení dat výkonu. Další informace o nástrojích výkonu WPF naleznete v tématu [sada Performance Suite WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Nástroj pro diagnostiku rozhraní DirectX  
 Nástroj Dxdiag. exe pro diagnostiku rozhraní DirectX je navržený tak, aby pomohl řešit problémy související s rozhraním DirectX. Výchozí instalační složka nástroje pro diagnostiku rozhraní DirectX:  
  
 `~\Windows\System32`  
  
 Když spustíte nástroj pro diagnostiku rozhraní DirectX, hlavní okno obsahuje sadu karet, které vám umožní zobrazit a diagnostikovat informace týkající se rozhraní DirectX. Například karta **systém** poskytuje systémové informace o počítači a určuje verzi rozhraní DirectX, která je nainstalována v počítači.  
  
 ![Screenhot: Nástroj pro diagnostiku rozhraní DirectX](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Hlavní okno nástroje pro diagnostiku rozhraní DirectX  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Sada Performance Suite WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Nastavení registru pro vykreslení grafiky](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Tipy a triky animace](../graphics-multimedia/animation-tips-and-tricks.md)
