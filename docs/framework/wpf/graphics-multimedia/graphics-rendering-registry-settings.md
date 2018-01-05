---
title: "Nastavení registru pro vykreslení grafiky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a760f910bfd9e64fddfe2e7db3bb380cf744719d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-rendering-registry-settings"></a>Nastavení registru pro vykreslení grafiky
Toto téma obsahuje přehled [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiky vykreslování nastavení registru, které ovlivňují [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  

  
<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Kdy použít nastavení registru vykreslování grafiky  
 Tato nastavení registru jsou uvedené pro řešení potíží, ladění a účely podpory produktu. Protože změny registru mít vliv na všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, aplikace by mělo nikdy změnit tyto klíče registru, automaticky nebo během instalace.  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>Co jsou XPDM a WDDM?  
 Některé grafiky vykreslování nastavení registru mají různé výchozí hodnoty, v závislosti na tom, zda grafická karta používá XPDM nebo WDDM ovladačů. Je XPDM [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] Model ovladače zobrazení a WDDM je Model ovladače zobrazení systému Windows. Je k dispozici v počítačích se systémem WDDM [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] a [!INCLUDE[win7](../../../../includes/win7-md.md)]. Je k dispozici v počítačích se systémem XPDM [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], a [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)]. Další informace o WDDM najdete v tématu [Průvodce Model návrhu zobrazení ovladačů systému Windows Vista](http://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Nastavení registru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje čtyři nastavení registru pro řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování:  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Zakázat možnost hardwarové akcelerace**|Určuje, zda se má povolit hardwarovou akceleraci.|  
|**Maximální hodnota Multisample**|Určuje úroveň multisampling pro vyhlazení [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obsah.|  
|**Požadované ovladače grafické karty datum nastavení**|Určuje, zda systém zakáže hardwarovou akceleraci vydané dřív než listopadu 2004 ovladače.|  
|**Reference – možnost umožňuje použít**|Určuje, zda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] by měl používat umožňuje odkaz.|  
  
 Tato nastavení mají přístup všechny externí konfigurace nástroj, který umí tak, aby odkazovaly [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nastavení registru. Tato nastavení taky můžou vytvořit nebo upravit přístup k hodnoty přímo pomocí [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Editor registru.  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>Zakázat možnost hardwarové akcelerace  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Zakázat možnost hardwarové akcelerace** umožňuje vypnout hardwarovou akceleraci pro účely ladění a testování. Až uvidíte vykreslování artefakty v aplikaci, zakažte hardwarovou akceleraci. Pokud artefaktu zmizí, může být problém s ovladač videa.  
  
 **Zakázat možnost hardwarové akcelerace** je hodnotu DWORD s hodnotou 0 nebo 1. Hodnota 1 vypne hardwarovou akceleraci. Hodnota 0 umožňuje hardwarovou akceleraci zadaný systém splňuje požadavky na hardware akcelerace; Další informace najdete v tématu [vrstev vykreslování grafiky](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>Maximální hodnota Multisample  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maximální hodnota multisample** umožňuje nastavit maximální množství vyhlazení z [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] obsah. Pomocí této úrovni můžete zakázat [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] vyhlazení v [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] nebo povolit v [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].  
  
 **Maximální hodnota multisample** je hodnotu DWORD, rozsahu od 0 do 16. Hodnota 0 určuje, že by mělo být zakázáno multisample vyhlazení 3D obsahu a hodnotu 16 se pokusí použít až 16 x multisample vyhlazení, podporuje-li jej grafické karty. Mějte na paměti, že nastavení této hodnoty klíče registru v počítačích používajících ovladače XPDM způsobí aplikace použít velké množství další grafické paměti, snížit výkon [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] vykreslování a má potenciál zavádět chyb při vykreslování a stabilitu problémy.  
  
 Pokud není nastaven tento klíč registru, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výchozí hodnota je 0 pro XPDM ovladače a 4 pro WDDM ovladače.  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>Požadované ovladače grafické karty datum nastavení  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 V listopadu 2004 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] vydání nové verze ovladače testování pokyny; ovladače zapsat za toto datum nabídka lepší stability. Ve výchozím nastavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použije hardwarové akcelerace kanálu pro tyto ovladače a bude přejít k vykreslování softwaru pro ovladače XPDM před toto datum publikovat.  
  
 **Požadované ovladače grafické karty datum nastavení** můžete určit alternativní minimálního data pro XPDM ovladače. Měli byste zadat pouze dřívější než. listopadu 2004 datum, pokud jste si jisti, že je ovladač videa dostatečně stabilní pro podporu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Nastavení požadované ovladače grafické karty přebírá řetězec následující formát:  
  
||  
|-|  
|*RRRR* `/` *MM* `/` *DD*|  
  
 Kde *rrrr* je čtyřmístný rok *MM* je v měsíci letopočty a *DD* dvoumístné den. Pokud je tato hodnota nenastavenou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá. listopadu 2004 jako jeho datum požadované ovladače grafické karty.  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>Reference – možnost umožňuje použít  
  
|Klíč registru|Typ hodnoty|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Reference – možnost umožňuje použít** umožňuje vynutit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do režimu vykreslování simulované hardwaru pro ladění: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přejde do režimu hardwaru, ale používá [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] odkazovat umožňuje softwaru d3dref9.dll místo skutečným hardwarovým zařízením.  
  
 Umožňuje odkaz je velmi pomalé, ale obchází ovladač videa, aby se zabránilo žádné problémy s vykreslováním způsobeny problémy ovladačů. Z tohoto důvodu můžete odkaz umožňuje určit, pokud jsou způsobeny problémy s vykreslováním ovladače grafické karty. Soubor d3dref9.dll musí být v umístění, kde aplikace k němu přístup, například v žádném z umístění v systémové cestě nebo v místním adresáři aplikace.  
  
 **Reference – možnost umožňuje použít** přebírá hodnotu DWORD. Hodnota 0 určuje, že není umožňuje odkaz použít. Další nenulovou hodnotu vynutí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používat umožňuje odkaz.  
  
## <a name="see-also"></a>Viz také  
 [Vrstvy vykreslování grafiky](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
