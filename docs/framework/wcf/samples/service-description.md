---
title: Popis služby
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d77797ed2871f2211ff142e2f45c160a92632138
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144083"
---
# <a name="service-description"></a>Popis služby
Ukázka popisu služby ukazuje, jak může služba načíst informace o popisu služby za běhu. Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), s další operace služby definované vrátit popisné informace o službě. Informace, které je vrácena seznamy základních adres a koncových bodů pro službu. Služba poskytuje tyto informace <xref:System.ServiceModel.OperationContext> <xref:System.ServiceModel.ServiceHost>pomocí <xref:System.ServiceModel.Description.ServiceDescription> , a třídy.  
  
 V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka má upravenou verzi `IServiceDescriptionCalculator`smlouvy kalkulačky s názvem . Smlouva definuje další operaci služby s názvem, `GetServiceDescriptionInfo` která vrátí víceřádkový řetězec klientovi, který popisuje základní adresu nebo adresy a koncový bod služby nebo koncové body pro službu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 Kód implementace `GetServiceDescriptionInfo` pro <xref:System.ServiceModel.Description.ServiceDescription> používá k seznamu koncových bodů služby. Vzhledem k tomu, že koncové body služby mohou mít relativní adresy, nejprve uvádí základní adresy pro službu. Chcete-li získat všechny tyto informace, kód <xref:System.ServiceModel.OperationContext.Current%2A>získá jeho provozní kontext pomocí . A <xref:System.ServiceModel.ServiceHost> jeho <xref:System.ServiceModel.Description.ServiceDescription> objekt jsou načteny z kontextu operace. Chcete-li seznam základních koncových bodů pro službu, kód <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> iterates prostřednictvím kolekce hostitele služby. Chcete-li seznam koncových bodů služby pro službu, kód iterates prostřednictvím kolekce koncových bodů popisu služby.  
  
```csharp
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 Při spuštění ukázky se zobrazí operace kalkulačky a potom `GetServiceDescriptionInfo` informace o službě vrácené operací. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
