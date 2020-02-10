---
title: Aktivace protokolem TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 3487d84a63b2838dc1b55fdf3f41b410fcfc2e63
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094875"
---
# <a name="tcp-activation"></a>Aktivace protokolem TCP

Tato ukázka demonstruje hostování služby, která používá aktivační služby procesů systému Windows (WAS) k aktivaci služby, která komunikuje přes protokol net. TCP. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

Ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované v pracovním procesu aktivovaném nástrojem WAS. Aktivita klienta se zobrazí v okně konzoly.

Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován rozhraním `ICalculator`, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení), jak je znázorněno v následujícím ukázkovém kódu:

```csharp
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

Implementace služby vypočítá a vrátí příslušný výsledek:

```csharp
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

Ukázka používá variantu připojení NET. TCP se zapnutým sdílením portů TCP a vypnuté zabezpečení. Pokud chcete použít zabezpečenou vazbu TCP, změňte režim zabezpečení serveru na požadované nastavení a znovu spusťte Svcutil. exe na straně klienta, čímž vygenerujete konfigurační soubor klienta aktualizace.

Následující příklad ukazuje konfiguraci služby:

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
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

Koncový bod klienta je nakonfigurován tak, jak je znázorněno v následujícím ukázkovém kódu:

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

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že je nainstalovaná služba IIS 7,0. Pro aktivaci byla požadována služba IIS 7,0.

2. Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

    Kromě toho musíte nainstalovat komponenty WCF, které nejsou součástí aktivace přes protokol HTTP:

    1. V nabídce **Start** klikněte na položku **Ovládací panely**.

    2. Vyberte **programy a funkce**.

    3. Klikněte na **zapnout nebo vypnout součásti systému Windows**.

    4. Rozbalte uzel **Microsoft .NET Framework 3,0** a podívejte se na funkci **Windows Communication Foundation aktivace jiným protokolem než http** .

3. Při konfiguraci byla podpora aktivace protokolem TCP podporována.

    Následující dva kroky jsou implementovány v dávkovém souboru s názvem AddNetTcpSiteBinding. cmd, který je umístěn v ukázkovém adresáři.

    1. Aby bylo možné podporovat NET. TCP Activation, musí být výchozí webová stránka nejprve svázána s portem NET. TCP. To lze provést pomocí nástroje Appcmd. exe, který je nainstalován se sadou nástrojů pro správu Internetová informační služba 7,0 (IIS). Na příkazovém řádku na úrovni správce spusťte následující příkaz:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > Tento příkaz je jedním řádkem textu. Tento příkaz přidá vazbu sítě NET. TCP na výchozí webovou stránku, která naslouchá na portu TCP 808 s libovolným názvem hostitele.

    2. I když všechny aplikace v rámci lokality sdílí společnou vazbu NET. TCP, každá aplikace může povolit podporu NET. TCP samostatně. Pokud chcete povolit NET. TCP pro aplikaci/ServiceModelSamples, spusťte následující příkaz z příkazového řádku na úrovni správce:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu. Tento příkaz umožňuje, aby aplikace/ServiceModelSamples byla dostupná pomocí `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples`.

4. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

5. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

    Odeberte vazbu na lokalitu NET. TCP, kterou jste přidali pro tuto ukázku.

    Následující dva kroky jsou implementovány v dávkovém souboru s názvem RemoveNetTcpSiteBinding. cmd, který je umístěn v ukázkovém adresáři.

    1. Ze seznamu povolených protokolů odeberte NET. TCP spuštěním následujícího příkazu z příkazového řádku na úrovni správce:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > Tento příkaz musí být zadán jako jeden řádek textu.

    2. Odeberte vazbu sítě NET. TCP spuštěním následujícího příkazu z příkazového řádku na úrovni správce:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > Tento příkaz musí být zadán jako jeden řádek textu.

## <a name="see-also"></a>Viz také

- [Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
