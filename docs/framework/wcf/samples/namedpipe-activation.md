---
title: Aktivace pojmenovaného kanálu
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: a7d940d6be56160945ca0f8697361314af96bc0b
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487542"
---
# <a name="namedpipe-activation"></a>Aktivace pojmenovaného kanálu

V této ukázce hostování služba, která se používá k aktivaci služby, která komunikuje přes názvy kanálů Windows Process Activation Service (WAS). Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a vyžaduje [!INCLUDE[wv](../../../../includes/wv-md.md)] ke spuštění.

> [!NOTE]
> Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a>Ukázka podrobnosti

Ukázka se skládá z programu konzoly klienta (.exe) a služby knihovny (.dll) hostované v pracovním procesu aktivaci služby Aktivace procesu (WAS) Windows. Činnost klienta je vidět v okně konzoly.

Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (přidat, odečítání, násobení a rozdělit), jak je znázorněno v následujícím ukázkovém kódu.

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

Klient podá synchronní žádosti dané matematické operace a implementaci služby vypočítá a vrátí odpovídající výsledek.

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

Ukázka používá upravené `netNamedPipeBinding` vazby se zabezpečení. Vazba je zadán v konfiguračních souborech pro klienta a služby. Typ vazby služby je zadaný v elementu koncového bodu `binding` atributu, jak je znázorněno v následující ukázková konfigurace.

Pokud chcete použít vazbu zabezpečené pojmenovaný kanál, změňte režim zabezpečení serveru na požadované nastavení a znovu spusťte svcutil.exe na straně klienta k získání konfiguračního souboru aktualizovaného klienta.

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

Informace o koncovém bodu klienta je nakonfigurován, jak je znázorněno v následujícím ukázkovém kódu.

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

Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1. Ujistěte se, že služba IIS 7.0 je nainstalována. Služba IIS 7.0 je vyžadováno pro aktivaci WAS.

2. Ujistěte se dá provést [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

    Kromě toho je třeba nainstalovat jiným protokolem než HTTP aktivačních komponent WCF:

    1. Z **Start** nabídce zvolte **ovládací panely**.

    2. Vyberte **programy a funkce**.

    3. Klikněte na tlačítko **součásti Windows zapnout nebo vypnout**.

    4. Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontrolu **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.

3. Konfigurace Windows WAS Process Activation Service () pro podporu aktivace pojmenovaného kanálu.

    V zájmu usnadnění práce následující dva kroky jsou implementovány v dávkovém souboru volá AddNetPipeSiteBinding.cmd nachází v adresáři ukázkové.

    1. Kvůli podpoře aktivace net.pipe, musíte ji nejdřív svázat výchozí webový server se protokol net.pipe. To lze provést pomocí appcmd.exe, která se instaluje s sada nástrojů pro správu služby IIS 7.0. Z příkazového řádku se zvýšenými oprávněními (správce) spusťte následující příkaz.

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > Tento příkaz je jeden řádek textu.

        Tento příkaz přidá vazbu webu net.pipe výchozí webový server.

    2. Přestože všechny aplikace v rámci lokality sdílejí společné net.pipe vazby, každá aplikace můžete povolit podporu net.pipe jednotlivě. Pokud chcete povolit net.pipe /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku se zvýšenými oprávněními.

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > Tento příkaz je jeden řádek textu.

        Tento příkaz umožňuje aplikaci /servicemodelsamples přistupovat pomocí obou `http://localhost/servicemodelsamples` a `net.tcp://localhost/servicemodelsamples`.

4. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

5. Odeberte net.pipe vazby webu, kterou jste přidali pro tuto ukázku.

    V zájmu usnadnění práce následující dva kroky jsou implementovány v dávkovém souboru volá RemoveNetPipeSiteBinding.cmd nachází v adresáři ukázkové:

    1. Odeberte net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > Tento příkaz musí být zadán jako jeden řádek textu.

    2. Odeberte vazbu webu net.tcp spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > Tento příkaz musí být zadán v jako jeden řádek textu.

## <a name="see-also"></a>Viz také:

- [Hostování AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
