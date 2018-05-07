---
title: Popis služby
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d86a6a78995042f0c6a45cf6e40e31c3e515e8eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="service-description"></a>Popis služby
Popis služby příklad ukazuje, jak službu můžete načíst jeho informace popisu služby za běhu. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), s další službou operace definované vrátit popisné informace o službě. Informace, které se vrátí seznam základní adresy a koncové body pro službu. Služba poskytuje s využitím tato informace <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, a <xref:System.ServiceModel.Description.ServiceDescription> třídy.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka má upravenou verzi kontrakt kalkulačky volat `IServiceDescriptionCalculator`. Kontrakt definuje operace další služby s názvem `GetServiceDescriptionInfo` , vrátí řetězec Víceřádkový klientovi, který popisuje základní adresa nebo adresy a koncový bod služby nebo koncové body pro službu.  
  
```  
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
  
 Implementace kód pro `GetServiceDescriptionInfo` používá <xref:System.ServiceModel.Description.ServiceDescription> seznam koncových bodů služby. Protože koncové body služby může mít relativní adresy, nejprve uvádí základní adresy pro službu. Všechny tyto informace získáte kód získá kontext jeho operace pomocí <xref:System.ServiceModel.OperationContext.Current%2A>. <xref:System.ServiceModel.ServiceHost> a jeho <xref:System.ServiceModel.Description.ServiceDescription> objektu se načítají z kontextu operaci. Pro zobrazení seznamu základní koncové body pro službu, kód iteruje hostitele služby <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> kolekce. Seznam koncových bodů služby pro službu, kód iteruje popis služby koncových bodů kolekce.  
  
```  
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
  
 Při spuštění ukázky, uvidíte na kalkulačky operace a pak vrácené informace o služby `GetServiceDescriptionInfo` operaci. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
  
## <a name="see-also"></a>Viz také
