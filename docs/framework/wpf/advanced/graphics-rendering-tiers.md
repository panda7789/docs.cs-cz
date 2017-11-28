---
title: "Vrstvy vykreslování grafiky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], performance
- rendering graphics [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
caps.latest.revision: "44"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a64ca2f0da2e10a3042b5f9c30baf3caa37534e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="graphics-rendering-tiers"></a>Vrstvy vykreslování grafiky
Vrstvu vykreslování definuje úroveň grafiky schopnost hardwaru a výkon pro zařízení, které běží [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  

  
<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Grafika hardwaru  
 Funkce hardwaru grafiky, aby většina vliv úrovně vrstvy vykreslování, jsou:  
  
-   **Video RAM** množství grafické paměti v grafickém hardwaru Určuje velikost a počet vyrovnávacích pamětí, které lze použít pro grafiky skládání.  
  
-   **Pixelů shaderu** je shaderu pixelů grafiky, zpracování funkce, která vypočítá účinky na základě za pixelů. V závislosti na řešení zobrazené grafiky může být několik mil. pixelů, které je třeba zpracovat pro každý snímek zobrazení.  
  
-   **Vrchol shaderu** vrchol shaderu je grafiky, funkce, která provádí matematické operace vrchol data objektu zpracování.  
  
-   **Podpora násobnou** násobnou podporu odkazuje na možnost použít dvě nebo více jedinečných textury během prolnutí operace u objektu 3D grafický. Stupeň multitexture podpory je určen podle počet multitexture jednotek na grafickém hardwaru.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Definice úrovní vykreslování  
 Funkce hardwaru grafiky určit možnosti vykreslování produktu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Systému definuje vykreslování vrstev:  
  
-   **Vykreslování vrstvy 0** žádné grafiky hardwarovou akceleraci. Všechny funkce grafiky pomocí akcelerace softwaru. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je nižší než verze 9.0.  
  
-   **Vykreslování vrstvy 1** některé funkce grafiky použít hardwarovou akceleraci grafiky. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je větší než nebo rovno verze 9.0.  
  
-   **Vykreslování vrstva 2** většinu funkcí grafiky použít hardwarovou akceleraci grafiky. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Úrovni verze je větší než nebo rovno verze 9.0.  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> Vlastnost umožňuje načíst vrstvě vykreslování v době běhu aplikace. Chcete-li zjistit, jestli je zařízení podporuje určité funkce hardwaru accelerated grafiky používáte úroveň vykreslování. Aplikace pak může trvat cesty jiný kódu v době běhu v závislosti na úrovni vykreslování podporován zařízením s technologií.  
  
### <a name="rendering-tier-0"></a>Vykreslování vrstvy 0  
 Vykreslování vrstvy hodnota 0 znamená, že neexistuje žádná grafiky hardwarové akcelerace, které jsou k dispozici pro aplikaci na zařízení. Na této úrovni vrstvy by měl předpokládají, že všechny grafiky bude vykreslen softwarem s žádné hardwarovou akceleraci. Tato úroveň funkce odpovídá [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] verzi, která je menší než 9.0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Vykreslování vrstvy 1 a vykreslování vrstvy 2  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework 4, vykreslování vrstvy 1 podřízených zahrnout pouze grafiky hardwaru, který podporuje [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 9.0 nebo vyšší. Grafika hardwaru, který podporuje [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 nebo 8 je nyní definována jako vykreslování vrstvy 0.  
  
 Hodnota vykreslování vrstvy 1 nebo 2 znamená, která nejvíc funkce grafiky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hardwarovou akceleraci bude používat, pokud nezbytné systémové prostředky jsou k dispozici a nebyly vyčerpání. To odpovídá [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] verzi, která je větší než nebo rovna hodnotě 9.0.  
  
 V následující tabulce jsou uvedeny rozdíly v grafiky požadavky na hardware pro vykreslování vrstvy 1 a vykreslování vrstvy 2:  
  
|Funkce|Vrstvy 1|Vrstva 2|  
|-------------|------------|------------|  
|[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]verze|Musí být větší než nebo rovna hodnotě 9.0.|Musí být větší než nebo rovna hodnotě 9.0.|  
|Video RAM|Musí být větší než nebo rovna hodnotě 60MB.|Musí být větší než nebo roven 120MB.|  
|Shaderu pixelů|Úroveň verze musí být větší než nebo rovna hodnotě 2.0.|Úroveň verze musí být větší než nebo rovna hodnotě 2.0.|  
|Vrchol shaderu|Nevyžaduje.|Úroveň verze musí být větší než nebo rovna hodnotě 2.0.|  
|Multitexture jednotky|Nevyžaduje.|Počet jednotek musí být větší než nebo rovna hodnotě 4.|  
  
 Následující funkce a možnosti jsou hardwaru accelerated pro vykreslování vrstvy 1 a vykreslování vrstvy 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|2D vykreslování|Většina 2D vykreslování je podporována.|  
|3D rasterizační|Většina 3D rasterizační je podporována.|  
|3D volba filtrování|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pokusí se použít volba filtrování při vykreslování 3D obsahu. Volba filtrování odkazuje na zlepšení kvality obrázku textury na plochy, které jsou daleko a příkře šikmo s ohledem na fotoaparát.|  
|3D MIP mapování|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pokusí se použít mapování MIP při vykreslování 3D obsahu. Mapování MIP zvyšuje kvalitu vykreslování texture, když texturou zabírá menší zobrazení of pole v <xref:System.Windows.Controls.Viewport3D>.|  
|Kruhové přechody|Když podporované, nepoužívejte <xref:System.Windows.Media.RadialGradientBrush> pro velké objekty.|  
|3D osvětlení výpočty|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]provede na vrchol osvětlení, což znamená, že intenzita světla se počítá na každý vrcholu pro každý materiál použít mřížku.|  
|Vykreslování textu|Dílčí pixelů písma vykreslování používá shadery dostupné pixelů na grafickém hardwaru.|  
  
 Následující funkce a možnosti jsou hardwaru accelerated pouze pro vykreslování vrstvy 2:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|3D vyhlazení|3D vyhlazení je podporována pouze v operačních systémech, které podporují zobrazení ovladačů modelu WDDM (Windows), jako například [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] a [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Následující funkce a možnosti jsou **není** accelerated hardwaru:  
  
|Funkce|Poznámky|  
|-------------|-----------|  
|Obsah na tištěných|Veškerý obsah na tištěných je vykreslen pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] softwaru kanálu.|  
|Rastrového obsah, který používá<xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Žádný obsah vykreslen pomocí <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> metodu <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.|  
|Vedle sebe obsah, který používá<xref:System.Windows.Media.TileBrush>|Žádné rozložen formou dlaždic obsah, ve kterém <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.TileBrush> je nastaven na <xref:System.Windows.Media.TileMode.Tile>.|  
|Plochy, které překračují maximální velikost textury hardwaru grafiky|Pro většinu grafiky hardware jsou velké povrchy velikost 2048 x 2048 nebo 4096 x 4096 pixelů.|  
|Všechny operace, jejichž video RAM požadavek překračuje velikost paměti hardwaru grafiky|Video RAM využití aplikace můžete monitorovat pomocí nástroje Perforator nástroj, který je součástí [WPF – výkonnostní sada](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e) ve Windows SDK.|  
|Vrstvený windows|Povolit vrstveného windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace k vykreslení obsahu na obrazovku na okno obdélníkový. V operačních systémech, které podporují zobrazení ovladačů modelu WDDM (Windows), jako například [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] a [!INCLUDE[win7](../../../../includes/win7-md.md)], vrstvený windows jsou accelerated hardwaru. Na jiných systémů jako například [!INCLUDE[winxp](../../../../includes/winxp-md.md)], vrstvený windows jsou vykreslovány softwarem s žádné hardwarovou akceleraci.<br /><br /> Můžete povolit vrstveného windows v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavením následující <xref:System.Windows.Window> vlastnosti:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Další zdroje  
 Následující prostředky vám může pomoct analyzovat charakteristiky výkonu už vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
### <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, zda se má povolit hardwarovou akceleraci.|  
|**Maximální hodnota Multisample**|Určuje úroveň multisampling pro vyhlazení [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obsah.|  
|**Požadované ovladače grafické karty datum nastavení**|Určuje, zda systém zakáže hardwarovou akceleraci vydané dřív než listopadu 2004 ovladače.|  
|**Reference – možnost umožňuje použít**|Určuje, zda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] by měl používat umožňuje odkaz.|  
  
 Tato nastavení mají přístup všechny externí konfigurace nástroj, který umí tak, aby odkazovaly [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení registru. Tato nastavení taky můžou vytvořit nebo upravit přístup k hodnoty přímo pomocí [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Editor registru. Další informace najdete v tématu [nastavení registru vykreslování grafiky](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Profilace výkonu WPF – nástroje  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje sadu nástrojů, které vám umožní analyzovat běhového chování vaší aplikace a zjistit typy optimalizací výkonu, která můžete použít na profilování výkonu. Následující tabulka uvádí výkon profilace nástroje, které jsou součástí [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] nástroj WPF – výkonnostní sada:  
  
|Nástroj|Popis|  
|----------|-----------------|  
|Perforator|Použití pro analýzu chování vykreslování.|  
|Visual Profiler|Použít pro profilace použití [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] služby, jako je rozložení a elementy ve vizuální strojové struktuře zpracování událostí.|  
  
 WPF – výkonnostní sada poskytuje bohatou a grafické zobrazení dat výkonu. Další informace o WPF nástroje pro sledování výkonu najdete v tématu [WPF – výkonnostní sada](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e).  
  
### <a name="directx-diagnostic-tool"></a>Nástroje pro diagnostiku DirectX  
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Diagnostický nástroj, Dxdiag.exe, slouží k vyřešení [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-problémům. Výchozí instalační složku pro [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] je nástroj pro diagnostiku:  
  
 `~\Windows\System32`  
  
 Při spuštění [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] diagnostický nástroj, hlavní okno obsahuje sadu karet, které vám umožní zobrazit a provést diagnostiku [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-související informace. Například **systému** poskytuje systémové informace o počítači a určuje verzi [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] který máte nainstalován ve vašem počítači.  
  
 ![Screenhot: Nástroj pro diagnostiku rozhraní DirectX](../../../../docs/framework/wpf/advanced/media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Hlavní okno nástroje pro diagnostiku DirectX  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.RenderCapability>  
 <xref:System.Windows.Media.RenderOptions>  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [WPF – výkonnostní sada](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)  
 [Nastavení registru vykreslování grafiky](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md)  
 [Animace tipy a triky](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
