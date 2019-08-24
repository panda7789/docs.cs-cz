---
title: 'Postupy: Vytváření služeb systému Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 960d30f4e484238e9e7c23741578650a8c3005c8
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987155"
---
# <a name="how-to-create-windows-services"></a>Postupy: Vytváření služeb systému Windows
Při vytváření služby můžete použít šablonu projektu sady Visual Studio s názvem **služba systému Windows**. Tato šablona automaticky provede spoustu práce za vás odkazem na příslušné třídy a obory názvů, nastavením dědičnosti ze základní třídy pro služby a přepsáním několika metod, které pravděpodobně chcete přepsat.  
  
> [!WARNING]
> Šablona projektu služby systému Windows není k dispozici v edici Express sady Visual Studio.  
  
 Aby bylo možné vytvořit funkční službu, musíte:  
  
- <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Nastavte vlastnost.  
  
- Vytvořte potřebné instalační programy pro aplikaci služby.  
  
- Přepsat a zadat kód pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pro přizpůsobení způsobů, kterými se vaše služba chová.  
  
### <a name="to-create-a-windows-service-application"></a>Vytvoření aplikace služby systému Windows  
  
1. Vytvořte projekt **služby systému Windows** .  
  
    > [!NOTE]
    > Pokyny k zápisu služby bez použití šablony najdete v tématu [How to: Napište služby](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)programově.  
  
2. V okně **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro vaši službu.  
  
     ![Nastavte vlastnost ServiceName.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    > Hodnota <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti musí vždy odpovídat názvu zaznamenanému v instalačních třídách. Změníte-li tuto vlastnost, je nutné aktualizovat <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> také vlastnost instalačních tříd.  
  
3. Nastavením libovolné z následujících vlastností určíte, jak bude služba fungovat.  
  
    |Vlastnost|Nastavení|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True`pro indikaci, že služba bude přijímat žádosti o zastavení provozu; `false` zabránit zastavení služby.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True`pro indikaci, že služba chce dostávat oznámení, když počítač, ve kterém se nachází, je vypnutý, a umožňuje tak <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> volání procedury.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True`pro indikaci, že služba bude přijímat požadavky na pozastavení nebo pokračování v běhu; `false` brání pozastavení a obnovení služby.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`pro indikaci, že služba může zpracovávat oznámení o změnách stavu napájení počítače. `false` brání službě v upozorňování na tyto změny.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True`zápis informativních položek do protokolu událostí aplikace, když vaše služba provádí akci; `false` tuto funkci můžete zakázat. Další informace najdete v tématu [jak: Protokoluje informace o](../../../docs/framework/windows-services/how-to-log-information-about-services.md)službách. **Poznámka:**  Ve výchozím nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> je nastavena na `true`.|  
  
    > [!NOTE]
    > Pokud <xref:System.ServiceProcess.ServiceBase.CanStop%2A> `false`nebo <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jsou nastaveny na, **správce řízení služeb** zakáže odpovídající možnosti nabídky pro zastavení, pozastavení nebo pokračování služby.  
  
4. Přihlaste se k editoru kódu a vyplňte požadované zpracování pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> postupy a. <xref:System.ServiceProcess.ServiceBase.OnStop%2A>  
  
5. Přepište jakékoli jiné metody, pro které chcete definovat funkčnost.  
  
6. Přidejte nezbytné instalační programy pro aplikaci služby. Další informace najdete v tématu [jak: Přidejte instalační programy do aplikace](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)služby.  
  
7. Sestavte projekt výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .  
  
    > [!NOTE]
    > Netiskněte klávesu F5 pro spuštění projektu – projekt služby nemůžete tímto způsobem spustit.  
  
8. Nainstalujte službu. Další informace najdete v tématu [jak: Nainstalujte a odinstalujte](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)služby.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Postupy: Programové psaní služeb](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)
- [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Postupy: Protokolovat informace o službách](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [Postupy: Spustit služby](../../../docs/framework/windows-services/how-to-start-services.md)
- [Postupy: Určení kontextu zabezpečení pro služby](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
- [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
