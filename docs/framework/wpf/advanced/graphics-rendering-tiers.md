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
ms.openlocfilehash: 3c21ae3d00aa9f1b48a89650430b89ceccb2a1b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186017"
---
# <a name="graphics-rendering-tiers"></a>Vrstvy vykreslování grafiky
Úroveň vykreslování definuje úroveň grafických hardwarových [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schopností a výkonu pro zařízení, které spouští aplikaci.  

<a name="graphics_hardware"></a>
## <a name="graphics-hardware"></a>Grafický hardware  
 Funkce grafického hardwaru, které nejvíce ovlivňují úrovně úrovně vykreslování, jsou:  
  
- **Video RAM** Velikost grafické paměti na grafickém hardwaru určuje velikost a počet vyrovnávacích pamětí, které lze použít pro skládání grafiky.  
  
- **Shader pixelů** Shader obrazových bodů je funkce zpracování grafiky, která vypočítá efekty na základě pixelů. V závislosti na rozlišení zobrazené grafiky může být několik milionů pixelů, které je třeba zpracovat pro každý snímek zobrazení.  
  
- **Shader vrcholů** Shader vrcholů je funkce zpracování grafiky, která provádí matematické operace s daty vrcholu objektu.  
  
- **Podpora multitextury** Podpora multitextur odkazuje na schopnost aplikovat dvě nebo více odlišných textur během operace prolnutí na objekt 3D grafiky. Stupeň podpory více textur je určen počtem vícetexturových jednotek na grafickém hardwaru.  
  
<a name="rendering_tier_definitions"></a>
## <a name="rendering-tier-definitions"></a>Vykreslování definic vrstev  
 Funkce grafického hardwaru určují možnostvykreslování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Systém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definuje tři úrovně vykreslování:  
  
- **Úroveň vykreslování 0** Žádná hardwarová akcelerace grafiky. Všechny grafické funkce používají softwarovou akceleraci. Úroveň verze DirectX je menší než verze 9.0.  
  
- **Úroveň vykreslování 1** Některé grafické funkce používají hardwarovou akceleraci grafiky. Úroveň verze DirectX je větší nebo rovna verzi 9.0.  
  
- **Úroveň vykreslování 2** Většina grafických funkcí používá hardwarovou akceleraci grafiky. Úroveň verze DirectX je větší nebo rovna verzi 9.0.  
  
 Vlastnost <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> umožňuje načíst úroveň vykreslování v době spuštění aplikace. Vrstva vykreslování slouží k určení, zda zařízení podporuje určité hardwarově akcelerované grafické funkce. Vaše aplikace pak může trvat různé cesty kódu za běhu v závislosti na úrovni vykreslování podporované zařízením.  
  
### <a name="rendering-tier-0"></a>Úroveň vykreslování 0  
 Hodnota úrovně vykreslování 0 znamená, že pro aplikaci v zařízení není k dispozici žádná hardwarová akcelerace grafiky. Na této úrovni úrovně byste měli předpokládat, že všechny grafiky budou vykresleny softwarem bez hardwarové akcelerace. Funkce této úrovně odpovídá verzi DirectX, která je menší než 9.0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Vykreslovací úroveň 1 a úroveň vykreslování 2  
  
> [!NOTE]
> Počínaje rozhraním .NET Framework 4 byla úroveň vykreslování 1 předefinována tak, aby zahrnovala pouze grafický hardware, který podporuje rozhraní DirectX 9.0 nebo vyšší. Grafický hardware, který podporuje Rozhraní DirectX 7 nebo 8, je nyní definován jako úroveň vykreslování 0.  
  
 Hodnota úrovně vykreslování 1 nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 2 znamená, že většina grafických funkcí bude používat hardwarovou akceleraci, pokud jsou k dispozici potřebné systémové prostředky a nebyly vyčerpány. To odpovídá verzi DirectX, která je větší nebo rovna 9.0.  
  
 Následující tabulka ukazuje rozdíly v požadavcích grafického hardwaru pro vykreslování tier 1 a vykreslovací vrstvy 2:  
  
|Funkce|Vrstva 1|Vrstva 2|  
|-------------|------------|------------|  
|Verze DirectX|Musí být větší nebo rovna 9.0.|Musí být větší nebo rovna 9.0.|  
|Video RAM|Musí být větší nebo rovna 60 MB.|Musí být větší nebo rovna 120MB.|  
|Shader obrazových bodů|Úroveň verze musí být větší nebo rovna 2.0.|Úroveň verze musí být větší nebo rovna 2.0.|  
|Shader vrcholů|Žádný požadavek.|Úroveň verze musí být větší nebo rovna 2.0.|  
|Jednotky s více texturami|Žádný požadavek.|Počet jednotek musí být větší nebo roven 4.|  
  
 Následující funkce a možnosti jsou hardwarově akcelerované pro vykreslování tier 1 a vykreslovací úroveň 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|2D vykreslování|Většina 2D vykreslování je podporována.|  
|3D rastrování|Většina 3D rastrování je podporována.|  
|3D anizotropní filtrování|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pokusí se použít anizotropní filtrování při vykreslování 3D obsahu. Anizotropní filtrování se týká zvýšení kvality obrazu textur na povrchu, které jsou daleko a strmě šikmé s ohledem na kameru.|  
|Mapování 3D MIP|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pokusí se použít mapování MIP při vykreslování 3D obsahu. Mapování MIP zlepšuje kvalitu vykreslování textury, <xref:System.Windows.Controls.Viewport3D>když textura zabírá menší zorné pole v .|  
|Kruhové přechody|Při podpoře se vyhněte použití <xref:System.Windows.Media.RadialGradientBrush> na velkých objektech.|  
|Výpočty 3D osvětlení|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]provádí osvětlení na vrchol, což znamená, že intenzita světla musí být vypočtena v každém vrcholu pro každý materiál aplikovaný na síť.|  
|Vykreslování textu|Vykreslování písem subpixelpoužívá na grafickém hardwaru dostupné shaderů pixelů.|  
  
 Následující funkce a možnosti jsou hardwarově akcelerovány pouze pro vykreslování úrovně 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|3D vyhlazení|3D vyhlazení je podporováno pouze v operačních systémech, které podporují model ovladače zobrazení systému Windows (WDDM), například Windows Vista a Windows 7.|  
  
 Následující funkce a možnosti **nejsou** hardwarově akcelerovány:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|Tištěný obsah|Veškerý tištěný obsah je vykreslen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pomocí softwarového kanálu.|  
