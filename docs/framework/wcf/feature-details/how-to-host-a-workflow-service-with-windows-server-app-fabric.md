---
title: 'Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: ecc7a954b2d88cdbcf934cc836e9ad6e3ef7ed52
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964766"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric

Hostování služeb pracovních postupů v App Fabric se podobá hostování v rámci služby IIS/. Jediným rozdílem je, že prostředky aplikace App Fabric poskytují nasazení, monitorování a správu služeb pracovních postupů. V tomto tématu se používá služba pracovního postupu vytvořená v [tématu Vytvoření dlouhotrvající služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Toto téma vás provede vytvořením služby pracovního postupu. V tomto tématu se dozvíte, jak hostovat službu pracovního postupu pomocí App Fabric. Další informace o Windows Server App Fabric najdete v [dokumentaci k Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)). Před dokončením následujících kroků se ujistěte, že máte nainstalované Windows Server App Fabric.  Tuto možnost otevřete Internetová informační služba (inetmgr. exe) tak, že kliknete na název vašeho serveru v zobrazení **připojení** , kliknete na weby a kliknete na **výchozí web**. Na pravé straně obrazovky by se měla zobrazit část s názvem **App Fabric**. Pokud tuto část nevidíte (bude v horní části pravého podokna), nemáte nainstalovanou aplikaci Fabric. Další informace o instalaci Windows serveru App Fabric najdete v tématu [instalace Windows serveru App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee790960(v=azure.10)).  
  
### <a name="creating-a-simple-workflow-service"></a>Vytvoření jednoduché služby pracovního postupu  
  
1. Otevřete Visual Studio 2012 a načtěte řešení OrderProcessing, které jste vytvořili v tématu [Vytvoření dlouhodobě spuštěné služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) .  
  
2. Klikněte pravým tlačítkem na projekt **OrderService** a vyberte **vlastnosti** a vyberte kartu **Web** .  
  
3. V části **spouštěcí akce** stránky vlastností vyberte **konkrétní stránku** a do pole pro úpravy zadejte Service1. xamlx.  
  
4. V části **servery** na stránce vlastností vyberte **použít místní webový server služby IIS** a zadejte následující adresu URL: `http://localhost/OrderService`.  
  
5. Klikněte na tlačítko **vytvořit virtuální adresář** . Tím se vytvoří nový virtuální adresář a nastaví se projekt ke zkopírování potřebných souborů do virtuálního adresáře při sestavení projektu.  Případně můžete ručně zkopírovat soubor. xamlx, Web. config a všechny potřebné knihovny DLL do virtuálního adresáře.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Konfigurace služby pracovního postupu hostovaného v systému Windows Server App Fabric  
  
1. Otevřete Internetová informační služba Manager (inetmgr. exe).  
  
2. V podokně **připojení** přejděte do virtuálního adresáře OrderService.  
  
3. Klikněte pravým tlačítkem na OrderService a vyberte **Spravovat WCF a služby WF**, **Konfigurovat...** . Zobrazí se dialogové okno **konfigurovat WCF a WF pro aplikaci** .  
  
4. Vyberte kartu **Obecné** a zobrazte Obecné informace o aplikaci, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Karta Obecné v dialogovém okně Konfigurace prostředků infrastruktury aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration – obecné")  
  
5. Vyberte kartu **monitorování** . Tato možnost zobrazuje různá nastavení monitorování, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Karta monitorování konfigurace prostředků infrastruktury aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration – monitorování")  
  
     Další informace o konfiguraci monitorování služby pracovního postupu v App Fabric najdete v tématu [Konfigurace monitorování pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677384(v=azure.10)).  
  
6. Vyberte kartu **trvalosti pracovního postupu** . To vám umožní nakonfigurovat aplikaci tak, aby používala výchozího zprostředkovatele trvalosti aplikace App Fabric, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Trvalost konfigurace &#45; prostředků infrastruktury aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration – trvalost")  
  
     Další informace o konfiguraci trvalosti pracovního postupu ve Windows serveru App Fabric najdete v tématu [Konfigurace trvalosti pracovního postupu v App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677353(v=azure.10)).  
  
7. Vyberte kartu **Správa hostitele pracovního postupu** . To vám umožní určit, kdy se mají instance služby nečinných pracovních postupů uvolnit a zachovat, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Správa hostitele pracovního postupu pro konfiguraci prostředků infrastruktury aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration – Správa")  
  
     Další informace o konfiguraci správy hostitele pracovního postupu najdete [v tématu Konfigurace správy hostitele pracovního postupu v App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff383424(v=azure.10)).  
  
8. Vyberte kartu **automatické spuštění** . To umožňuje zadat nastavení automatického spuštění pro služby pracovního postupu v aplikaci, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Snímek obrazovky, který ukazuje konfiguraci&#45;automatického spuštění prostředků infrastruktury aplikace](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     Další informace o konfiguraci automatického spuštění najdete v tématu [Konfigurace automatického startu pomocí App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677261(v=azure.10)).  
  
9. Vyberte kartu **omezování** . To vám umožní nakonfigurovat nastavení omezování pro službu pracovního postupu, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Snímek obrazovky, který ukazuje konfiguraci omezení aplikace App Fabric.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     Další informace o konfiguraci omezení najdete v tématu [Konfigurace omezování pomocí App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677261(v=azure.10)).  
  
10. Vyberte kartu **zabezpečení** . To vám umožní nakonfigurovat nastavení zabezpečení pro aplikaci, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Konfigurace zabezpečení prostředků infrastruktury aplikace](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration – zabezpečení")  
  
     Další informace o konfiguraci zabezpečení pomocí Windows Server App Fabric najdete v tématu [Konfigurace zabezpečení pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677278(v=azure.10)).  
  
### <a name="using-windows-server-app-fabric"></a>Pomocí Windows Server App Fabric  
  
1. Sestavte řešení a zkopírujte potřebné soubory do virtuálního adresáře.  
  
2. Klikněte pravým tlačítkem na projekt OrderClient a vyberte **ladit**, **spustit novou instanci** a spusťte klientskou aplikaci.  
  
3. Klient se spustí a Visual Studio zobrazí dialogové okno **připojit upozornění zabezpečení** , klikněte na tlačítko **Nepřipojeno** . To oznamuje, že se Visual Studio nepřipojí k procesu služby IIS pro ladění.  
  
4. Klientská aplikace okamžitě zavolá službu pracovního postupu a potom počká. Služba pracovního postupu přejde do stavu nečinnosti a bude trvalá. Můžete to ověřit tak, že spustíte Internetová informační služba (inetmgr. exe), přejdete do OrderService v podokně připojení a vyberete ho. Potom v pravém podokně klikněte na ikonu řídicí panel prostředků App Fabric. V části trvalé instance WF se zobrazí jedna trvalá instance služby pracovního postupu, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Snímek obrazovky zobrazující řídicí panel prostředků App Fabric](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     V **historii instance WF** se zobrazí informace o službě pracovního postupu, jako je počet aktivací služby pracovního postupu, počet dokončení instance služby pracovního postupu a počet instancí pracovních postupů s chybami. V části aktivní nebo nečinné instance se zobrazí odkaz na odkaz Zobrazit další informace o instancích nečinných pracovních postupů, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Snímek obrazovky, který ukazuje podrobnosti trvalé instance pracovního postupu.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     Další informace o funkcích Windows Server App Fabric a o tom, jak je používat, najdete v tématu [funkce hostování Windows serveru App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10)) .  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
- [Instalace Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee790960(v=azure.10))
- [Dokumentace k Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10))
