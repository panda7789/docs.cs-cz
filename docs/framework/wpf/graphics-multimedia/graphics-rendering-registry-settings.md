---
title: Nastavení registru pro vykreslení grafiky
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: 642dfdd784af4b85672cf5b0c8e60079763f4c47
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112281"
---
# <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky
Toto téma obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přehled nastavení registru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování grafiky, které ovlivňují aplikace.  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kdy použít nastavení registru vykreslování grafiky  
 Tato nastavení registru jsou k dispozici pro účely řešení potíží, ladění a podpory produktu. Vzhledem k tomu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] že změny v registru ovlivňují všechny aplikace, aplikace by nikdy změnit tyto klíče registru automaticky nebo během instalace.  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>Co jsou XPDM a WDDM?  
 Některá nastavení registru vykreslování grafiky mají různé výchozí hodnoty v závislosti na tom, zda grafická karta používá ovladač XPDM nebo WDDM. XPDM je Microsoft Windows XP Display Driver Model a WDDM je Windows Display Driver Model. WdDM je k dispozici v počítačích se systémem Windows Vista a Windows 7. XpDM je k dispozici v počítačích se systémem Windows Vista, Microsoft Windows XP a Microsoft Windows Server 2003. Další informace o wddm naleznete v [tématu Windows Display Driver Model (WDDM) Design Guide](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide).  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Poskytuje čtyři nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] registru pro řízení vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, zda má být povolena hardwarová akcelerace.|  
|**Maximální hodnota vícenásobného vzorku**|Určuje stupeň vícenásobného vzorkování pro vyhlazení 3D obsahu.|  
|**Požadované datum ovladače videa**|Určuje, zda systém zakáže hardwarovou akceleraci ovladačů vydaných před listopadem 2004.|  
|**Použít možnost referenčního rastrování**|Určuje, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zda má být používán referenční rastrovač.|  
  
 K těmto nastavením lze přistupovat libovolným externím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konfiguračním nástrojem, který ví, jak odkazovat na nastavení registru. Tato nastavení lze také vytvořit nebo upravit přístupem k hodnotám přímo pomocí Editoru registru systému Windows.  
  
<a name="disablehardwareacceleration"></a>
## <a name="disable-hardware-acceleration-option"></a>Zakázat možnost hardwarové akcelerace  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 Možnost **zakázat hardwarovou akceleraci** umožňuje vypnout hardwarovou akceleraci pro účely ladění a testování. Když se v aplikaci zobrazí artefakty vykreslování, zkuste vypnout hardwarovou akceleraci. Pokud artefakt zmizí, problém může být s ovladačem grafické karty.  
  
 **Možnost zakázat hardwarovou akceleraci** je hodnota DWORD, která je buď 0 nebo 1. Hodnota 1 zakáže hardwarovou akceleraci. Hodnota 0 umožňuje hardwarovou akceleraci za předpokladu, že systém splňuje požadavky na hardwarovou akceleraci. Další informace naleznete [v tématu Úrovně vykreslování grafiky](../advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>
## <a name="maximum-multisample-value"></a>Maximální hodnota vícenásobného vzorku  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maximální hodnota vícenásobného vzorku** umožňuje upravit maximální množství vyhlazení 3D obsahu. Tato úroveň slouží k zakázání 3D vyhlazení v systému Windows Vista.  
  
 **Maximální hodnota vícenásobného vzorku** je hodnota DWORD, která se pohybuje od 0 do 16. Hodnota 0 určuje, že vícenásobné vyhlazení 3D obsahu by mělo být zakázáno a hodnota 16 se pokusí použít až 16x vícenásobné vyhlazení, pokud je grafická karta podporována. Mějte na paměti, že nastavení této hodnoty klíče registru v počítačích používajících ovladače XPDM způsobí, že aplikace budou používat velké množství další grafické paměti, sníží výkon 3D vykreslování a může zavést chyby a stabilitu vykreslování. Problémy.  
  
 Není-li tento klíč [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] registru nastaven, je výchozí hodnota 0 pro ovladače XPDM a 4 pro ovladače WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>Požadované datum ovladače videa  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Řetězec|  
  
 V listopadu 2004 vydala společnost Microsoft novou verzi pokynů pro testování ovladačů. řidiči napsané po tomto datu nabízejí lepší stabilitu. Ve výchozím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení bude pro tyto ovladače používat kanál hardwarové akcelerace a vrátí se k vykreslování softwaru pro ovladače XPDM publikované před tímto datem.  
  
 **Požadované nastavení data ovladače videa** umožňuje zadat alternativní minimální datum pro ovladače XPDM. Datum starší než listopad 2004 byste měli zadat pouze v případě, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jste si jisti, že ovladač grafické karty je dostatečně stabilní pro podporu .  
  
 Požadované nastavení ovladače grafické karty má řetězec následujícího formátu:  
  
| |  
|-|  
|*Yyyy* `/` *MM* `/` *DD*|  
  
 Kde *YYYY* je čtyřmístný rok, *MM* je dvoumístný měsíc a *DD* je dvoumístný den. Pokud je tato hodnota [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpojena, použije listopad 2004 jako požadované datum ovladače grafické karty.  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>Použít možnost referenčního rastrování  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Možnost rezerce odkazu použít** umožňuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vynutit do režimu simulovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hardwarového vykreslování pro ladění: přejde do hardwarového režimu, ale používá rastrovač referenčního softwaru Microsoft Direct3D, d3dref9.dll, namísto skutečného hardwarového zařízení.  
  
 Referenční rastrovač je velmi pomalý, ale obchází ovladač videa, aby se zabránilo problémům s vykreslováním způsobeným problémy s ovladači. Z tohoto důvodu můžete použít rastrový rezerátor k určení, pokud jsou problémy s vykreslováním způsobeny ovladačem videa. Soubor d3dref9.dll musí být v umístění, kde k němu má aplikace přístup, například v libovolném umístění v systémové cestě nebo v místním adresáři aplikace.  
  
 **Možnost rezertora odkazu použít** přebírá hodnotu DWORD. Hodnota 0 označuje, že referenční rastrovač není použit. Všechny ostatní nenulové [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodnoty vynutí použít referenční rastrovač.  
  
## <a name="see-also"></a>Viz také

- [Vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
