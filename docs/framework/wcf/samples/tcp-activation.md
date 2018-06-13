---
title: Aktivace protokolem TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 9f08864c1d5139160ac25e0733ddcfc1c8557ad9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807403"
---
# <a name="tcp-activation"></a>Aktivace protokolem TCP
Tento příklad znázorňuje hostování službu, která používá k aktivaci služby, který komunikuje přes protokol net.tcp služby Aktivace procesů systému Windows (WAS). Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 Ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované v pracovním procesu aktivován WAS. Činnost klienta je viditelný v okně konzoly.  
  
 Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobení a dělení), jak je znázorněno v následujícím ukázkovém kódu:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Implementace služby vypočítá a vrátí výsledek ve odpovídající:  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 Příklad používá jeho variantě net.tcp s sdílení portů TCP povoleno a zabezpečení vypnutý. Pokud chcete použít zabezpečené vazba TCP, změňte režim zabezpečení serveru na požadované nastavení a spusťte znovu Svcutil.exe na straně klienta pro generování konfigurační soubor aktualizace klienta.  
  
 Následující příklad ukazuje konfiguraci pro službu:  
  
```xml  
<system.serviceModel>  
  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->  
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="PortSharingBinding" portSharingEnabled="true">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Koncový bod klienta je nakonfigurován, jak je znázorněno v následujícím ukázkovém kódu:  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <netTcpBinding>  
          <binding name="NetTcpBinding_ICalculator">  
            <security mode="None"/>  
          </binding>  
        </netTcpBinding>  
    </bindings>  
    <client>  
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"  
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />  
    </client>  
</system.serviceModel>  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je nainstalovaná. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je vyžadována pro aktivace WAS.  
  
2.  Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Kromě toho je třeba nainstalovat součásti Aktivace jiným protokolem než HTTP WCF:  
  
    1.  Z **spustit** nabídce zvolte **ovládací panely**.  
  
    2.  Vyberte **programy a funkce**.  
  
    3.  Klikněte na tlačítko **součásti systému Windows vypnutí a zapnutí**.  
  
    4.  Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontroly **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.  
  
3.  Konfigurace WAS pro podporu Aktivace protokolem TCP.  
  
     Pro potřeby následující dva kroky jsou implementované v dávkovém souboru názvem AddNetTcpSiteBinding.cmd umístěný v adresáři ukázka.  
  
    1.  Kvůli podpoře aktivace net.tcp, nutné ji nejdřív svázat výchozí web na net.tcp port. To lze provést pomocí Appcmd.exe, která se instaluje s sady nástrojů pro správu Internetové informační služby 7.0 (IIS). Z příkazového řádku na úrovni správce spusťte následující příkaz:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  Tento příkaz je na jednom řádku textu. Tento příkaz přidá vazbu net.tcp lokality na výchozí web naslouchá na portu TCP 808 s žádné název hostitele.  
  
    2.  Přestože všechny aplikace v rámci lokality sdílet běžné net.tcp vazbu, každá aplikace můžete povolit podporu net.tcp jednotlivě. Pokud chcete povolit net.tcp /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku na úrovni správce:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu. Tento příkaz povolí aplikaci /servicemodelsamples získat přístup pomocí obou http://localhost/servicemodelsamples a net.tcp://localhost/servicemodelsamples.  
  
4.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
     Odeberte net.tcp vazby webu, který jste přidali Tato ukázka.  
  
     Pro potřeby následující dva kroky jsou implementované v dávkovém souboru názvem RemoveNetTcpSiteBinding.cmd umístěný v adresáři ukázka.  
  
    1.  Odebrání net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku na úrovni správce:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tento příkaz musí být zadán jako jeden řádek textu.  
  
    2.  Odebrání vazby webu net.tcp spuštěním následujícího příkazu z příkazového řádku na úrovni správce:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz musí být zadán v jako jeden řádek textu.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
