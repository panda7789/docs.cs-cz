---
title: Ukázka Začínáme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: 74c3b825bbd51a082f20e8e2009e1ca5f0b35100
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837150"
---
# <a name="getting-started-sample"></a>Ukázka Začínáme
Ukázka Začínáme ukazuje, jak implementovat typické služby a typické klienta pomocí Windows Communication Foundation (WCF). Tato ukázka představuje základ pro všechny další ukázky základní technologii.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 Služba popisuje operace, které provádí v kontraktu služby, který veřejně zpřístupní jako metadata. Služba také obsahuje kód k provedení operace.  
  
 Klient obsahuje definici kontraktu služby a proxy třídu pro přístup k službě. Proxy kód je generován z metadat služby pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)], služba je hostována v aktivace služby Windows (WAS). Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], je hostované v Internetové informační služby (IIS) a technologie ASP.NET. Hostování služby IIS nebo WAS umožňuje službě automaticky aktivuje při prvním přístupu.  
  
> [!NOTE]
>  Pokud chcete začít pracovat s pomocí ukázky, který hostuje službu v konzolové aplikaci, místo služby IIS, najdete v článku [hostování na vlastním serveru](../../../../docs/framework/wcf/samples/self-host.md) vzorku.  
  
 Klienta a služby v souboru nastavení konfigurace, které poskytují flexibilitu v době nasazování zadat podrobnosti o přístup. To zahrnuje definice koncového bodu, který určuje adresu, vazba a kontrakt. Vazbu určuje přenos a zabezpečení podrobnosti o tom, jak tato služba je přístup k.  
  
 Nakonfiguruje službu běhové chování publikování metadat.  
  
 Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď. Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení). Klient podá požadavky a odpovědi služby s výsledkem dané matematické operace. Implementuje služby `ICalculator` kontrakt, který je definován v následujícím kódu.  
  
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
  
 Služba zpřístupňuje koncový bod pro komunikaci se službou, definované pomocí konfiguračního souboru konfigurace (Web.config), jak je znázorněno v následující ukázka.  
  
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
  
 Služba zpřístupňuje koncový bod na základní adrese poskytované hostitelem služby IIS nebo WAS. Je vazba konfigurována se standardní <xref:System.ServiceModel.WSHttpBinding>, která poskytuje komunikaci pomocí protokolu HTTP a standardní protokoly webové služby pro adresování a zabezpečení. Smlouva je `ICalculator` službou implementována.  
  
 Podle konfigurace, služba může získat přístup na adrese `http://localhost/servicemodelsamples/service.svc` klientem na stejném počítači. Pro klienty ve vzdálených počítačích pro přístup ke službě musí se zadat název plně kvalifikované domény místo localhost.  
  
 Ve výchozím nastavení nevystavuje rozhraní metadat. V důsledku toho služba Zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> a zpřístupňuje koncový bod metadat exchange (MEX) na `http://localhost/servicemodelsamples/service.svc/mex`. Následující konfigurace ukazuje to.  
  
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
  
 Klient komunikuje, používat typ daný kontrakt pomocí třídy klienta, který je generován [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Tento vygenerovaný client je součástí souboru generatedClient.cs nebo generatedClient.vb. Tento nástroj načte metadata pro určitou službu a generuje klienta pro použití tak, že klientská aplikace na komunikaci pomocí typu dané smlouvy. Hostovaná služba musí být k dispozici pro generování kódu klienta, protože služba se používá k načtení aktualizovanými metadaty.  
  
 Spusťte následující příkaz z příkazového řádku sady SDK v adresáři klienta ke generování typové proxy:  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 Ke generování klienta v jazyce Visual Basic zadejte následující z příkazového řádku sady SDK:  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 Pomocí generovaného klienta má klient přístup konfigurací uvedenou příslušnou adresu a vazbu koncového bodu dané služby. Stejně jako služby Klient použije konfigurační soubor (App.config) zadat koncový bod, pomocí kterého chce komunikovat. Konfigurace koncového bodu klienta se skládá z absolutní adresu pro koncový bod služby, vazba a kontrakt, jak je znázorněno v následujícím příkladu.  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 Implementace klienta vytvoří instanci klienta a pomocí typu rozhraní zahájit komunikaci se službou, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Začínáme se službou příklad ukazuje standardní způsob, jak vytvořit klienta a služby. Druhý [základní](../../../../docs/framework/wcf/samples/basic-sample.md) pracovat s tímto příkladem k předvedení funkcí konkrétního produktu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Postupy: Hostování služby WCF v IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
