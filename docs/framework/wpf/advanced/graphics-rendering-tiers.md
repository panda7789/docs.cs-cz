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
ms.openlocfilehash: d5924ff9336bc6e93022caf1b85d5fd98f7a617d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051582"
---
# <a name="graphics-rendering-tiers"></a>Vrstvy vykreslování grafiky
Vrstvy vykreslování definuje úroveň hardwaru grafiky a výkonu pro zařízení se systémem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  

<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Grafický Hardware  
 Funkce, že mají největší dopad na úrovně vrstvy vykreslování grafiky hardware patří:  
  
- **Video RAM** množství grafické paměti na hardwarovou akceleraci Určuje velikost a počet vyrovnávacích pamětí, které lze použít pro skládání grafiky.  
  
- **Pixel Shader** pixel shader je grafických funkce, která vypočítá účinky na základě jednotlivých pixelů. V závislosti na řešení zobrazených grafiky může být několik milionů pixelů, které potřebují ke zpracování pro každý snímek pro zobrazení.  
  
- **Vertex Shader** vertex shader je grafických funkce, která provádí matematických operací s daty vrcholu objektu.  
  
- **Podpora násobnou** násobnou podporu odkazuje na možnost použít dva nebo více jedinečných textury během prolnutí operace u objektu 3D grafiky. Stupeň multitexture podpory se určuje podle počtu jednotek multitexture na hardwarovou akceleraci.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Definice úrovní vykreslování  
 Funkce hardwarovou akceleraci definují možností vykreslování objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Systém definuje tři vrstvy vykreslování:  
  
- **Vykreslování vrstvy 0** žádné hardwarovou akceleraci grafiky. Všechny funkce grafiky použít softwarové akcelerace. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je starší než verze 9.0.  
  
- **Vykreslování vrstvy 1** některé grafické funkce využívají hardwarovou akceleraci grafiky. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je větší než nebo rovna verzi 9.0.  
  
- **Vykreslování vrstva 2** většinu funkcí grafiky použít hardwarovou akceleraci grafiky. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je větší než nebo rovna verzi 9.0.  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> Vlastnost umožňuje načíst úroveň vykreslování v době spuštění aplikace. Používáte k určení, jestli zařízení podporuje některé funkce grafiky hardwarově urychlené vykreslování úroveň. Vaše aplikace potom může provést různý kód cesty v době běhu v závislosti na úrovni vykreslování zařízení podporuje.  
  
### <a name="rendering-tier-0"></a>Vykreslování vrstvy 0  
 Vrstvy vykreslování hodnota 0 znamená, že neexistuje žádná grafiky hardwarová akcelerace, které jsou k dispozici pro aplikaci na zařízení. Na této úrovni úroveň by měl předpokládat, že všechny grafiky bude vykreslen softwarem s žádné hardwarovou akceleraci. Tato úroveň funkce odpovídá [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] verzi, která je menší než 9.0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Vykreslení vrstvy 1 a vykreslování vrstvy 2  
  