|Rastrovaný obsah, který používá<xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Jakýkoli obsah vykreslený <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> pomocí <xref:System.Windows.Media.Imaging.RenderTargetBitmap>metody .|  
|Kachlový obsah, který používá<xref:System.Windows.Media.TileBrush>|Jakýkoli obsah vedle stlačení, ve <xref:System.Windows.Media.TileBrush.TileMode%2A> kterém je vlastnost nastavena <xref:System.Windows.Media.TileBrush> na <xref:System.Windows.Media.TileMode.Tile>.|  
|Povrchy, které přesahují maximální velikost textury grafického hardwaru|U většiny grafických hardwaru mají velké plochy velikost 2048 × 2048 nebo 4096 × 4096 pixelů.|  
|Jakákoli operace, jejíž požadavek na paměť videa přesahuje paměť grafického hardwaru|Využití paměti RAM videa aplikace můžete sledovat pomocí nástroje Perforator, který je součástí [sady WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) v sadě Windows SDK.|  
|Vrstvená okna|Okna s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vrstvami umožňují aplikacím vykreslovat obsah na obrazovku v neobdélníkovém okně. V operačních systémech, které podporují model ovladače zobrazení systému Windows (WDDM), například Windows Vista a Windows 7, jsou vrstvená okna hardwarově akcelerovaná. V jiných systémech, například v systému Windows XP, jsou vrstvená okna vykreslena softwarem bez hardwarové akcelerace.<br /><br /> Okna s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vrstvami můžete povolit nastavením následujících <xref:System.Windows.Window> vlastností:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>
## <a name="other-resources"></a>Další prostředky  
 Následující prostředky vám mohou pomoci analyzovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] charakteristiky výkonu aplikace.  
  
### <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Poskytuje čtyři nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] registru pro řízení vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, zda má být povolena hardwarová akcelerace.|  
|**Maximální hodnota vícenásobného vzorku**|Určuje stupeň vícenásobného vzorkování pro vymýšce 3D obsahu.|  
|**Požadované datum ovladače videa**|Určuje, zda systém zakáže hardwarovou akceleraci ovladačů vydaných před listopadem 2004.|  
|**Použít možnost referenčního rastrování**|Určuje, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zda má být používán referenční rastrovač.|  
  
 K těmto nastavením lze přistupovat libovolným externím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konfiguračním nástrojem, který ví, jak odkazovat na nastavení registru. Tato nastavení lze také vytvořit nebo upravit přístupem k hodnotám přímo pomocí Editoru registru systému Windows. Další informace naleznete [v tématu Graphics Rendering Registry Settings](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Nástroje pro profilování výkonu WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Poskytuje sadu nástrojů pro profilování výkonu, které umožňují analyzovat chování aplikace za běhu a určit typy optimalizace výkonu, které můžete použít. V následující tabulce jsou uvedeny nástroje pro profilování výkonu, které jsou součástí sady WPF Performance Suite sady Windows SDK:  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Perforator|Slouží k analýze chování vykreslování.|  
|Visual Profiler|Slouží k profilování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použití služeb, jako je například rozložení a zpracování událostí, prvky ve vizuálním stromu.|  
  
 WPF Performance Suite poskytuje bohaté, grafické zobrazení dat o výkonu. Další informace o nástrojích výkonu WPF naleznete v tématu [WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Nástroj pro diagnostiku rozhraní DirectX  
 Nástroj Dxdiag.exe, nástroj DirectX Diagnostic Tool, je navržen tak, aby vám pomohl řešit problémy související s rozhraním DirectX. Výchozí instalační složka diagnostického nástroje DirectX je:  
  
 `~\Windows\System32`  
  
 Při spuštění nástroje DirectX Diagnostic Tool obsahuje hlavní okno sadu karet, které umožňují zobrazit a diagnostikovat informace související s rozhraním DirectX. Karta **Systém** například poskytuje systémové informace o počítači a určuje verzi rozhraní DirectX nainstalovanou v počítači.  
  
 ![Screenhot: Diagnostický nástroj DirectX](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Hlavní okno diagnostického nástroje DirectX  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Výkonová sada WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Nastavení registru pro vykreslení grafiky](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Tipy a triky animace](../graphics-multimedia/animation-tips-and-tricks.md)
