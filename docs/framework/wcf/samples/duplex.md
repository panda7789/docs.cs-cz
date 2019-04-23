---
title: Duplex
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 1dedc6d771e75acd0d657bb5430c178428c0f0ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976700"
---
# <a name="duplex"></a>Duplex
Duplexní ukázka ukazuje, jak definovat a implementovat duplexního kontraktu. Duplexní komunikaci nastane, pokud klient vytvoří relaci se službou a poskytuje službu na kanál, na kterém služba odesílat zprávy o zpět do klienta. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Duplexní kontrakt je definován jako dvojici rozhraní – primární rozhraní z klienta do služby a rozhraní zpětného volání ze služby ke klientovi. V této ukázce `ICalculatorDuplex` rozhraní umožňuje klientovi k provádění matematických operací výpočtu výsledku přes relaci. Služba vrátí výsledky v `ICalculatorDuplexCallback` rozhraní. Duplexní kontrakt vyžaduje relaci, protože kontextu musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službou.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS). Duplexní kontrakt je definovaná následujícím způsobem:  
  
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
  
 `CalculatorService` Třída implementuje primární `ICalculatorDuplex` rozhraní. Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režimu instance udržovat výsledek pro každou relaci. Soukromá vlastnost s názvem `Callback` slouží k přístupu k zpětného volání kanálu ke klientovi. Služba používá zpětné volání pro odesílání zpráv zpět do klienta prostřednictvím rozhraní zpětného volání.  
  
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
  
 Klient musí poskytnout třídu, která implementuje rozhraní zpětného volání duplexní kontrakt pro příjem zpráv ze služby. V ukázce `CallbackHandler` třída je definována pro implementaci `ICalculatorDuplexCallback` rozhraní.  
  
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
  
 Proxy server, který je vygenerován pro duplexní kontrakt vyžaduje <xref:System.ServiceModel.InstanceContext> poskytované při konstrukci. To <xref:System.ServiceModel.InstanceContext> se používá jako web pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy odeslané ze služby. <xref:System.ServiceModel.InstanceContext> Je vytvořený pomocí instance `CallbackHandler` třídy. Tento objekt zpracovává zprávy odeslané do klienta v rozhraní zpětného volání ze služby.  
  
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
  
 Konfigurace se změnila má být poskytnuta vazba, která podporuje komunikace relace a duplexní komunikaci. `wsDualHttpBinding` Podporuje komunikaci relace a umožňuje duplexní komunikaci poskytnutím duální připojení pomocí protokolu HTTP, jeden pro každý směr. Ve službě je jediným rozdílem v konfiguraci vazby, který se používá. Na straně klienta je nutné nakonfigurovat adresu serveru můžete použít pro připojení ke klientovi, jak je znázorněno v následující ukázková konfigurace.  
  
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
  
 Když spustíte ukázku, uvidíte zprávy, které jsou vráceny do klienta na rozhraní zpětného volání, která je odeslána ze služby. Zobrazí se každý přechodný výsledek, za nímž následuje celou rovnici. Po dokončení všech operací. Stiskněte klávesu ENTER pro vypnutí klient.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!IMPORTANT]
    >  Při spuštění klienta v konfiguraci mezi počítači, nezapomeňte nahradit "localhost" v obou `address` atribut [ \<koncový bod > z \<klienta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu a `clientBaseAddress` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element s názvem příslušný počítač, jak je znázorněno v následující:  
  
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
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