> [!NOTE]
>  Spuštění v rozhraní .NET Framework 4, vykreslování vrstvy 1 podřízených zahrnout grafiky hardware, který podporuje pouze [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 9.0 či vyšší. Grafický hardware, který podporuje [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 nebo 8 je teď definovaný jako vykreslování vrstvy 0.  
  
 Hodnota vykreslování vrstvy 1 nebo 2 znamená, že většina funkcí grafiky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použije hardwarovou akceleraci v případě potřeby systémové prostředky jsou k dispozici a nebyly byl vyčerpán. To odpovídá [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] verzi, která je větší než nebo rovna hodnotě 9.0.  
  
 V následující tabulce jsou uvedeny rozdíly v grafickém požadavky na hardware pro vykreslování vrstvy 1 a vykreslování vrstvy 2:  
  
|Funkce|Úroveň 1|Úroveň 2|  
|-------------|------------|------------|  
|[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Verze|Musí být větší než nebo rovna hodnotě 9.0.|Musí být větší než nebo rovna hodnotě 9.0.|  
|Video paměti RAM|Musí být větší než nebo rovno 60MB.|Musí být větší než nebo roven 120MB.|  
|Pixel shader|Úroveň verze musí být větší než nebo rovna hodnotě 2.0.|Úroveň verze musí být větší než nebo rovna hodnotě 2.0.|  
|Vertex shaderu|Žádný požadavek.|Úroveň verze musí být větší než nebo rovna hodnotě 2.0.|  
|Multitexture jednotky|Žádný požadavek.|Počet jednotek musí být větší než nebo rovna 4.|  
  
 Následující funkce a možnosti jsou hardware accelerated pro vykreslování vrstvy 1 a vykreslování vrstvy 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|2D vykreslování|Většina 2D vykreslování je podporováno.|  
|3D rastrování|Většina 3D rasterizační je podporována.|  
|3D anizotropní filtrování|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pokusí se použít anisotropního filtrování při vykreslování 3D obsahu. Anizotropní filtrování odkazuje na zlepšení kvality obrázku textur na površích, které jsou daleko a příkře lomených s ohledem na fotoaparátu/kamery.|  
|3D mapování MIP|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pokusí se použít mapování MIP při 3D vykreslování obsahu. Mapování MIP zdokonaluje kvalitu vykreslování textury, když textury zabírá menší pole zobrazení v <xref:System.Windows.Controls.Viewport3D>.|  
|Radiálními přechody|I když se podporuje, nepoužívejte <xref:System.Windows.Media.RadialGradientBrush> na velké objekty.|  
|3D osvětlení výpočty|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádí osvětlení na vrchol, což znamená, že každý vrchol pro každý materiál použitý pro sítě je nutné vypočítat intenzita světla.|  
|Vykreslování textu|Dílčí pixel písma vykreslování používá k dispozici pixel shaderů na hardwarovou akceleraci.|  
  
 Následující funkce a možnosti jsou hardware accelerated pouze pro vykreslování vrstvy 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|3D vyhlazení|3D vyhlazení je podporována pouze v operačních systémech, které podporují Windows zobrazení ovladač WDDM (Model), jako je například [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] a [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Následující funkce a možnosti jsou **není** hardware accelerated:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|Tisk obsahu|Veškerý obsah tištěné je vykreslen pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] softwaru kanálu.|  
|Rastrový obsah, který používá <xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Žádný obsah vykreslovány <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> metoda <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.|  
|Vedle sebe obsah, který používá <xref:System.Windows.Media.TileBrush>|Žádný obsah, ve kterém vedle sebe <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.TileBrush> je nastavena na <xref:System.Windows.Media.TileMode.Tile>.|  
|Zařízení Surface, které překračují maximální velikost textury hardwarovou akceleraci|Pro většinu hardwarovou akceleraci jsou velké povrchy velikost 2048 x 2048 nebo 4096 × 4096 pixelů.|  
|Všechny operace, jejichž video RAM požadavek překračuje paměť hardwarovou akceleraci|Využití paměti RAM video aplikace můžete monitorovat pomocí nástroje Perforator nástroj, který je součástí [WPF – výkonnostní sada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) v sadě Windows SDK.|  
|Vrstvené windows|Povolit vrstvami windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací k vykreslení obsahu na obrazovku neobdélníkových oken. V operačních systémech, které podporují Windows zobrazení ovladač WDDM (Model), jako je například [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] a [!INCLUDE[win7](../../../../includes/win7-md.md)]rozvrstvenou windows jsou hardware accelerated. V ostatních systémech jako například [!INCLUDE[winxp](../../../../includes/winxp-md.md)]rozvrstvenou windows jsou vykreslovány software s žádné hardwarovou akceleraci.<br /><br /> Můžete povolit vrstvy systému windows v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tak, že nastavíte následující <xref:System.Windows.Window> vlastnosti:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Další zdroje  
 Následující prostředky vám může pomoct analyzovat charakteristiky výkonu vašich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
### <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, zda by měla být povolená hardwarová akcelerace.|  
|**Maximální hodnota Multisample**|Určuje, do jaké míry multisampling pro vyhlazení [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obsah.|  
|**Vyžaduje ovladačem grafické karty data nastavení**|Určuje, zda systém zakáže hardwarovou akceleraci ovladače vydané před listopadem 2004.|  
|**Pomocí možnosti odkaz rasterizéru**|Určuje, zda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používejte rasterizéru referenčního.|  
  
 Tato nastavení je možný přes všechny externí konfigurační nástroj, který se ví, jak odkazovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení registru. Tato nastavení také můžou vytvořit nebo upravit přístup k hodnoty přímo s použitím [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Editor registru. Další informace najdete v tématu [nastavení registru pro vykreslení grafiky](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Nástroje pro profilaci výkonu WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje sadu nástrojů, které vám umožní analyzovat chování za běhu aplikace a určete typy optimalizace výkonu, které můžete použít profilování výkonu. V následující tabulce jsou uvedeny výkonu profilování nástroje, které jsou součástí [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] nástrojů WPF – výkonnostní sada:  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Perforator|Slouží k analýze chování vykreslování.|  
|Visual Profiler|Použijte pro profilaci použití [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] služby, jako je rozložení a elementy ve vizuálním stromu zpracování událostí.|  
  
 WPF – výkonnostní sada poskytuje bohaté a grafické zobrazení dat výkonu. Další informace o výkonu WPF – nástroje najdete v tématu [WPF – výkonnostní sada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Nástroje pro diagnostiku DirectX  
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Diagnostický nástroj, Dxdiag.exe, je účelem je pomoci při řešení problémů [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]– související problémy. Výchozí instalační složku pro [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] je nástroj pro diagnostiku:  
  
 `~\Windows\System32`  
  
 Při spuštění [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] diagnostický nástroj, hlavní okno obsahuje sadu karet, které vám umožní zobrazit a diagnostikovat [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-související informace. Například **systému** karta poskytuje systémové informace o počítači a určuje verzi modulu [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] , která je nainstalovaná ve vašem počítači.  
  
 ![Screenhot: Nástroje pro diagnostiku DirectX](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Hlavní okno diagnostické nástroje DirectX  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [WPF – výkonnostní sada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Nastavení registru pro vykreslení grafiky](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Tipy a triky animace](../graphics-multimedia/animation-tips-and-tricks.md)
