---
title: Spolupráce s webovými službami ASMX
ms.date: 03/30/2017
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
ms.openlocfilehash: b5af8f15d38f730d2243c642d4623c0bc6e1343c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183590"
---
# <a name="interoperating-with-asmx-web-services"></a>Spolupráce s webovými službami ASMX
Tato ukázka ukazuje, jak integrovat klientskou aplikaci WCF (Windows Communication Foundation) s existující webovou službou ASMX.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka se skládá z programu klientské konzole (.exe) a knihovny služeb (.dll) hostované Internetovou informační službou (IIS). Služba je webová služba ASMX, která implementuje smlouvu, která definuje vzor komunikace požadavek odpověď. Služba zpřístupňuje matematické`Add` `Subtract`operace `Multiply`( `Divide`, , , a ). Klient provádí synchronní požadavky na matematické operace a služby odpovědi s výsledkem. Aktivita klienta je viditelná v okně konzoly.  
  
 Implementace webové služby ASMX zobrazená v následujícím ukázkovém kódu vypočítá a vrátí příslušný výsledek.  
  
```csharp  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 Jak je nakonfigurováno, služba `http://localhost/servicemodelsamples/service.asmx` je přístupná klientem ve stejném počítači. Pro klienty na vzdálených počítačích pro přístup ke službě musí být zadán kvalifikovaný název domény namísto localhost.  
  
 Komunikace se provádí prostřednictvím klienta generované [servicemodel metadata utility tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Klient je obsažen v souboru generatedClient.cs. Služba ASMX musí být k dispozici pro generování proxy kódu, protože se používá k načtení aktualizovaných metadat. Spusťte následující příkaz z příkazového řádku v adresáři klienta a vygenerujte zadaný proxy server.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 Pomocí generovaného klienta můžete získat přístup ke koncovému bodu služby konfigurací příslušné adresy a vazby. Podobně jako služba klient používá konfigurační soubor (App.config) k určení koncového bodu pro komunikaci. Konfigurace koncového bodu klienta se skládá z absolutní adresy pro koncový bod služby, vazbu a smlouvu, jak je znázorněno v následující ukázce konfigurace.  
  
```xml  
<client>  
   <endpoint
      address="http://localhost/ServiceModelSamples/service.asmx"
      binding="basicHttpBinding"
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 Implementace klienta vytvoří instanci generovaného klienta. Vygenerovaný klient pak lze ke komunikaci se službou.  
  
```csharp  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
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
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
