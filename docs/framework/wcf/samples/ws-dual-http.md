---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 4acf2491c242099f6c8b6c9c01dc18e9c99c9934
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589731"
---
# <a name="ws-dual-http"></a>WS Dual Http

Dvojitá ukázka HTTP ukazuje, jak nakonfigurovat `WSDualHttpBinding` vazbu. Tato ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS). Služba implementuje oboustranný kontrakt. Kontrakt je definován `ICalculatorDuplex` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení). V této ukázce `ICalculatorDuplex` rozhraní umožňuje klientovi provádět matematické operace, které vypočítávají výsledek spuštění přes relaci. Nezávisle služba vrátí výsledky na `ICalculatorDuplexCallback` rozhraní. Duplexní smlouva vyžaduje relaci, protože je nutné vytvořit kontext, který bude korelovat sadu zpráv odesílaných mezi klientem a službou. `WSDualHttpBinding`Vazba podporuje duplexní komunikaci.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

Chcete-li nakonfigurovat koncový bod služby pomocí `WSDualHttpBinding` , zadejte vazbu v konfiguraci koncového bodu, jak je znázorněno na obrázku.

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

2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

3. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

    > [!IMPORTANT]
    > Při spuštění klienta nástroje v konfiguraci mezi počítači, je nutné nahradit localhost v obou `address` atributech [ \<endpoint> \<client> ](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu a `clientBaseAddress` atribut [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) elementu názvem příslušného počítače, jak je znázorněno níže:

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
