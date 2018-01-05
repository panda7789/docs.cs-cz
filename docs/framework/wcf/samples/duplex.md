---
title: Duplex
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0baf0a188ccb67f50a57ea0a56bb16dc40c53bbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="duplex"></a>Duplex
Duplexní ukázka ukazuje, jak definovat a implementovat duplexního kontraktu. Duplexní komunikace nastane, když klient vytvoří relaci se službou a poskytuje služby kanál, na kterém služba mohou zasílat zprávy zpět do klienta. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Duplexní kontrakt je definován jako dvojice rozhraní – primární rozhraní z klienta pro službu a rozhraní pro zpětné volání ze služby do klienta. V této ukázce `ICalculatorDuplex` rozhraní, které umožňuje provádět matematické operace, výpočet výsledek přes relaci klienta. Služba vrátí výsledky na `ICalculatorDuplexCallback` rozhraní. Duplexní kontrakt vyžaduje relaci, protože kontextu musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službu.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS). Duplexní kontrakt je definován následujícím způsobem:  
  
```  
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
  
 `CalculatorService` Třída implementuje primární `ICalculatorDuplex` rozhraní. Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> instance režimu zachování výsledek pro každou relaci. Soukromá vlastnost s názvem `Callback` se používá pro přístup k kanál zpětného volání pro klienta. Služba používá zpětné volání pro odesílání zpráv zpět do klienta přes rozhraní zpětného volání.  
  
```  
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
        Callback.Equation(equation + " = " + result.ToString());  
        equation = result.ToString();  
    }  
  
    public void AddTo(double n)  
    {  
        result += n;  
        equation += " + " + n.ToString();  
        Callback.Result(result);  
    }  
    ...  
    ICalculatorDuplexCallback Callback  
    {  
        get  
        {  
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();  
        }  
    }  
}  
```  
  
 Klient musí poskytnout třídu, která implementuje rozhraní zpětné volání duplexního kontraktu pro příjem zpráv ze služby. V ukázce `CallbackHandler` třída definovaná implementovat `ICalculatorDuplexCallback` rozhraní.  
  
```  
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
  
 Proxy server, který se vygeneruje pro vyžaduje duplexního kontraktu <xref:System.ServiceModel.InstanceContext> při vytváření, musíte zadat. To <xref:System.ServiceModel.InstanceContext> slouží jako lokality pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy, které se odesílají zpět ze služby. <xref:System.ServiceModel.InstanceContext> Je vytvořený pomocí instance `CallbackHandler` třídy. Tento objekt zpracovává zprávy odeslané ze služby pro klienta v rozhraní zpětného volání.  
  
```  
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
  
 Má být poskytnuta vazba, která podporuje komunikaci relace a duplexní komunikace se změnila konfigurace. `wsDualHttpBinding` Podporuje komunikaci relace a umožňuje duplexní komunikace tím, že poskytuje duální připojení protokolu HTTP, jeden pro všechny směry. Ve službě je jediným rozdílem v konfiguraci vazby, který se používá. Na klientovi je nutné nakonfigurovat adresu, která server můžete použít pro připojení k klienta, jak je znázorněno v následující ukázka konfigurace.  
  
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
  
 Při spuštění vzorového uvidíte zprávy, které se vrátí klientovi v rozhraní zpětné volání, která je odeslána ze služby. Zobrazí se každý zprostředkující výsledek, za nímž následuje celý rovnice po dokončení všech operací. Stisknutím klávesy ENTER vypnout klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C#, C++ nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!IMPORTANT]
    >  Při spuštění klienta v počítači konfiguraci, nezapomeňte nahradit "localhost" v obou `address` atribut [koncový bod](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu a `clientBaseAddress` atribut [ \< Vazba >](../../../../docs/framework/misc/binding.md) element [ \<– wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element s názvem příslušný počítač, jak je uvedené v následující:  
  
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
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
  
## <a name="see-also"></a>Viz také
