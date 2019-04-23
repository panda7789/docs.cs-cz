---
title: Hostitel WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 586d306d0f375241c9382e1e24cf1af75b990ba9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122860"
---
# <a name="wpf-host-presentationhostexe"></a>Hostitel WPF (PresentationHost.exe)
Hostitel Windows Presentation Foundation (WPF) (PresentationHost.exe) je aplikace, která umožňuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace zajistit také jejich hostování v kompatibilní prohlížečů (včetně [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] a novější). Ve výchozím nastavení, je Windows Presentation Foundation (WPF) hostitele zaregistrovaný jako prostředí a [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] obslužné rutiny pro hostované v prohlížeči [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsah, který obsahuje:  
  
-   Přijít o provedené (– nezkompilovaný) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory (.xaml).  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Pro soubory z těchto typů hostitele Windows Presentation Foundation (WPF):  
  
-   Spustí zaregistrovanou [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] obslužné rutiny pro hostování daného obsahu Windows Presentation Foundation (WPF).  
  
-   Načte správné verze požadované [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] a sestavení Windows Presentation Foundation (WPF).  
  
-   Zajišťuje, že příslušná úroveň oprávnění pro zónu nasazení jsou na místě.  
  
 Toto téma popisuje parametry příkazového řádku, které lze použít s PresentationHost.exe.  
  
## <a name="usage"></a>Použití  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|filename|Cesta souboru, který má být aktivován. Může být také [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-debug|Při aktivaci aplikace, není na potvrzení nebo spuštění z úložiště. Toto funguje pouze v případě místního souboru se aktivuje.|  
|-debugSecurityZoneURL \<url>|Použít s [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] hodnotě k označení PresentationHost.exe, aplikace by měl ladit, jako kdyby byly nasazeny z určeného [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]. Určuje zónu nasazení i webovou stránku původu.|  
|-vkládání|Vyžadovány rozhraním OLE. Pokud `-event` nebo `-debug` jsou parametr zadán, není potřeba zadávat `-embedding` parametr, protože tento parametr je nastaven interně.|  
|-události \<eventname >|Otevřete událost s tímto názvem a dají signál, jakmile je inicializována a jste připravení hostitele PresentationHost.exe [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsah. PresentationHost.exe bude ukončen. Pokud došlo k chybě při otevírání události, například když ji dosud nebyla vytvořena.|  
|-launchApplication \<url >|Spouští samostatný [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] ze zadané adresy URL aplikace. [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] a jsou použity zásady zabezpečení rozhraní WinINet týkající se aplikací .NET.|  
  
## <a name="scenarios"></a>Scénáře  
  
### <a name="shell-handler"></a>Obslužná rutina prostředí  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>Obslužná rutina MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Ladění sady Visual Studio  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Ladění v zóně sady Visual Studio  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](../security-wpf.md)
