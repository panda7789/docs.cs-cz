---
title: "Ukázka Začínáme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
caps.latest.revision: "60"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f97ad418f3d5ed197e8c35edf9e897eb393ef18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-sample"></a>Ukázka Začínáme
Ukázka Začínáme ukazuje, jak implementovat typické služby a typické klienta pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Tato ukázka je základem pro všechny ostatní vzorky základní technologie.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 Služba popisuje operace, které provádí v kontraktu služby, který zveřejňuje veřejně jako metadata. Služba také obsahuje kód k provedení operace.  
  
 Klient obsahuje definici kontraktu služby a třídu proxy pro přístup k službě. Generování kódu proxy z metadat služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)], služba je hostovaná v aktivační služby systému Windows (WAS). Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], se hostuje na Internetové informační služby (IIS) a ASP.NET. Hostování služby ve službě IIS nebo WAS umožňuje službě automaticky aktivovat při prvním přístupu.  
  
> [!NOTE]
>  Pokud chcete začít pracovat s vzorku, který hostuje službu v konzolové aplikaci, místo služby IIS najdete v tématu [hostování na vlastním](../../../../docs/framework/wcf/samples/self-host.md) ukázka.  
  
 Služba a klient zadejte podrobnosti přístupu v souboru nastavení konfigurace, které poskytují flexibilitu v době nasazení. To zahrnuje definici koncového bodu, které určuje adresy, vazby a kontrakt. Vazba určuje přenos a zabezpečení podrobnosti jak služba je přístupná.  
  
 Nakonfiguruje službu běhového chování publikování metadat.  
  
 Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobit a dělit). Klient podá požadavky a odpovědi služby s výsledkem dané matematické operace. Implementuje služby `ICalculator` kontrakt, který je definován v následujícím kódu.  
  
```vb  
' Define a service contract.  
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>  
     Public Interface ICalculator  
        <OperationContract()>  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
```  
  
```csharp  
// Define a service contract.  
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
  
 Implementace služby vypočítá a vrátí odpovídající výsledek, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
' Service class which implements the service contract.  
Public Class CalculatorService  
Implements ICalculator  
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
Return n1 + n2  
End Function  
  
Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
Return n1 - n2  
End Function  
  
Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
Return n1 * n2  
End Function  
  
Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
Return n1 / n2  
End Function  
End Class  
```  
  
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
  
 Službu zpřístupní koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru aplikace (Web.config), jak je znázorněno v následující ukázková konfigurace.  
  
```xaml  
<services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- ICalculator is exposed at the base address provided by  
         host: http://localhost/servicemodelsamples/service.svc.  -->  
       <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
       ...  
    </service>  
</services>  
```  
  
 Službu zpřístupní koncový bod na základní adrese od hostitele služby IIS nebo WAS. Vazba je nakonfigurována s standardní <xref:System.ServiceModel.WSHttpBinding>, který poskytuje komunikaci pomocí protokolu HTTP a standardní protokoly webové služby pro adresování a zabezpečení. Smlouva je `ICalculator` implementované službu.  
  
 Podle konfigurace, služba je přístupná na http://localhost/servicemodelsamples/service.svc klientem na stejném počítači. Pro klienty na computersto vzdálený přístup službu musí zadat název plně kvalifikované domény místo localhost.  
  
 Rozhraní framework nevystavuje metadata ve výchozím nastavení. Jako takový službu Zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> a zpřístupní koncový bod metadat exchange (MEX) v http://localhost/servicemodelsamples/service.svc/mex. Následující konfigurace ukazuje to.  
  
```xaml  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- the mex endpoint is explosed at  
       http://localhost/servicemodelsamples/service.svc/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults  
   attribute to true-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Klient komunikuje pomocí danou zakázku typu pomocí třídy klienta, který je generovaný [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Tato generovaného klienta je obsažený v souboru generatedClient.cs nebo generatedClient.vb. Tento nástroj načte metadata pro danou službu a vygeneruje klienta pro použití klientskou aplikací pro komunikaci pomocí typu danou zakázku. Hostovaná služba musí být k dispozici pro generování kódu klienta, protože služba se používá k načtení aktualizované metadata.  
  
 Spusťte následující příkaz z příkazového řádku sady SDK v adresáři klienta ke generování typové proxy server:  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 Ke generování klienta v jazyce Visual Basic typu následující z příkazového řádku SDK:  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 Pomocí generovaného klienta, klient může získat koncový bod uvedená služba nakonfigurováním příslušnou adresu a vazby. Jako službu Klient použije konfigurační soubor (App.config) k určení koncový bod, pomocí kterého chce komunikovat. Konfigurace klienta koncový bod se skládá z absolutní adresu pro koncový bod služby, vazby a kontrakt, jak je znázorněno v následujícím příkladu.  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 Implementace klienta vytvoří klienta a používá rozhraní typové zahájíte komunikaci se službou, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
' Create a client  
Dim client As New CalculatorClient()  
  
' Call the Add service operation.  
            Dim value1 = 100.0R  
            Dim value2 = 15.99R  
            Dim result = client.Add(value1, value2)  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
' Call the Subtract service operation.  
value1 = 145.00R  
value2 = 76.54R  
result = client.Subtract(value1, value2)  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
' Call the Multiply service operation.  
value1 = 9.00R  
value2 = 81.25R  
result = client.Multiply(value1, value2)  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
' Call the Divide service operation.  
value1 = 22.00R  
value2 = 7.00R  
result = client.Divide(value1, value2)  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
'Closing the client gracefully closes the connection and cleans up resources  
```  
  
```csharp  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
// Call the Subtract service operation.  
value1 = 145.00D;  
value2 = 76.54D;  
result = client.Subtract(value1, value2);  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
// Call the Multiply service operation.  
value1 = 9.00D;  
value2 = 81.25D;  
result = client.Multiply(value1, value2);  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
// Call the Divide service operation.  
value1 = 22.00D;  
value2 = 7.00D;  
result = client.Divide(value1, value2);  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
//Closing the client releases all communication resources.  
client.Close();  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Ukázka Začínáme ukazuje standardní způsob, jak vytvořit klienta a služby. Druhá [základní](../../../../docs/framework/wcf/samples/basic-sample.md) pracovat s tímto příkladem k předvedení funkcí určitý produkt.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Postupy: Hostování služby WCF v IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
