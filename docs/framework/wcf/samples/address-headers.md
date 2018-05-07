---
title: Hlavičky adresy
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: c0e3807aadc18c7737f3a5e354135721cbfccf3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="address-headers"></a>Hlavičky adresy
Příklad hlavičky adresy znázorňuje, jak klienti můžete předat parametry referenční dokumentace ke službě pomocí Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Specifikace WS-Addressing definuje představu o odkaz na koncový bod jako způsob, jak konkrétní koncový bod webové služby. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], koncový bod odkazy jsou modelovány pomocí `EndpointAddress` třída - `EndpointAddress` je typ pole adresy `ServiceEndpoint` – třída.  
  
 Část referenčního modelu koncový bod je, že každý odkaz přenášet některé odkaz parametry, které přidat velmi identifikační informace. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], tyto parametry odkaz jsou modelovat jako instance `AddressHeader` třídy.  
  
 V této ukázce klienta přidá odkaz na parametr, který se `EndpointAddress` koncového bodu klienta. Služba hledá tento odkaz na parametr a používá jeho hodnotu v logice jeho operace služby "Hello".  
  
## <a name="client"></a>Klient  
 Pro klienta k odesílání parametr odkaz, musíte přidat `AddressHeader` k `EndpointAddress` z `ServiceEndpoint`. Protože `EndpointAddress` třídy se nedá změnit, změna adresy koncového bodu je třeba provést pomocí `EndpointAddressBuilder` – třída. Následující kód inicializuje klientovi umožní odeslat odkaz na parametr jako součást zprávy.  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 Kód vytvoří `EndpointAddressBuilder` pomocí původní `EndpointAddress` jako počáteční hodnota. Potom přidá hlavičku nově vytvořený adresu; volání `CreateAddressHeadercreates` hlavička s konkrétním názvem, obor názvů a hodnoty. V tomto poli hodnota je "Jan". Jakmile záhlaví se přidá do Tvůrce `ToEndpointAddress()` metoda převede (měnitelný) Tvůrce zpět na adresu koncového bodu (neměnné), která je přiřazená zpět do pole Adresa koncového bodu klienta.  
  
 Teď, když volání klienta `Console.WriteLine(client.Hello());`, služba je moct získat hodnotu tohoto parametru adresu, jak je vidět ve výsledném výstupu klienta.  
  
 `Hello, John`  
  
## <a name="server"></a>Server  
 Provádění operace služby `Hello()` používá aktuální `OperationContext` zkontrolovat hodnoty hlavičky na příchozí zprávy.  
  
```csharp   
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 Kód iteruje nad všechny hlavičky na příchozí zprávy, hledá hlavičky, které jsou parametry odkaz s určitým názvem a. Když se najde parametr čte hodnotu parametru a ukládá v proměnné "id".  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>Viz také
