---
title: Duplex
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 64036a1314bc3f60023cdc555fa1eaece7c687c8
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715148"
---
# <a name="duplex"></a>Duplex

Duplexní Ukázka ukazuje, jak definovat a implementovat duplexní kontrakt. Duplexní komunikace probíhá, když klient vytvoří relaci se službou a poskytne službě kanál, na kterém může služba odesílat zprávy zpátky klientovi. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Duplexní kontrakt je definován jako dvojice rozhraní – primární rozhraní od klienta ke službě a rozhraní zpětného volání od služby ke klientovi. V této ukázce rozhraní `ICalculatorDuplex` umožňuje klientovi provádět matematické operace a vypočítat výsledek v relaci. Služba vrátí výsledky v rozhraní `ICalculatorDuplexCallback`. Duplexní smlouva vyžaduje relaci, protože je nutné vytvořit kontext, který bude korelovat sadu zpráv odesílaných mezi klientem a službou.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS). Duplexní smlouva je definována takto:

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,
                 CallbackContract=typeof(ICalculatorDuplexCallback))]
public interface ICalculatorDuplex
{
    [OperationContract(IsOneWay = true)]
    void Clear();
    [OperationContract(IsOneWay = true)]
    void AddTo(double n);
    [OperationContract(IsOneWay = true)]
    void SubtractFrom(double n);
    [OperationContract(IsOneWay = true)]
    void MultiplyBy(double n);
    [OperationContract(IsOneWay = true)]
    void DivideBy(double n);
}

public interface ICalculatorDuplexCallback
{
    [OperationContract(IsOneWay = true)]
    void Result(double result);
    [OperationContract(IsOneWay = true)]
    void Equation(string eqn);
}
```

Třída `CalculatorService` implementuje primární rozhraní `ICalculatorDuplex`. Služba využívá režim instance <xref:System.ServiceModel.InstanceContextMode.PerSession> k uchování výsledku pro každou relaci. Privátní vlastnost s názvem `Callback` se používá pro přístup k kanálu zpětného volání ke klientovi. Služba používá zpětné volání pro posílání zpráv zpátky do klienta prostřednictvím rozhraní zpětného volání.

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorDuplex
{
    double result = 0.0D;
    string equation;

    public CalculatorService()
    {
        equation = result.ToString();
    }

    public void Clear()
    {
        Callback.Equation($"{equation} = {result}");
        equation = result.ToString();
    }

    public void AddTo(double n)
    {
        result += n;
        equation += $" + {n}";
        Callback.Result(result);
    }

    //...

    ICalculatorDuplexCallback Callback
    {
        get
        {
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();
        }
    }
}
```

Klient musí poskytnout třídu, která implementuje rozhraní zpětného volání pro oboustrannou smlouvu pro příjem zpráv ze služby. V ukázce je `CallbackHandler` třída definována pro implementaci rozhraní `ICalculatorDuplexCallback`.

```csharp
public class CallbackHandler : ICalculatorDuplexCallback
{
   public void Result(double result)
   {
      Console.WriteLine("Result({0})", result);
   }

   public void Equation(string equation)
   {
      Console.WriteLine("Equation({0}", equation);
   }
}
```

Proxy, který je generován pro duplexní smlouvu, vyžaduje, aby při konstrukci byl poskytnut <xref:System.ServiceModel.InstanceContext>. Tato <xref:System.ServiceModel.InstanceContext> slouží jako web pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy odesílané zpět ze služby. <xref:System.ServiceModel.InstanceContext> je vytvořen s instancí třídy `CallbackHandler`. Tento objekt zpracovává zprávy odesílané ze služby klientovi na rozhraní zpětného volání.

```csharp
// Construct InstanceContext to handle messages on callback interface.
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());

// Create a client.
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);

Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");
Console.WriteLine();

// Call the AddTo service operation.
double value = 100.00D;
client.AddTo(value);

// Call the SubtractFrom service operation.
value = 50.00D;
client.SubtractFrom(value);

// Call the MultiplyBy service operation.
value = 17.65D;
client.MultiplyBy(value);

// Call the DivideBy service operation.
value = 2.00D;
client.DivideBy(value);

// Complete equation.
client.Clear();

Console.ReadLine();

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();
```

Konfigurace byla změněna tak, aby poskytovala vazbu, která podporuje komunikaci relace i duplexní komunikaci. `wsDualHttpBinding` podporuje komunikaci relací a umožňuje duplexní komunikaci tím, že poskytuje duální připojení HTTP, jedno pro každý směr. V rámci služby je jediným rozdílem v konfiguraci použití vazby. Na straně klienta je nutné nakonfigurovat adresu, kterou může server používat pro připojení ke klientovi, jak je znázorněno v následující ukázkové konfiguraci.

```xml
<client>
  <endpoint name=""
            address="http://localhost/servicemodelsamples/service.svc"
            binding="wsDualHttpBinding"
            bindingConfiguration="DuplexBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
</client>

<bindings>
  <!-- Configure a binding that support duplex communication. -->
  <wsDualHttpBinding>
    <binding name="DuplexBinding"
             clientBaseAddress="http://localhost:8000/myClient/">
    </binding>
  </wsDualHttpBinding>
</bindings>
```

Při spuštění ukázky se zobrazí zprávy vracené klientovi na rozhraní zpětného volání, které je odesláno ze služby. Po dokončení všech operací se zobrazí každý mezilehlé výsledek následovaný celým vzorcem. Pro vypnutí klienta stiskněte klávesu ENTER.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C#edici, C++nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

    > [!IMPORTANT]
    > Pokud spouštíte klienta v konfiguraci mezi počítači, nezapomeňte nahradit "localhost" v atributu `address` [\<koncového bodu > \<elementu klienta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) a atribut `clientBaseAddress`\<[vazby](../../configure-apps/file-schema/wcf/bindings.md) > elementu\<> [](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) elementu s názvem příslušného počítače, jak je znázorněno v následujícím příkladu:

    ```xml
    <client>
        <endpoint name = ""
        address="http://service_machine_name/servicemodelsamples/service.svc"
        ... />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
