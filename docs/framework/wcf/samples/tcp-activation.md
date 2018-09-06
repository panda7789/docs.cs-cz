---
title: Aktivace protokolem TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: c10cc1edfb06d55fc8a59a32bf905c95b20a19dc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799356"
---
# <a name="tcp-activation"></a>Aktivace protokolem TCP
Tato ukázka předvádí, který je hostitelem služby, které používá služby aktivační procesů Windows (WAS) k aktivaci služby, která komunikuje přes protokol net.tcp. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 Ukázka se skládá z programu konzoly klienta (.exe) a služby knihovny (.dll) hostované v pracovním procesu aktivoval WAS. Činnost klienta je vidět v okně konzoly.  
  
 Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (přidat, odečítání, násobení a rozdělit), jak je znázorněno v následujícím ukázkovém kódu:  
  
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
  
 Implementace služby vypočítá a vrátí odpovídající výsledek:  
  
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
  
 Ukázka používá variantu net.tcp vazby s povoleno sdílení portu TCP a zabezpečení vypnuto. Pokud chcete použít zabezpečený TCP vazby, změňte režim zabezpečení serveru na požadované nastavení a znovu spusťte Svcutil.exe na straně klienta se vygenerovat soubor aktualizace klienta konfigurace.  
  
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
  
 Jak je znázorněno v následujícím ukázkovém kódu, je nakonfigurovaný koncový bod klienta:  
  
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
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je nainstalována. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je vyžadován pro aktivaci WAS.  
  
2.  Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Kromě toho je třeba nainstalovat jiným protokolem než HTTP aktivačních komponent WCF:  
  
    1.  Z **Start** nabídce zvolte **ovládací panely**.  
  
    2.  Vyberte **programy a funkce**.  
  
    3.  Klikněte na tlačítko **součásti Windows zapnout nebo vypnout**.  
  
    4.  Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontrolu **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.  
  
3.  Konfigurace WAS pro podporu Aktivace protokolem TCP.  
  
     V zájmu usnadnění práce následující dva kroky jsou implementovány v dávkovém souboru volá AddNetTcpSiteBinding.cmd nachází v adresáři ukázkové.  
  
    1.  Kvůli podpoře aktivace net.tcp, musíte ji nejdřív svázat výchozí webový server k portu net.tcp. To lze provést pomocí Appcmd.exe, která se instaluje s sada nástrojů pro správu Internetové informační služby 7.0 (IIS). Z příkazového řádku na úrovni správce spusťte následující příkaz:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  Tento příkaz je jeden řádek textu. Tento příkaz přidá vazbu webu net.tcp výchozí webový server naslouchá na portu TCP 808 s libovolný název hostitele.  
  
    2.  Přestože všechny aplikace v rámci lokality sdílejí společné vazby net.tcp, každá aplikace můžete povolit podporu net.tcp jednotlivě. Pokud chcete povolit net.tcp /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku na úrovni správce:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je jeden řádek textu. Tento příkaz umožňuje aplikaci /servicemodelsamples přistupovat pomocí obou http://localhost/servicemodelsamples a net.tcp://localhost/servicemodelsamples.  
  
4.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
     Odeberte net.tcp vazby webu, kterou jste přidali pro tuto ukázku.  
  
     V zájmu usnadnění práce následující dva kroky jsou implementovány v dávkovém souboru volá RemoveNetTcpSiteBinding.cmd nachází v adresáři ukázkové.  
  
    1.  Odebrání net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku na úrovni správce:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tento příkaz musí být zadán jako jeden řádek textu.  
  
    2.  Odeberte vazbu webu net.tcp spuštěním následujícího příkazu z příkazového řádku na úrovni správce:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz musí být zadán v jako jeden řádek textu.  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
