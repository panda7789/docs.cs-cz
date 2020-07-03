---
title: Nastavení registru pro vykreslení grafiky
description: Přečtěte si, jak používat nastavení registru pro účely řešení potíží, ladění a podpory produktů v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: a2c6cfa5a207ae89c053f6ee81597f01458b5933
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853765"
---
# <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky
Toto téma poskytuje přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení registru pro vykreslování grafiky, která mají vliv na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kdy použít nastavení registru pro vykreslování grafiky  
 Tato nastavení registru jsou k dispozici pro účely řešení potíží, ladění a podpory produktů. Vzhledem k tomu, že změny registru ovlivňují všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, aplikace by nikdy neměly měnit tyto klíče registru automaticky nebo během instalace.  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>Co jsou XPDM a WDDM?  
 Některá nastavení registru pro vykreslování grafiky mají různé výchozí hodnoty v závislosti na tom, jestli vaše grafická karta používá ovladač XPDM nebo WDDM. XPDM je model ovladače zobrazení Microsoft Windows XP a WDDM je model ovladače zobrazení systému Windows. WDDM je k dispozici na počítačích se systémy Windows Vista a Windows 7. XPDM je k dispozici na počítačích se systémy Windows Vista, Microsoft Windows XP a Microsoft Windows Server 2003. Další informace o WDDM naleznete v tématu [Průvodce návrhem řídicích ovladačů systému Windows (WDDM)](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide).  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, jestli má být povolená hardwarová akcelerace.|  
|**Maximální hodnota pro více vzorků**|Určuje stupeň vícenásobného vzorkování pro antialiasing 3D obsah.|  
|**Požadované nastavení data ovladače videa**|Určuje, jestli systém zakáže hardwarovou akceleraci pro ovladače vydané před listopadu 2004.|  
|**Použít možnost rastrového odkazu**|Určuje, jestli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se má použít rastrový rastrový odkaz.|  
  
 K těmto nastavením může mít přístup kterýkoli externí konfigurační nástroj, který ví, jak odkazovat na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení registru. Tato nastavení se dají vytvářet nebo upravovat taky tak, že se přistupují k hodnotám přímo pomocí Editoru registru Windows.  
  
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
  
 **Maximální hodnota pro více vzorků** umožňuje upravit maximální množství antialiasing 3D obsahu. Tuto úroveň použijte k zakázání 3D antialiasing v systému Windows Vista.  
  
 **Maximální hodnota více vzorků** je hodnota DWORD, která je v rozsahu od 0 do 16. Hodnota 0 určuje, že se má vypnout antialiasing 3D obsahu s více vzorky a hodnota 16 se pokusí použít až 16x antialiasing s více ukázkami, pokud je tato grafická karta podporovaná. Mějte na paměti, že nastavení této hodnoty klíče registru na počítačích, které používají ovladače XPDM, způsobí, že aplikace budou používat velké množství dalších video paměti, sníží se výkon prostorového vykreslování a bude mít potenciál k zavedení chyb vykreslování a problémů s stabilitou.  
  
 Pokud není tento klíč registru nastavený, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Výchozí hodnota je 0 pro ovladače XPDM a 4 pro ovladače WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>Požadované nastavení data ovladače videa  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Řetězec|  
  
 V listopadu 2004 společnost Microsoft vydala novou verzi pokynů pro testování ovladačů; ovladače napsané po tomto datu nabízejí lepší stabilitu. Ve výchozím nastavení použije [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kanál hardwarové akcelerace pro tyto ovladače a přejde zpět na softwarové vykreslování pro ovladače XPDM publikované před tímto datem.  
  
 **Požadované nastavení data ovladače videa** vám umožní zadat alternativní datum minima pro XPDM ovladače. Měli byste zadat jenom datum starší než listopadu 2004, pokud máte jistotu, že váš ovladač videa je dostatečně stabilní, aby podporoval [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
 Požadované nastavení ovladače videokarty má řetězec v následujícím formátu:  
  
| |  
|-|  
|*RRRR* `/` *MM* `/` *DD* mm|  
  
 Kde *RRRR* je čtyřmístné číslo roku, *mm* je dvoumístný měsíc a *DD* je dva číslice dne. Pokud je tato hodnota nastavená na hodnotu zrušit, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použije se jako požadované datum ovladače videa 2004. listopadu.  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>Použít možnost rastrového odkazu  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Možnost použít rastrový odkaz** umožňuje vynutit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] režim vykreslování simulovaného hardwaru pro ladění: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přejde do režimu hardwaru, ale místo skutečného hardwarového zařízení používá nástroj Microsoft Direct3D reference software Rastrováním d3dref9.dll.  
  
 Rastrový rastr je velmi pomalý, ale obchází ovladač videa, aby nedocházelo k problémům s vykreslováním způsobeným problémy s ovladačem. Z tohoto důvodu můžete použít rastrový odkaz k určení, zda je příčinou problémy vykreslování ovladačem videokarty. Soubor d3dref9.dll musí být v umístění, kde k němu aplikace má přístup, například v libovolném umístění v systémové cestě nebo v místním adresáři aplikace.  
  
 **Možnost použít rastrový odkaz** má hodnotu DWORD. Hodnota 0 značí, že se nepoužívá rastrový rastr. Jakákoli jiná nenulová hodnota vynutí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použití rastrového rastrového odkazu.  
  
## <a name="see-also"></a>Viz také

- [Vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
