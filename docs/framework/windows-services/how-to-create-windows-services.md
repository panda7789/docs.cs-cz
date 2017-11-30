---
title: "Postupy: Vytváření služeb systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: c4d7f2f19c8d156f86513ac7138bccd59ae3b7fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-windows-services"></a>Postupy: Vytváření služeb systému Windows
Když vytváříte službu, můžete použít šabloně projektu sady Visual Studio s názvem **služba systému Windows**. Tato šablona automaticky provede většinu práce vám tak, že odkazy na příslušné třídy a obory názvů, nastavení dědičnosti ze základní třídy pro služby, a přepsání několik metod budete pravděpodobně chcete přepsat.  
  
> [!WARNING]
>  Šablona projektu služby systému Windows není k dispozici v edici Express sady Visual Studio.  
  
 Minimálně vytvoření funkčnosti služby, musíte:  
  
-   Nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost.  
  
-   Vytvořte potřebné instalační programy pro aplikaci služby.  
  
-   Přepsat a zadat kód pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody pro přizpůsobení způsobů, jak se chová služby.  
  
### <a name="to-create-a-windows-service-application"></a>Vytvoření aplikace služby systému Windows  
  
1.  Vytvoření **služba systému Windows** projektu.  
  
    > [!NOTE]
    >  Pokyny pro zápis služby bez použití šablony, v tématu [postupy: zápis služeb prostřednictvím kódu programu](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2.  V **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro vaši službu.  
  
     ![Nastavte vlastnost ServiceName. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  Hodnota <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost musí vždy odpovídat názvu zaznamenávají v třídách Instalační služby. Pokud tuto vlastnost změníte, musíte aktualizovat <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost také třídy Instalační služby.  
  
3.  Nastavte následující vlastnosti k určení, jak bude vaše služba fungovat.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True`k označení, že služba bude přijímat žádosti o zastaví; `false` zabránit zastavenou službu.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True`k označení, že služba chce dostávat oznámení při vypnutí počítače, na kterém je umístěn mimo provoz, povolení k volání <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> postupu.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True`k označení, že služba bude přijímat požadavky pozastavit nebo obnovit systémem; `false` aby služby z je pozastavený a obnovený.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`k označení, že služba dokáže zpracovat oznámení změny stavu napájení počítače; `false` zabránit službu upozornění na tyto změny.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True`k zápisu informační položky do protokolu událostí aplikace, když služby provádí akce; `false` zakázat tuto funkci. Další informace najdete v tématu [postup: protokolu informace o služby](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Poznámka:** ve výchozím nastavení, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> je nastaven na `true`.|  
  
    > [!NOTE]
    >  Když <xref:System.ServiceProcess.ServiceBase.CanStop%2A> nebo <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jsou nastaveny na `false`, **správce řízení služeb** vypne odpovídající možností v nabídce zastavit, pozastavit nebo službu dále používat.  
  
4.  Přístup k editoru kódu a vyplňte chcete použít pro zpracování <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy.  
  
5.  Přepište jiné metody, pro které chcete definovat funkce.  
  
6.  Přidejte nezbytné instalační programy pro aplikaci služby. Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7.  Sestavení projektu výběrem **sestavit řešení** z **sestavení** nabídky.  
  
    > [!NOTE]
    >  Není stisknutím klávesy F5 spusťte projekt – služba projektu nelze spustit tímto způsobem.  
  
8.  Nainstalujte službu. Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikace služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: zápis služeb prostřednictvím kódu programu](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Postupy: protokolování informací o službách](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Postupy: spuštění služeb](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Postupy: určení kontextu zabezpečení pro služby](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [Postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
