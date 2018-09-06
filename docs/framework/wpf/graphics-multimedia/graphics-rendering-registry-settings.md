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
ms.openlocfilehash: acaa8f2ff6611f2f0beb07b74193341edfa2a428
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035988"
---
# <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky
Toto téma obsahuje přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení registru, které ovlivňují vykreslování grafiky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.  
  

  
<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kdy použít nastavení registru pro vykreslení grafiky  
 Tato nastavení registru jsou k dispozici pro řešení potíží, ladění a účely podpory produktu. Protože změny do registru ovlivní všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, aplikace by mělo nikdy změnit tyto klíče registru, automaticky, nebo v průběhu instalace.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>Co jsou XPDM a WDDM?  
 Některé z nastavení registru pro vykreslení grafiky mít různé výchozí hodnoty, v závislosti na tom, zda grafická karta používá XPDM nebo WDDM ovladače. Je XPDM [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] Model ovladače pro zobrazení a WDDM je Model ovladače zobrazení Windows. Je k dispozici v počítačích se systémem WDDM [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] a [!INCLUDE[win7](../../../../includes/win7-md.md)]. Je k dispozici v počítačích se systémem XPDM [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], a [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)]. Další informace o WDDM najdete v tématu [Průvodce návrhem modelu zobrazení ovladač aplikace Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, zda by měla být povolená hardwarová akcelerace.|  
|**Maximální hodnota Multisample**|Určuje, do jaké míry multisampling pro vyhlazení [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obsah.|  
|**Vyžaduje ovladačem grafické karty data nastavení**|Určuje, zda systém zakáže hardwarovou akceleraci ovladače vydané před listopadem 2004.|  
|**Pomocí možnosti odkaz rasterizéru**|Určuje, zda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používejte rasterizéru referenčního.|  
  
 Tato nastavení je možný přes všechny externí konfigurační nástroj, který se ví, jak odkazovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení registru. Tato nastavení také můžou vytvořit nebo upravit přístup k hodnoty přímo s použitím [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Editor registru.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Zakázat možnost hardwarové akcelerace  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Zakázat možnost hardwarové akcelerace** umožňuje vypnutí hardwarové akcelerace pro účely ladění a testování. Když se zobrazí artefakty vykreslování v aplikaci, vypněte hardwarovou akceleraci. Pokud artefakt zmizí, může být problém s ovladač videa.  
  
 **Zakázat možnost hardwarové akcelerace** je hodnota DWORD 0 nebo 1. Hodnota 1 vypne hardwarovou akceleraci. Hodnota 0 povolí hardwarovou akceleraci předpokladu, že systém splňuje požadavky na hardware akcelerace; Další informace najdete v tématu [vrstvy vykreslování grafiky](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>Maximální hodnota Multisample  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maximální hodnota multisample** umožňuje nastavit maximální dobu, vyhlazení z [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obsah. Pomocí této úrovni můžete zakázat [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] antialiasingu v [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] nebo ji povolit v [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].  
  
 **Maximální hodnota multisample** je hodnota DWORD rozsahu od 0 do 16. Hodnota 0 určuje, že by mělo být zakázáno multisample vyhlazení 3D obsahu a hodnotu 16, pokusí se použít až 16 x multisample vyhlazení, pokud nepodporuje grafické karty. Mějte na paměti, že nastavení této hodnoty klíče registru na počítačích s ovladači XPDM způsobí aplikací použít velké množství paměti další videa, snížit výkon [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] vykreslování a má potenciál způsobit chyby vykreslování a problémy se stabilitou.  
  
 Pokud není nastaven tento klíč registru, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výchozí hodnota je 0 XPDM ovladače a 4 pro WDDM ovladače.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Vyžaduje ovladačem grafické karty data nastavení  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 V listopadu 2004 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] vydali novou verzi ovladače testování pokyny; ovladače zapsat po toto datum stabilitu lepší nabídku. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] budete používat pro tyto ovladače kanálu akcelerace hardwarové a softwarové vykreslování XPDM ovladače publikované před tímto datem přejde zpět.  
  
 **Vyžaduje nastavení data ovladačem grafické karty** umožňuje určit alternativní minimální datum XPDM ovladače. Měli byste zadat pouze data starší než dne, 2004 Pokud si nejste jistí, že je ovladač videa dostatečně stabilní, aby podporují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Toto nastavení vyžaduje ovladačem grafické karty přijímá řetězec v následujícím formátu:  
  
| |  
|-|  
|*RRRR* `/` *MM* `/` *DD*|  
  
 Kde *rrrr* je čtyřmístný rok *MM* je dvoumístným měsícem a *DD* je den dvě číslice. Pokud tato hodnota není nastavená, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá. listopadu 2004 jako jeho požadovaný ovladačem grafické karty datum.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Pomocí možnosti odkaz rasterizéru  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Pomocí možnosti odkaz rasterizéru** umožňuje vynutit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do režimu vykreslování simulované hardwaru pro ladění: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přejde do režimu hardwaru, ale používá [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] odkazovat rasterizéru softwaru d3dref9.dll namísto skutečné hardwarové zařízení.  
  
 Rasterizéru referenčního je velmi pomalé, ale vynechá ovladač videa, aby všechny problémy s vykreslováním způsobeny problémy ovladače. Z tohoto důvodu můžete rasterizéru referenčního k určení, pokud vykreslování problémy jsou způsobené ovladačem grafické karty. Soubor d3dref9.dll musí být v umístění, kam aplikace přístup, jako například do libovolného umístění v systémové cestě nebo v místním adresáři aplikace.  
  
 **Pomocí možnosti odkaz rasterizéru** přebírá hodnotu DWORD. Hodnota 0 znamená, že se nepoužívá rasterizéru referenčního. Další vynutí nenulové hodnoty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rasterizéru referenčního používat.  
  
## <a name="see-also"></a>Viz také  
 [Vrstvy vykreslování grafiky](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
