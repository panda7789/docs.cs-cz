---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: bc8958ab092f97e94a75bc366d576441c1a5bbbd
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424545"
---
# <a name="ws-dual-http"></a>WS Dual Http

Dvojitá ukázka HTTP ukazuje, jak nakonfigurovat vazbu `WSDualHttpBinding`. Tato ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS). Služba implementuje oboustranný kontrakt. Kontrakt je definován rozhraním `ICalculatorDuplex`, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení). V této ukázce rozhraní `ICalculatorDuplex` umožňuje klientovi provádět matematické operace, které vypočítávají výsledek spuštění přes relaci. Nezávisle služba vrátí výsledky v rozhraní `ICalculatorDuplexCallback`. Duplexní smlouva vyžaduje relaci, protože je nutné vytvořit kontext, který bude korelovat sadu zpráv odesílaných mezi klientem a službou. Vazba `WSDualHttpBinding` podporuje duplexní komunikaci.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

Pokud chcete nakonfigurovat koncový bod služby s `WSDualHttpBinding`, zadejte vazbu v konfiguraci koncového bodu, jak je znázorněno na obrázku.

```xml
<endpoint address=""
         binding="wsDualHttpBinding"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
```

Na straně klienta je nutné nakonfigurovat adresu, kterou může server používat pro připojení ke klientovi, jak je znázorněno v následující ukázkové konfiguraci.

```xml
<system.serviceModel>
  <client>
    <endpoint address=
         "http://localhost/servicemodelsamples/service.svc"
         binding="wsDualHttpBinding"
         bindingConfiguration="Binding1"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
  </client>

  <bindings>
    <!-- Configure a WSDualHttpBinding that supports duplex -->
    <!-- communication. -->
    <wsDualHttpBinding>
      <binding name="Binding1"
               clientBaseAddress="http://localhost:8000/myClient/"
               useDefaultWebProxy="true"
               bypassProxyOnLocal="false">
      </binding>
    </wsDualHttpBinding>
  </bindings>
</system.serviceModel>
```

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```console
Press <ENTER> to terminate client once the output is displayed.

Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

Při spuštění ukázky se zobrazí zprávy vracené klientovi do rozhraní zpětného volání odeslaného ze služby. Po dokončení všech operací se zobrazí každý mezilehlé výsledek následovaný celým vzorcem. Pro vypnutí klienta stiskněte klávesu ENTER.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

    > [!IMPORTANT]
    > Pokud spouštíte klienta v konfiguraci mezi počítači, nezapomeňte nahradit localhost v atributu `address` [\<koncového bodu > \<elementu klienta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) a `clientBaseAddress` atributu\<[vazby](../../../../docs/framework/misc/binding.md) > prvek prvku [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) s názvem příslušného počítače, jak je znázorněno v následujícím příkladu:

    ```xml
    <client>
        <endpoint name = ""
          address=
         "http://service_machine_name/servicemodelsamples/service.svc"
        />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress=
            "http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```
