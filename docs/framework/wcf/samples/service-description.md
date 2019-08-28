---
title: Popis služby
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: 430079cab91c61fe28db3f0a9d6c0797c7b0278a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038856"
---
# <a name="service-description"></a>Popis služby
Ukázka popis služby ukazuje, jak může služba získat informace o popisu služby za běhu. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)s definovanou další operací služby, která vrací popisné informace o službě. Vrácené informace obsahují seznam základních adres a koncových bodů pro službu. Služba poskytuje tyto informace pomocí <xref:System.ServiceModel.OperationContext>tříd, <xref:System.ServiceModel.ServiceHost>a <xref:System.ServiceModel.Description.ServiceDescription> .  
  
 V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 V této ukázce je nazvaná `IServiceDescriptionCalculator`upravená verze kontraktu kalkulačky. Smlouva definuje další operaci služby s názvem `GetServiceDescriptionInfo` , která vrací víceřádkový řetězec klientovi, který popisuje základní adresu, adresy a koncový bod služby nebo koncové body služby.  
  
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
  
 Implementační kód pro `GetServiceDescriptionInfo` <xref:System.ServiceModel.Description.ServiceDescription> používá pro výpis koncových bodů služby. Vzhledem k tomu, že koncové body služby mohou mít relativní adresy, nejprve vypíše základní adresy pro službu. Chcete-li získat všechny tyto informace, kód získá svůj kontext operace pomocí <xref:System.ServiceModel.OperationContext.Current%2A>. <xref:System.ServiceModel.ServiceHost> A jeho<xref:System.ServiceModel.Description.ServiceDescription> objekt jsou načteny z kontextu operace. Chcete-li zobrazit seznam základních koncových bodů pro službu, kód provede iteraci v <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> kolekci hostitele služby. Chcete-li zobrazit seznam koncových bodů služby pro službu, kód prochází z kolekce koncových bodů popisu služby.  
  
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
  
 Když spustíte ukázku, zobrazí se operace kalkulačky a potom informace o službě vrácené `GetServiceDescriptionInfo` operací. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
