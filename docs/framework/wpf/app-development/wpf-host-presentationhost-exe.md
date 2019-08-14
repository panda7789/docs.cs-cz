---
title: Hostitel WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: eda34c71f5735ae7ea3fcedea3a400e92756243b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972260"
---
# <a name="wpf-host-presentationhostexe"></a>Hostitel WPF (PresentationHost.exe)
Hostitel Windows Presentation Foundation (WPF) (PresentationHost. exe) je aplikace, která umožňuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hostování aplikací v kompatibilních prohlížečích (včetně aplikace Microsoft Internet Explorer 6 a novější). Ve výchozím nastavení je hostitel Windows Presentation Foundation (WPF) zaregistrován jako prostředí a obslužná rutina MIME pro obsah hostovaný [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] v prohlížeči, což zahrnuje:  
  
- Volné (nekompilované) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory (. XAML).  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Pro soubory těchto typů hostitel Windows Presentation Foundation (WPF):  
  
- Spustí zaregistrovanou obslužnou rutinu HTML pro hostování obsahu Windows Presentation Foundation (WPF).  
  
- Načte správné verze požadovaných sestavení modulu CLR (Common Language Runtime) a Windows Presentation Foundation (WPF).  
  
- Zajišťuje, aby byly správné úrovně oprávnění pro zónu nasazení.  
  
 Toto téma popisuje parametry příkazového řádku, které lze použít s PresentationHost. exe.  
  
## <a name="usage"></a>Použití  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|filename|Cesta k souboru, který se má aktivovat Může to [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]být také.|  
|-debug|Při aktivaci aplikace ji nepotvrdí ani nespustí ze Storu. Tato funkce funguje pouze v případě, že je aktivován místní soubor.|  
|-debugSecurityZoneURL \<url>|Používá se s [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] hodnotou pro indikaci PresentationHost. exe, že by měla být aplikace Laděna, jako kdyby byla nasazena ze zadaného [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]. Tím se určuje jak zóna nasazení, tak původní lokalita.|  
|– vkládání|Požadováno OLE. Je-li `-debug` zadán parametr `-embedding` `-event` nebo, není nutné parametr zadat, protože tento parametr je nastaven interně.|  
|-> \<události EventName|Otevřete událost s tímto názvem a nazvěte ji, když se PresentationHost. exe inicializuje a je připravený [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na hostování obsahu. PresentationHost. exe skončí, pokud došlo k chybě při otevírání události, například pokud ještě nebyla vytvořena.|  
|– launchApplication \<URL >|Spustí samostatnou aplikaci ClickOnce ze zadané adresy URL. Aplikují se zásady zabezpečení Internet Exploreru a WinINet týkající se aplikací .NET.|  
  
## <a name="scenarios"></a>Scénáře  
  
### <a name="shell-handler"></a>Obslužná rutina prostředí  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>Obslužná rutina MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Ladění sady Visual Studio  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Ladění sady Visual Studio v zóně  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení](../security-wpf.md)
