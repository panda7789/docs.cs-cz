---
title: Klient ASMX se službou WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 5a0262361eac35ac45c3861deee13133011754ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="asmx-client-with-a-wcf-service"></a>Klient ASMX se službou WCF
Tento příklad ukazuje postup vytvoření služby pomocí služby Windows Communication Foundation (WCF) a pak z jinou hodnotu než přístup ke službě[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientovi, například klient ASMX.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované Internetové informační služby (IIS). Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (`Add`, `Subtract`, `Multiply`, a `Divide`). Klient ASMX zadává synchronní požadavků a odpovědí služby s výsledkem matematické operace.  
  
 Implementuje služby `ICalculator` smlouvy definovaným v následujícím kódu.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
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
  
 <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> mapování typů CLR na reprezentaci XML. <xref:System.Runtime.Serialization.DataContractSerializer> Jinak než XmlSerializer interpretuje některé reprezentace XML. Jinou hodnotu než[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generátory proxy serveru, jako je například Wsdl.exe, generovat více použitelné rozhraní při používání třídy XmlSerializer. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Se použije na `ICalculator` rozhraní, aby třídy XmlSerializer je používána pro mapování typů CLR do formátu XML. Implementace služby vypočítá a vrátí odpovídající výsledek.  
  
 Službu zpřístupní jeden koncový bod pro komunikaci se službou, definovat pomocí konfiguračního souboru (Web.config). Koncový bod se skládá z adresy, vazby a kontraktu. Službu zpřístupní koncový bod na základní adrese od hostitele Internetové informační služby (IIS). `binding` Je atribut nastaven na basicHttpBinding, která poskytuje HTTP komunikaci pomocí protokolu SOAP 1.1, který je kompatibilní s WS-I BasicProfile 1.1, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->  
    <endpoint address=""  
              binding="basicHttpBinding"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
</services>  
```  
  
 Klient ASMX komunikuje s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby pomocí zadaných proxy server, který je generován nástroj webové služby popis Language (WSDL) (Wsdl.exe). Typové proxy je obsažený v souboru generatedClient.cs. Nástroj WSDL načte metadata pro zadanou službu a generuje typové proxy server pro použití klientem komunikovat. Ve výchozím nastavení rozhraní nevystavuje veškerá metadata. Ke zveřejnění metadata vyžadovaných ke generování proxy server, je nutné přidat [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) a nastavit jeho `httpGetEnabled` atribut `True` jak je znázorněno v následující konfiguraci.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- Setting httpGetEnabled to True on the serviceMetadata  
           behavior exposes the service's wsdl at <base address>?wsdl :  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Spusťte následující příkaz z příkazového řádku v adresáři klienta ke generování typem proxy.  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 Pomocí vygenerovaný typové proxy server, klient může získat koncový bod uvedená služba nakonfigurováním příslušnou adresu. Klient použije k určení koncového bodu pro komunikaci se konfigurační soubor (App.config).  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 Implementace klienta vytvoří instanci typu proxy server při zahájení komunikace se službou.  
  
```  
// Create a client to the CalculatorService.  
using (CalculatorService client = new CalculatorService())  
{  
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
  
}  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Další informace o předávání a vrací data komplexní typy najdete v článku: [datové vazby v klientovi Windows Forms](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [datové vazby v klientovi Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), a [dat Vazby v klientovi ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a>Viz také
