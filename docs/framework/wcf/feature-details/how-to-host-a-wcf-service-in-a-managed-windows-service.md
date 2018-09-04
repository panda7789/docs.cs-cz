---
title: 'Postupy: Hostování služby WCF ve spravované službě Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: edbc67ddf20eee6ebbe9091faa43bc1de91809d2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557901"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Postupy: Hostování služby WCF ve spravované službě Windows

Toto téma popisuje základní kroky potřebné k vytvoření služby Windows Communication Foundation (WCF), který je hostitelem služby Windows. Ve scénáři zajišťuje hostování možnost, která je dlouho běžící služby WCF hostované mimo Internetové informační služby (IIS) v zabezpečeném prostředí, který není zpráva aktivuje spravované služby Windows. Doba platnosti služby je místo toho řídí operační systém. Tato možnost hostování je k dispozici ve všech verzích Windows.

Windows services můžete spravovat pomocí Microsoft.ManagementConsole.SnapIn v konzole Microsoft Management Console (MMC) a dá se nespustí automaticky při spuštění systému. Tato možnost hostování se skládá z registrace domény aplikace (AppDomain), který je hostitelem služby WCF je spravovaná služba Windows tak, že doba platnosti procesu služby se řídí podle správce řízení služeb (SCM) pro služby Windows.

Kód služby obsahuje implementace služby kontraktu služby, služby Windows třídy a třídu Instalační služby. Třída implementace služby `CalculatorService`, je služba WCF. `CalculatorWindowsService` Je služba Windows. K získání způsobilosti jako služba Windows, třída dědí z `ServiceBase` a implementuje `OnStart` a `OnStop` metody. V `OnStart`, <xref:System.ServiceModel.ServiceHost> se vytvoří pro `CalculatorService` zadejte a otevřít. V `OnStop`, služba je zastaven a odstraněn. Hostitel je také odpovídají za poskytování základní adresu k hostiteli služby, který je nakonfigurovaný v nastavení aplikace. Instalační třída, která dědí z <xref:System.Configuration.Install.Installer>, umožňuje programu nainstalovat jako službu Windows pomocí nástroje Installutil.exe.

## <a name="construct-the-service-and-provide-the-hosting-code"></a>Vytvoření služby a zadejte kód hostování

1.  Vytvořit novou sadu Visual Studio **konzolovou aplikaci** projekt s názvem **služby**.

2.  Přejmenujte soubor Program.cs Service.cs.

3.  Změna oboru názvů `Microsoft.ServiceModel.Samples`.

4.  Přidejte odkazy na následující sestavení:

    - System.ServiceModel.dll

    - System.ServiceProcess.dll

    - System.Configuration.Install.dll

5.  Přidejte následující příkazy using do Service.cs.

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6.  Definovat `ICalculator` kontraktu služby, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7.  Implementace kontraktu služby ve třídě volá `CalculatorService` jak je znázorněno v následujícím kódu.

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8.  Vytvořit novou třídu s názvem `CalculatorWindowsService` , která dědí z <xref:System.ServiceProcess.ServiceBase> třídy. Přidat místní proměnnou s názvem `serviceHost` na odkaz <xref:System.ServiceModel.ServiceHost> instance. Definovat `Main` metodu, která volá `ServiceBase.Run(new CalculatorWindowsService)`

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. Přepsat <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metody vytvoření a otevřením nového <xref:System.ServiceModel.ServiceHost> instance, jak je znázorněno v následujícím kódu.

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. Přepsat <xref:System.ServiceProcess.ServiceBase.OnStop%2A> ukončovací metoda <xref:System.ServiceModel.ServiceHost> jak je znázorněno v následujícím kódu.

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. Vytvořit novou třídu s názvem `ProjectInstaller` , která dědí z <xref:System.Configuration.Install.Installer> a, který je označený <xref:System.ComponentModel.RunInstallerAttribute> nastavena na `true`. To umožňuje službě Windows a nainstalovat nástroj Installutil.exe.

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. Odeberte `Service` třídu, která byla vygenerována při vytváření projektu.

13. Přidání konfiguračního souboru aplikace do projektu. Obsah souboru nahraďte následujícím konfiguračním souboru XML.

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

     V souboru App.config klikněte pravým tlačítkem myši **Průzkumníka řešení** a vyberte **vlastnosti**. V části **kopírovat do výstupního adresáře** vyberte **kopírovat, pokud je novější**.

     Tento příklad explicitně určuje koncové body v konfiguračním souboru. Pokud nemůžete přidat žádné koncové body pro službu, modulu runtime přidá výchozí koncové body za vás. V tomto příkladě vzhledem k tomu, že služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavena na `true`, vaše služba má také povoleno publikování metadat. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="install-and-run-the-service"></a>Instalace a spuštění služby

1.  Sestavte řešení k vytvoření `Service.exe` spustitelný soubor.

2.  Otevřete Developer Command Prompt pro sadu Visual Studio a přejděte do adresáře projektu. Typ `installutil bin\service.exe` příkazového řádku pro instalaci služby Windows.

     Typ `services.msc` příkazového řádku pro přístup k správce řízení služeb (SCM). Služba Windows by se zobrazit v služby jako "WCFWindowsServiceSample". Služby WCF můžete reagovat jen na klienty, pokud je služba Windows spuštěná. Spustit službu, klikněte pravým tlačítkem na ho v SCM a vyberte možnost "Spustit" nebo typ **net start WCFWindowsServiceSample** příkazového řádku.

3.  Pokud provedete změny ve službě, musíte ji zastavit a odinstalujte ho. Zastavte službu, klikněte pravým tlačítkem na službu v SCM a vyberte "Stop", nebo **typ net stop WCFWindowsServiceSample** příkazového řádku. Všimněte si, že pokud zastavíte službu Windows a pak spusťte klienta, <xref:System.ServiceModel.EndpointNotFoundException> dojde k výjimce, když se klient pokusí o přístup ke službě. Chcete-li odinstalovat typ služby Windows **installutil /u bin\service.exe** příkazového řádku.

## <a name="example"></a>Příklad

Tady je úplný seznam všech kód použitý v tomto tématu:

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

Podobně jako možnost "Samoobslužné hostování" hostitelským prostředím služby Windows vyžaduje, že některé kód hostování se zapisují jako součást aplikace. Služba se implementuje jako konzolovou aplikaci a obsahuje vlastní kód hostování. V jiných hostitelských prostředích, jako je například Windows Process Activation Service (WAS) hostování v Internetové informační služby (IIS), není nutné pro vývojářům umožňuje psát kód hostování.

## <a name="see-also"></a>Viz také

- [Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)
- [Hostování ve spravované aplikaci](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)