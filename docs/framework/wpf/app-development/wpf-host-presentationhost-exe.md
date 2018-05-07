---
title: Hostitel WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: ca8198e17bec62866b6a58e6fd14ea468308f48b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-host-presentationhostexe"></a>Hostitel WPF (PresentationHost.exe)
Windows Presentation Foundation (WPF) hostitele (PresentationHost.exe) je aplikace, která umožňuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace pro hostování v prohlížečích kompatibilní (včetně [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] a novější). Ve výchozím nastavení, je hostitele Windows Presentation Foundation (WPF) zaregistrovaný jako prostředí a [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] hostované prohlížečem obslužné rutiny pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsah, který zahrnuje:  
  
-   Přijít (– nezkompilovaný) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory (XAML).  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Pro soubory z těchto typů hostitele Windows Presentation Foundation (WPF):  
  
-   Spustí zaregistrovanou [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] obslužné rutiny pro hostování daného obsahu Windows Presentation Foundation (WPF).  
  
-   Načte správné verze požadované [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] a sestavení Windows Presentation Foundation (WPF).  
  
-   Zajišťuje, že příslušná úroveň oprávnění pro danou zónu nasazení jsou na místě.  
  
 Toto téma popisuje parametry příkazového řádku, které lze použít s PresentationHost.exe.  
  
## <a name="usage"></a>Použití  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|filename|Cesta k souboru chcete aktivovat. Může být také [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-ladění|Při aktivaci aplikace, nebudou ho pro potvrzení a spustit z úložiště. Funguje pouze když je aktivován místního souboru.|  
|-debugSecurityZoneURL \<adresa url >|Použít s [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] hodnotu udávající PresentationHost.exe, že aplikace by měla ladit, jako kdyby byly nasazeny ze zadaného [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]. Určuje zóny nasazení a lokality původu.|  
|-Vložení|Vyžaduje OLE. Pokud `-event` nebo `-debug` jsou parametr zadán, není nutné zadávat `-embedding` parametr, protože tento parametr je nastaven interně.|  
|-událostí \<eventname >|Otevřete událost s tímto názvem a signalizován ho PresentationHost.exe je inicializována a připravena hostitel [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsah. PresentationHost.exe bude ukončen. Pokud došlo k chybě při otevírání události, jako třeba když ho dosud nebyla vytvořena.|  
|-launchApplication \<adresa url >|Spouští samostatný [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikace ze zadané adresy URL. [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] a jsou použity zásady zabezpečení WinINet týkající se aplikací .NET.|  
  
## <a name="scenarios"></a>Scénáře  
  
### <a name="shell-handler"></a>Obslužná rutina prostředí  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>Obslužná rutina MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Ladění v sadě Visual Studio  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Ladění v zóně sady Visual Studio  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../../docs/framework/wpf/security-wpf.md)
