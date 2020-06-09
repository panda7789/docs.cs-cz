---
title: Nestálá komunikace ve frontě
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: a9f7e8a96fd293c7f87cc19846a42a42f28de288
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602336"
---
# <a name="volatile-queued-communication"></a>Nestálá komunikace ve frontě

Tato ukázka předvádí, jak provést nestálou komunikaci ve frontě prostřednictvím přenosu služby Řízení front zpráv (MSMQ). Tato ukázka používá <xref:System.ServiceModel.NetMsmqBinding> . Tato služba je v tomto případě samoobslužná Konzolová aplikace, která vám umožní sledovat službu přijímající zprávy ve frontě.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

V komunikaci ve frontě klient komunikuje se službou pomocí fronty. Klient přesněji odesílá zprávy do fronty. Služba přijímá zprávy z fronty. Službu a klient proto nemusí běžet současně, aby bylo možné komunikovat pomocí fronty.

Když odešlete zprávu bez jakýchkoli ujištění, služba MSMQ bude k dispozici jenom k tomu, aby se tato zpráva dostala na rozdíl od přesně po ujištění, že služba MSMQ zajišťuje doručení zprávy, nebo pokud nemůže být doručena, a oznamuje, že zprávu nelze doručit.

V některých scénářích můžete chtít poslat nestálou zprávu bez jakýchkoli zárukou v rámci fronty, pokud je včasné doručování důležitější než ztráty zpráv. Nestálé zprávy neobsahují chyby Správce fronty. Proto pokud správce front dojde k chybě, netransakční fronta používaná k ukládání netransakčních zpráv se zachovají, ale zprávy samotné neobsahují, protože zprávy nejsou uloženy na disku.

> [!NOTE]
> Nemůžete posílat nestálé zprávy bez zárukou v rámci rozsahu transakce pomocí služby MSMQ. Je také nutné vytvořit netransakční frontu pro odesílání nestálých zpráv.

Kontrakt služby v této ukázce je `IStockTicker` definující jednosměrné služby, které jsou nejvhodnější pro použití s řazením do fronty.

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

Operace služby zobrazuje burzovní symbol a cenu, jak je znázorněno v následujícím ukázkovém kódu:

```csharp
public class StockTickerService : IStockTicker
{
    public void StockTick(string symbol, float price)
    {
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);
     }
     …
}
```

Služba je hostována svým hostitelem. Při použití přenosu služby MSMQ musí být použitá fronta předem vytvořená. To lze provést ručně nebo prostřednictvím kódu. V této ukázce služba obsahuje kód pro kontrolu existence fronty a v případě potřeby ji vytvoří. Název fronty se načte z konfiguračního souboru. Základní adresa je používána [nástrojem Svcutil. exe](../servicemodel-metadata-utility-tool-svcutil-exe.md) pro vygenerování proxy serveru pro službu.

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get MSMQ queue name from app settings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName);

    // Create a ServiceHost for the StockTickerService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shutdown the service.
        serviceHost.Close();
    }
}
```

Název fronty MSMQ je zadán v oddílu appSettings konfiguračního souboru. Koncový bod pro službu je definován v oddílu System. serviceModel konfiguračního souboru a určuje `netMsmqBinding` vazbu.

> [!NOTE]
> Název fronty používá tečku (.) pro místní počítač a oddělovače zpětného lomítka v cestě při vytváření fronty pomocí <xref:System.Messaging> . Adresa koncového bodu služby Windows Communication Foundation (WCF) určuje položku NET. MSMQ: schéma, pro místní počítač a lomítka v cestě používá localhost.

V konfiguraci jsou uvedeny také záruky a odolnost proti nestálosti zpráv.

```xml
<appSettings>
  <!-- use appSetting to configure MSMQ queue name -->
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />
</appSettings>

<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"
             behaviorConfiguration="CalculatorServiceBehavior">
    ...
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                binding="netMsmqBinding"
                bindingConfiguration="volatileBinding"
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />
    ...
    </service>
  </services>

  <bindings>
    <netMsmqBinding>
      <binding name="volatileBinding"
             durable="false"
           exactlyOnce="false"/>
    </netMsmqBinding>
  </bindings>
  ...
</system.serviceModel>
```

Vzhledem k tomu, že ukázka odesílá zprávy ve frontě pomocí netransakční fronty, nelze odeslat transakční zprávy do fronty.

```csharp
// Create a client.
Random r = new Random(137);

StockTickerClient client = new StockTickerClient();

float price = 43.23F;
for (int i = 0; i < 10; i++)
{
    float increment = 0.01f * (r.Next(10));
    client.StockTick("zzz" + i, price + increment);
}

//Closing the client gracefully cleans up resources.
client.Close();
```

Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta. Můžete vidět, že služba přijímá zprávy z klienta. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta. Počítejte s tím, že protože se používá služba zařazování do fronty, klient a služba nemusí být spuštěny ve stejnou dobu. Můžete spustit klienta, vypnout ho a pak spustit službu a nadále přijímat zprávy.

```console
The service is ready.
Press <ENTER> to terminate service.

Stock Tick zzz0:43.25
Stock Tick zzz1:43.23
Stock Tick zzz2:43.28
Stock Tick zzz3:43.3
Stock Tick zzz4:43.23
Stock Tick zzz5:43.25
Stock Tick zzz6:43.25
Stock Tick zzz7:43.24
Stock Tick zzz8:43.32
Stock Tick zzz9:43.3
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

Ve výchozím nastavení <xref:System.ServiceModel.NetMsmqBinding> je zapnuto zabezpečení přenosu. Existují dvě vlastnosti pro zabezpečení přenosu ve službě MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` ve výchozím nastavení je režim ověřování nastaven na hodnotu `Windows` a úroveň ochrany je nastavena na hodnotu `Sign` . Aby služba MSMQ poskytovala funkci ověřování a podepisování, musí být součástí domény a musí být nainstalovaná možnost integrace služby Active Directory pro službu MSMQ. Pokud tuto ukázku spustíte na počítači, který nesplňuje tato kritéria, zobrazí se chyba.

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Spuštění ukázky na počítači připojeném k pracovní skupině nebo bez integrace služby Active Directory

1. Pokud počítač není součástí domény nebo nemáte nainstalovanou integraci služby Active Directory, vypněte zabezpečení přenosu nastavením režimu ověřování a úrovně ochrany tak, `None` jak je znázorněno v následujícím ukázkovém kódu konfigurace:

    ```xml
    <system.serviceModel>
        <services>
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"
                   behaviorConfiguration="StockTickerServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>

            <!-- Define NetMsmqEndpoint -->
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                      binding="netMsmqBinding"
                      bindingConfiguration="volatileBinding"
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />

          </service>
        </services>

        <bindings>
          <netMsmqBinding>
            <binding name="volatileBinding"
                  durable="false"
                  exactlyOnce="false">
              <security mode="None" />
            </binding>
          </netMsmqBinding>
        </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="StockTickerServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. Před spuštěním ukázky se ujistěte, že jste změnili konfiguraci na serveru i v klientovi.

    > [!NOTE]
    > Nastavení `security mode` na `None` je ekvivalentní nastavení <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> a `Message` zabezpečení na `None` .

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`
