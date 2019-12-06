---
title: Aktivace pojmenovaného kanálu
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: a562ec51d35af08f49e89b652670e9a57b0f00c2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837854"
---
# <a name="namedpipe-activation"></a>Aktivace pojmenovaného kanálu

Tato ukázka demonstruje hostování služby, která používá aktivační službu procesů systému Windows (WAS) k aktivaci služby, která komunikuje s kanály názvů. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a vyžaduje spuštění systému Windows Vista.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a>Podrobnosti ukázky

Ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované v pracovním procesu aktivovaném službami aktivace procesů systému Windows (WAS). Aktivita klienta se zobrazí v okně konzoly.

Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován rozhraním `ICalculator`, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení), jak je znázorněno v následujícím ukázkovém kódu.

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

Klient provádí synchronní požadavky na danou matematickou operaci a implementace služby vypočítá a vrátí příslušný výsledek.

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

Ukázka používá upravenou vazbu `netNamedPipeBinding` bez zabezpečení. Vazba je určena v konfiguračních souborech pro klienta a službu. Typ vazby pro službu je zadán v atributu `binding` elementu koncového bodu, jak je znázorněno v následující ukázkové konfiguraci.

Pokud chcete použít zabezpečenou vazbu pojmenovaného kanálu, změňte režim zabezpečení serveru na požadované nastavení zabezpečení a znovu spusťte Svcutil. exe v klientovi, aby se získal aktualizovaný konfigurační soubor klienta.

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
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

Informace o koncovém bodu klienta jsou konfigurovány tak, jak je znázorněno v následujícím ukázkovém kódu.

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

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

2. Ujistěte se, že jste v [Windows Communication Foundation Samples provedli postup jednorázového nastavení](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

    Kromě toho musíte nainstalovat komponenty WCF, které nejsou součástí aktivace přes protokol HTTP:

    1. V nabídce **Start** klikněte na položku **Ovládací panely**.

    2. Vyberte **programy a funkce**.

    3. Klikněte na **zapnout nebo vypnout součásti systému Windows**.

    4. Rozbalte uzel **Microsoft .NET Framework 3,0** a podívejte se na funkci **Windows Communication Foundation aktivace jiným protokolem než http** .

3. Nakonfigurujte aktivační službu procesů systému Windows (WAS) pro podporu aktivace pojmenovaného kanálu.

    Následující dva kroky jsou implementovány v dávkovém souboru s názvem AddNetPipeSiteBinding. cmd, který je umístěn v ukázkovém adresáři.

    1. Aby bylo možné podporovat aktivaci NET. Pipes, musí být výchozí webová stránka nejprve svázána s protokolem NET. pipe. To lze provést pomocí nástroje Appcmd. exe, který je nainstalován se sadou nástrojů pro správu služby IIS 7,0. Na příkazovém řádku se zvýšenými oprávněními (správce) spusťte následující příkaz.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu.

        Tento příkaz přidá vazbu lokality NET. pipe k výchozímu webovému serveru.

    2. I když všechny aplikace v rámci lokality sdílejí společnou vazbu NET. pipe, může každá aplikace povolit podporu NET. pipe jednotlivě. Pokud chcete povolit NET. pipe pro aplikaci/ServiceModelSamples, spusťte z příkazového řádku se zvýšenými oprávněními následující příkaz.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > Tento příkaz je jedním řádkem textu.

        Tento příkaz umožňuje, aby aplikace/ServiceModelSamples byla dostupná pomocí `http://localhost/servicemodelsamples` i `net.tcp://localhost/servicemodelsamples`.

4. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

5. Odeberte vazbu na lokalitu NET. pipe, kterou jste přidali pro tuto ukázku.

    Pro usnadnění jsou v dávkovém souboru s názvem RemoveNetPipeSiteBinding. cmd, který se nachází v ukázkovém adresáři, implementované tyto dva kroky:

    1. Ze seznamu povolených protokolů odeberte NET. TCP spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > Tento příkaz musí být zadán jako jeden řádek textu.

    2. Odeberte vazbu sítě NET. TCP spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > Tento příkaz musí být zadán jako jeden řádek textu.

## <a name="see-also"></a>Viz také:

- [Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
