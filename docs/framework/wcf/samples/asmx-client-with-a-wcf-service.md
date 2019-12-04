---
title: Klient ASMX se službou WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: a560650dba250d1ee4f0b959ead70a2915c9997f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716140"
---
# <a name="asmx-client-with-a-wcf-service"></a>Klient ASMX se službou WCF

Tento příklad ukazuje, jak vytvořit službu pomocí Windows Communication Foundation (WCF) a pak přistupovat ke službě z klienta jiného typu než WCF, jako je například klient ASMX.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Tato ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS). Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď. Kontrakt je definován rozhraním `ICalculator`, které zpřístupňuje matematické operace (`Add`, `Subtract`, `Multiply`a `Divide`). Klient ASMX provede synchronní požadavky na matematickou operaci a službu s výsledkem.

Služba implementuje kontrakt `ICalculator`, jak je definován v následujícím kódu.

```csharp
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

<xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> mapují typy CLR do reprezentace XML. <xref:System.Runtime.Serialization.DataContractSerializer> interpretuje některé reprezentace XML jinak než XmlSerializer. Generátory proxy jiných než WCF, jako je WSDL. exe, vygenerují při použití objektu XmlSerializer užitečnější rozhraní. <xref:System.ServiceModel.XmlSerializerFormatAttribute> se aplikuje na rozhraní `ICalculator`, aby se zajistilo, že se XmlSerializer používá pro mapování typů CLR do XML. Implementace služby vypočítá a vrátí příslušný výsledek.

Služba zpřístupňuje jeden koncový bod pro komunikaci se službou, definovaná pomocí konfiguračního souboru (Web. config). Koncový bod se skládá z adresy, vazby a kontraktu. Služba zpřístupňuje koncový bod na základní adrese poskytnuté hostitelem služby Internetová informační služba (IIS). Atribut `binding` je nastaven na basicHttpBinding, který poskytuje komunikaci HTTP pomocí protokolu SOAP 1,1, který je kompatibilní s WS-I BasicProfile 1,1, jak je znázorněno v následující ukázkové konfiguraci.

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

Klient ASMX komunikuje se službou WCF pomocí typovaného proxy, který je generovaný nástrojem WSDL (Web Services Description Language) (WSDL. exe). Zadaný proxy server je obsažený v souboru generatedClient.cs. Nástroj WSDL načte metadata pro zadanou službu a vygeneruje typový proxy pro použití klientem ke komunikaci. Ve výchozím nastavení rozhraní nevystavuje žádná metadata. Chcete-li zveřejnit metadata požadovaná pro vygenerování proxy serveru, je nutné přidat [\<> oddílu serviceMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) a nastavit jeho atribut `httpGetEnabled` na `True`, jak je znázorněno v následující konfiguraci.

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

Spusťte následující příkaz z příkazového řádku v adresáři klienta pro vygenerování typovaného proxy serveru.

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

Pomocí generovaného typovaného proxy serveru může klient získat přístup k danému koncovému bodu služby nakonfigurováním příslušné adresy. Klient používá konfigurační soubor (App. config) k určení koncového bodu ke komunikaci.

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

Implementace klienta vytvoří instanci typového proxy serveru pro zahájení komunikace se službou.

```csharp
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

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!NOTE]
> Další informace o předávání a vracení složitých datových typů naleznete v tématu: [datové vazby v klientovi model Windows Forms](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [datové vazby v klientovi Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md)a [datové vazby v klientovi ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md) .

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
