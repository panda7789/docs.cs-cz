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
ms.openlocfilehash: f2af32315f8f955495c51f2928c2b8eed5350759
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016086"
---
# <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky
Toto téma poskytuje přehled nastavení registru pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování grafiky, která mají vliv [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na aplikace.  

<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kdy použít nastavení registru pro vykreslování grafiky  
 Tato nastavení registru jsou k dispozici pro účely řešení potíží, ladění a podpory produktů. Vzhledem k tomu, že změny registru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovlivňují všechny aplikace, aplikace by nikdy neměly měnit tyto klíče registru automaticky nebo během instalace.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>Co jsou XPDM a WDDM?  
 Některá nastavení registru pro vykreslování grafiky mají různé výchozí hodnoty v závislosti na tom, jestli vaše grafická karta používá ovladač XPDM nebo WDDM. XPDM je [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] model ovladače zobrazení a WDDM je model ovladače zobrazení systému Windows. WDDM je k dispozici na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] počítačích [!INCLUDE[win7](../../../../includes/win7-md.md)]se systémem a. XPDM je k dispozici na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]počítačích [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]se systémy [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)], a. Další informace o WDDM najdete v tématu [Průvodce návrhem zobrazovacího modelu Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, jestli má být povolená hardwarová akcelerace.|  
|**Maximální hodnota pro více vzorků**|Určuje stupeň vícenásobného vzorkování pro antialiasing 3D obsah.|  
|**Požadované nastavení data ovladače videa**|Určuje, jestli systém zakáže hardwarovou akceleraci pro ovladače vydané před listopadu 2004.|  
|**Použít možnost rastrového odkazu**|Určuje, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jestli se má použít rastrový rastrový odkaz.|  
  
 K těmto nastavením může mít přístup kterýkoli externí konfigurační nástroj, který ví, jak odkazovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na nastavení registru. Tato nastavení se dají vytvářet nebo upravovat taky tak, že se přistupují k hodnotám přímo pomocí Editoru registru Windows.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Zakázat možnost hardwarové akcelerace  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Možnost zakázat hardwarovou akceleraci** umožňuje vypnout hardwarovou akceleraci pro účely ladění a testování. Když se v aplikaci zobrazí artefakty vykreslování, zkuste vypnout hardwarovou akceleraci. Pokud artefakt zmizí, může se jednat o problém s vaším ovladačem videa.  
  
 **Možnost zakázat hardwarovou akceleraci** je hodnota DWORD, která je buď 0, nebo 1. Hodnota 1 zakáže hardwarovou akceleraci. Hodnota 0 povolí hardwarovou akceleraci za předpokladu, že systém splňuje požadavky na hardwarovou akceleraci. Další informace najdete v tématu [vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>Maximální hodnota pro více vzorků  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maximální hodnota pro více vzorků** umožňuje upravit maximální množství antialiasing 3D obsahu. Pomocí této úrovně můžete v [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] nástroji zakázat 3D antialiasing nebo [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]je povolit.  
  
 **Maximální hodnota více vzorků** je hodnota DWORD, která je v rozsahu od 0 do 16. Hodnota 0 určuje, že by měl být zakázán antialiasing obsah s více vzorky a hodnota 16 se pokusí o použití až 16x antialiasing s více ukázkami, pokud je tato grafická karta podporovaná. Mějte na paměti, že nastavení této hodnoty klíče registru na počítačích, které používají ovladače XPDM, způsobí, že aplikace budou používat velké množství dalších video paměti, sníží se výkon trojrozměrného vykreslování a bude mít potenciál k zavedení chyb a stability vykreslování. problém.  
  
 Pokud není tento klíč registru nastavený, výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodnota je 0 pro ovladače XPDM a 4 pro ovladače WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Požadované nastavení data ovladače videa  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 V listopadu 2004 společnost Microsoft vydala novou verzi pokynů pro testování ovladačů; ovladače napsané po tomto datu nabízejí lepší stabilitu. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použije kanál hardwarové akcelerace pro tyto ovladače a přejde zpět na softwarové vykreslování pro ovladače XPDM publikované před tímto datem.  
  
 **Požadované nastavení data ovladače videa** vám umožní zadat alternativní datum minima pro XPDM ovladače. Měli byste zadat jenom datum starší než listopadu 2004, pokud máte jistotu, že váš ovladač videa je dostatečně stabilní, aby podporoval [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Požadované nastavení ovladače videokarty má řetězec v následujícím formátu:  
  
| |  
|-|  
|*RRRR* `/` DD MM `/`|  
  
 Kde *RRRR* je čtyřmístné číslo roku, *mm* je dvoumístný měsíc a *DD* je dva číslice dne. Pokud je tato hodnota nastavená [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na hodnotu zrušit, použije se jako požadované datum ovladače videa 2004. listopadu.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Použít možnost rastrového odkazu  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Možnost použít rastrový odkaz** umožňuje vynutit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] režim vykreslování simulovaného hardwaru pro ladění: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přejde do režimu hardwaru, ale používá nástroj Microsoft Direct3D reference software Rastrováním, d3dref9. dll. místo skutečného hardwarového zařízení.  
  
 Rastrový rastr je velmi pomalý, ale obchází ovladač videa, aby nedocházelo k problémům s vykreslováním způsobeným problémy s ovladačem. Z tohoto důvodu můžete použít rastrový odkaz k určení, zda je příčinou problémy vykreslování ovladačem videokarty. Soubor d3dref9. dll musí být v umístění, kde aplikace k němu má přístup, například v libovolném umístění v systémové cestě nebo v místním adresáři aplikace.  
  
 **Možnost použít rastrový odkaz** má hodnotu DWORD. Hodnota 0 značí, že se nepoužívá rastrový rastr. Jakákoli jiná nenulová hodnota vynutí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použití rastrového rastrového odkazu.  
  
## <a name="see-also"></a>Viz také:

- [Vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
