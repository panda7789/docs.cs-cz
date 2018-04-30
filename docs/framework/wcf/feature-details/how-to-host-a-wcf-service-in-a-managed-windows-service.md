---
title: 'Postupy: Hostování služby WCF ve spravované službě Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aab9780a0d40ab71710d454deb3144219557450f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Postupy: Hostování služby WCF ve spravované službě Windows
Toto téma popisuje základní kroky potřebné pro vytvoření [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služba, která je hostitelem služby systému Windows. Ve spravovaných hostování možnost, která je dlouho běžící služby systému Windows je povoleno scénáři [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované v zabezpečeném prostředí, která není zpráv, ve aktivovat mimo Internetové informační služby (IIS). Doba platnosti služby místo toho řídí operační systém. Tento hostitelský možnost je dostupná ve všech verzích systému Windows.  
  
 Služby systému Windows lze spravovat pomocí Microsoft.ManagementConsole.SnapIn v konzole Microsoft Management Console (MMC) a lze nakonfigurovat automatické spuštění po spuštění systému. Tato možnost hostování se skládá z registraci domény aplikace (AppDomain), který je hostitelem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby jako spravovanou službu systému Windows tak, že doba platnosti procesu služby je řízena pomocí ovládacího prvku Správce služeb (SCM) pro služby systému Windows.  
  
 Kód služby zahrnuje implementace služby kontrakt služby, třídu služby systému Windows a třídu Instalační služby. Třídě implementace služby `CalculatorService`, je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. `CalculatorWindowsService` Je služba systému Windows. Aby se dosáhlo nároku jako služby systému Windows, třídy dědí z `ServiceBase` a implementuje `OnStart` a `OnStop` metody. V `OnStart`, <xref:System.ServiceModel.ServiceHost> se vytvoří `CalculatorService` zadejte a otevřít. V `OnStop`, služba je zastavena a zlikvidován. Hostitel je také zodpovědná za poskytování základní adresa hostitele služby, který byl nakonfigurován v nastavení aplikace. Instalační program třídy, která dědí z <xref:System.Configuration.Install.Installer>, umožňuje program, který chcete nainstalovat nástroj Installutil.exe jako služby systému Windows.  
  
### <a name="construct-the-service-and-provide-the-hosting-code"></a>Vytvoření služby a zadejte kód hostování  
  
1.  Vytvořte nový projekt Visual Studio konzolové aplikace s názvem "Služba".  
  
2.  Přejmenujte Program.cs Service.cs.  
  
3.  Změňte obor názvů na Microsoft.ServiceModel.Samples.  
  
4.  Přidejte odkazy na následující sestavení.  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceProcess.dll  
  
    -   System.Configuration.Install.dll  
  
5.  Přidejte následující příkazy using do Service.cs.  
  
     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]  
  
6.  Definování `ICalculator` kontrakt služby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]  
  
7.  Implementace kontraktu služby ve třídě nazvané `CalculatorService` jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]  
  
8.  Vytvořte novou třídu s názvem `CalculatorWindowsService` který dědí z <xref:System.ServiceProcess.ServiceBase> třídy. Přidat místní proměnné s názvem `serviceHost` k odkazu <xref:System.ServiceModel.ServiceHost> instance. Definování `Main` metoda, která volá `ServiceBase.Run(new CalculatorWindowsService)`  
  
     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]  
  
9. Přepsání <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metoda, při vytváření a otevírání novou <xref:System.ServiceModel.ServiceHost> instance, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]  
  
10. Přepsání <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda zavření <xref:System.ServiceModel.ServiceHost> jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]  
  
11. Vytvořte novou třídu s názvem `ProjectInstaller` který dědí z <xref:System.Configuration.Install.Installer> a který je označený <xref:System.ComponentModel.RunInstallerAttribute> nastavena na `true`. To umožňuje nainstalovat nástroj Installutil.exe služby systému Windows.  
  
     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]  
  
12. Odeberte `Service` třídu, která byla vygenerována, když vytvoříte projekt.  
  
13. Přidejte konfigurační soubor aplikace do projektu. Nahraďte obsah souboru s následující konfigurací XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>    <services>  
          <!-- This section is optional with the new configuration model  
               introduced in .NET Framework 4. -->  
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                   behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
            <endpoint address=""  
                      binding="wsHttpBinding"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceMetadata httpGetEnabled="true"/>  
              <serviceDebug includeExceptionDetailInFaults="False"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Klikněte pravým tlačítkem v souboru App.config **Průzkumníku řešení** a vyberte **vlastnosti**. V části **kopírovat do výstupního adresáře** vyberte **kopírovat, pokud je novější**.  
  
     Tento příklad explicitně určuje koncové body v konfiguračním souboru. Pokud jste ke službě nepřidávejte žádné koncové body, modul runtime přidá výchozí koncové body pro vás. V tomto příkladu protože služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavena na `true`, služby má také publikování metadat povolena. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
### <a name="install-and-run-the-service"></a>Nainstalujte a spusťte službu  
  
1.  Sestavte řešení Chcete-li vytvořit `Service.exe` spustitelný soubor.  
  
2.  Otevřete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek a přejděte do adresáře projektu. Typ `installutil bin\service.exe` příkazového řádku pro instalaci služby Windows.  
  
    > [!NOTE]
    >  Pokud použijete [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek, ujistěte se, že `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` adresář je v cestě k systému.  
  
     Typ `services.msc` příkazového řádku pro přístup k správce řízení služeb (SCM). Služba systému Windows by se zobrazit v služby jako "WCFWindowsServiceSample". [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Služby může odpovědět pouze na klienty, pokud je spuštěná služba Windows. Pokud chcete spustit službu, klikněte pravým tlačítkem ji v SCM a vyberte možnost "Start" nebo typ **net start WCFWindowsServiceSample** na příkazovém řádku.  
  
3.  Pokud provedete změny ve službě, musíte nejprve zastavte ji a odinstalujte ji. Chcete zastavit službu, klikněte pravým tlačítkem na službu v SCM a zvolte "Stop", nebo **typ net stop WCFWindowsServiceSample** na příkazovém řádku. Všimněte si, že pokud zastavíte službu systému Windows a pak spusťte klienta, <xref:System.ServiceModel.EndpointNotFoundException> když se klient pokusí o přístup ke službě došlo k výjimce. Chcete-li odinstalovat typ služby Windows **installutil /u bin\service.exe** na příkazovém řádku.  
  
## <a name="example"></a>Příklad  
 Níže je úplný seznam všech kód použitý v tomto tématu.  
  
 [!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
 [!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]  
  
 Jako možnost "Samoobslužné hostování" hostování prostředí služby systému Windows vyžaduje, aby některé hostování kódu zapsání jako součást aplikace. Služba je implementovaný jako konzolové aplikace a obsahuje vlastní kód pro hostování. V jiných hostitelských prostředích, jako je například služba aktivace procesů systému Windows (WAS) hostování v Internetové informační služby (IIS), není nutné pro vývojáře k zápisu hostování kódu.  
  
## <a name="see-also"></a>Viz také  
 [Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)  
 [Hostování ve spravované aplikaci](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
