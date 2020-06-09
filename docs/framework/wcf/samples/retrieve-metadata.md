---
title: Načítání metadat
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 4763686485dfe97844fad78cf0bb279113c0ce08
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594605"
---
# <a name="retrieve-metadata"></a>Načítání metadat
Tato ukázka předvádí, jak implementovat klienta, který dynamicky načítá metadata ze služby pro výběr koncového bodu, se kterým se má komunikovat. Tato ukázka je založena na [Začínáme](getting-started-sample.md). Služba byla upravena tak, aby zveřejnila dva koncové body – koncový bod na základní adrese pomocí `basicHttpBinding` vazby a zabezpečený koncový bod na adrese {*BaseAddress*}/Secure pomocí `wsHttpBinding` vazby. Namísto konfigurace klienta s adresami a vazbami koncových bodů klient dynamicky načítá metadata pro službu pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient> třídy a pak Importuje metadata jako <xref:System.ServiceModel.Description.ServiceEndpointCollection> pomocí <xref:System.ServiceModel.Description.WsdlImporter> třídy.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Klientská aplikace používá import <xref:System.ServiceModel.Description.ServiceEndpointCollection> k vytváření klientů ke komunikaci se službou. Klientská aplikace projde každým načteným koncovým bodem a komunikuje s každým koncovým bodem, který implementuje `ICalculator` kontrakt. Příslušná adresa a vazba jsou k dispozici u načteného koncového bodu, aby klient byl nakonfigurován tak, aby komunikoval s každým koncovým bodem, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 V okně konzoly klienta se zobrazují operace odesílané do každého koncového bodu, které zobrazují cestu k adrese a název vazby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
