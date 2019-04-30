---
title: 'Postupy: Vytváření služeb systému Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 469074336c8aa49fee1acf871360f8dbc1363247
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914148"
---
# <a name="how-to-create-windows-services"></a>Postupy: Vytváření služeb systému Windows
Při vytváření služby můžete použít šablonu projektu sady Visual Studio volá **Windows Service**. Tato šablona automaticky provádí velkou část práce za vás odkazováním na příslušné třídy a obory názvů, nastavením dědičnosti ze základní třídy pro služby, a přepisováním několika metod, které budete pravděpodobně chtít přepsat.  
  
> [!WARNING]
>  Šablona projektu služby Windows není k dispozici v edici Express sady Visual Studio.  
  
 Minimálně pro vytvoření funkční služby je potřeba:  
  
- Nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost.  
  
- Vytvořte nezbytné instalační programy pro aplikaci služby.  
  
- A zadejte kód pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody, chcete-li přizpůsobit způsoby, jak se chová vaší služby.  
  
### <a name="to-create-a-windows-service-application"></a>Vytvoření aplikace služby Windows  
  
1. Vytvoření **Windows Service** projektu.  
  
    > [!NOTE]
    >  Pokyny pro zápis služby bez použití šablony najdete v tématu [jak: Zápis služeb prostřednictvím kódu programu](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2. V **vlastnosti** okno, nastaveno <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro vaši službu.  
  
     ![Nastavte vlastnost ServiceName. ](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  Hodnota <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti musí vždy odpovídat názvu v instalačních třídách. Pokud tuto vlastnost změníte, je nutné aktualizovat <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost také instalačních tříd.  
  
3. Nastavte libovolné z následujících vlastností určíte, jak služba funguje.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True` Chcete-li určit, že služba bude přijímat žádosti o zastavení činnosti; `false` zabránit zastavení služby.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True` k označení, že služba chce obdržet oznámení, při vypnutí počítače, ve kterém žije, aby mohla volat <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> postup.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True` Chcete-li určit, že služba bude přijímat žádosti o pozastavení nebo obnovení činnosti; `false` zabránit službě pozastavit a obnovit.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` k označení, že služba může zpracovat oznámení změny stavu napájení počítače; `false` zabránit službě dostávat oznámení těchto změn.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True` pro zápis informačních položek do protokolu událostí aplikace, když služba provede akci; `false` zakázat tuto funkci. Další informace najdete v tématu [jak: Protokolování informací o službách](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Poznámka:**  Ve výchozím nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> je nastavena na `true`.|  
  
    > [!NOTE]
    >  Když <xref:System.ServiceProcess.ServiceBase.CanStop%2A> nebo <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jsou nastaveny na `false`, **správce řízení služeb** zakáže odpovídající možnosti nabídky zastavit, pozastavit nebo pokračovat ve službě.  
  
4. Přístup k editoru kódu a vyplňte zpracování, které požadujete pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy.  
  
5. Přepište všechny jiné metody, pro které chcete definovat funkci.  
  
6. Přidejte nezbytné instalační programy pro aplikaci služby. Další informace najdete v tématu [jak: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7. Sestavte projekt výběrem **sestavit řešení** z **sestavení** nabídky.  
  
    > [!NOTE]
    >  Nepoužívejte klávesu F5 ke spuštění projektu – tímto způsobem nelze spustit projekt služby.  
  
8. Nainstalujte službu. Další informace najdete v tématu [jak: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Postupy: Zápis služeb prostřednictvím kódu programu](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)
- [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Postupy: Protokolu informace o službách](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [Postupy: Spuštění služeb](../../../docs/framework/windows-services/how-to-start-services.md)
- [Postupy: Určení kontextu zabezpečení pro služby](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
- [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Návod: Vytvoření aplikace služby Windows v Návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
