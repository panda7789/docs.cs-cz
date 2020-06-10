---
title: 'Postupy: Hostování služby WCF ve spravované službě Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: dbd51abbc30b1010f7c4f206aad9a773eca0a714
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593175"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Postupy: Hostování služby WCF ve spravované službě Windows

Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), která je hostována službou systému Windows. Tento scénář je povolený možností hostování spravované služby systému Windows, která je dlouhodobě běžící služba WCF hostovaná mimo službu Internetová informační služba (IIS) v zabezpečeném prostředí, které není aktivovaná zpráva. Doba života služby se místo toho řídí operačním systémem. Tato možnost hostování je k dispozici ve všech verzích Windows.

Služby systému Windows je možné spravovat pomocí modulu Microsoft. ManagementConsole. snap-in v konzole MMC (Microsoft Management Console) a je možné je nakonfigurovat tak, aby se při spuštění systému automaticky spustily. Tato možnost hostování se skládá z registrace domény aplikace (AppDomain), která je hostitelem služby WCF jako spravované služby systému Windows, aby byla doba životnosti procesu řízena správcem řízení služeb (SCM) pro služby systému Windows.

Kód služby zahrnuje implementaci služby servisního kontraktu, třídy služby systému Windows a instalační třídy. Třída implementace služby, `CalculatorService` , je služba WCF. `CalculatorWindowsService`Je služba systému Windows. Chcete-li se kvalifikovat jako služba systému Windows, třída dědí z `ServiceBase` a `OnStart` implementuje `OnStop` metody a. V je `OnStart` <xref:System.ServiceModel.ServiceHost> vytvořen pro `CalculatorService` typ a otevřen. V nástroji `OnStop` je služba zastavená a vyřazená. Hostitel taky zodpovídá za poskytnutí základní adresy pro hostitele služby, který je nakonfigurovaný v nastavení aplikace. Instalační třída, která dědí z <xref:System.Configuration.Install.Installer> , umožňuje programu instalovat program jako službu systému Windows pomocí nástroje Installutil. exe.

## <a name="construct-the-service-and-provide-the-hosting-code"></a>Sestavte službu a poskytněte hostující kód

1. Vytvořte nový projekt **konzolové aplikace** sady Visual Studio s názvem **Service**.

2. Přejmenujte Program.cs na Service.cs.

3. Změňte obor názvů na `Microsoft.ServiceModel.Samples` .

4. Přidejte odkazy na následující sestavení:

    - System.ServiceModel.dll

    - System. ServiceProcess. dll

    - System.Configuration.Install.dll

5. Do Service.cs přidejte následující příkazy using.

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. Definujte `ICalculator` kontrakt služby, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. Implementujte kontrakt služby ve třídě s názvem `CalculatorService` , jak je znázorněno v následujícím kódu.

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. Vytvořte novou třídu s názvem `CalculatorWindowsService` , která dědí z <xref:System.ServiceProcess.ServiceBase> třídy. Přidejte místní proměnnou s názvem `serviceHost` , aby odkazovala na <xref:System.ServiceModel.ServiceHost> instanci. Definujte `Main` metodu, která volá`ServiceBase.Run(new CalculatorWindowsService)`

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. Přepište <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metodu vytvořením a otevřením nové <xref:System.ServiceModel.ServiceHost> instance, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. Přepsat <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodu, jak je <xref:System.ServiceModel.ServiceHost> znázorněno v následujícím kódu.

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. Vytvořte novou třídu s názvem `ProjectInstaller` , která dědí z <xref:System.Configuration.Install.Installer> a která je označena atributem <xref:System.ComponentModel.RunInstallerAttribute> na hodnotu `true` . To umožňuje instalaci služby systému Windows pomocí nástroje Installutil. exe.

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. Odeberte `Service` třídu, která byla generována při vytváření projektu.

13. Přidejte konfigurační soubor aplikace do projektu. Nahraďte obsah souboru následujícím kódem XML konfigurace.

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

     Klikněte pravým tlačítkem na soubor App. config v **Průzkumník řešení** a vyberte **vlastnosti**. V části **Kopírovat do výstupního adresáře** vyberte **Kopírovat, pokud je novější**.

     Tento příklad explicitně určuje koncové body v konfiguračním souboru. Pokud do služby nepřidáte žádné koncové body, modul runtime přidá pro vás výchozí koncové body. Protože je v tomto příkladu služba <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavená na `true` , má vaše služba také povolenou metadata publikování. Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).

## <a name="install-and-run-the-service"></a>Instalace a spuštění služby

1. Sestavte řešení pro vytvoření `Service.exe` spustitelného souboru.

2. Otevřete Developer Command Prompt pro Visual Studio a přejděte do adresáře projektu. `installutil bin\service.exe`Do příkazového řádku zadejte příkaz pro instalaci služby systému Windows.

     `services.msc`Pro přístup ke Správci řízení služeb (SCM) zadejte na příkazovém řádku. Služba systému Windows by se měla zobrazit v části služby jako "WCFWindowsServiceSample". Služba WCF může reagovat jenom na klienty, pokud je spuštěná služba systému Windows. Chcete-li službu spustit, klikněte na ni pravým tlačítkem myši a vyberte Start nebo zadejte do příkazového řádku příkaz **net start WCFWindowsServiceSample** .

3. Pokud provedete změny služby, musíte ji nejdřív zastavit a odinstalovat. Chcete-li službu zastavit, klikněte pravým tlačítkem myši na službu v SCM a vyberte stop (zastavit) nebo do příkazového řádku **zadejte net stop WCFWindowsServiceSample** . Všimněte si, že pokud zastavíte službu systému Windows a potom spustíte klienta, <xref:System.ServiceModel.EndpointNotFoundException> dojde k výjimce, když se klient pokusí o přístup ke službě. Pokud chcete odinstalovat typ služby systému Windows **Installutil/u bin\service.exe** na příkazovém řádku.

## <a name="example"></a>Příklad

Následuje úplný seznam kódu používaného v tomto tématu:

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

Stejně jako možnost samoobslužné hostování vyžaduje hostující prostředí služby systému Windows, aby byl jako součást aplikace napsán nějaký hostitelský kód. Služba je implementována jako Konzolová aplikace a obsahuje svůj vlastní hostitelský kód. V jiných hostitelských prostředích, jako je služba Aktivace procesů systému Windows (WAS) v Internetová informační služba (IIS), není nutné, aby vývojáři mohli psát hostující kód.

## <a name="see-also"></a>Viz také

- [Zjednodušená konfigurace](../simplified-configuration.md)
- [Hostování ve spravované aplikaci](hosting-in-a-managed-application.md)
- [Služby hostování](../hosting-services.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
