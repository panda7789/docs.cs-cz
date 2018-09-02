---
title: Hlavičky adresy
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: d2e38c674e0a3ea10df2e8363e90f4adf7edc9da
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420554"
---
# <a name="address-headers"></a>Hlavičky adresy
Hlavičky adresy ukázka demonstruje, jak klienti můžete předávat parametry referenční dokumentace ke službě pomocí Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Specifikace WS-Addressing koncept odkazem na koncový bod jako způsob, jak vyřešit konkrétní koncový bod webové služby. Ve službě WCF, jsou modelovány pomocí koncového bodu odkazy `EndpointAddress` class - `EndpointAddress` je typ pole adresu `ServiceEndpoint` třídy.  
  
 Referenční model koncový bod je, že každý odkaz můžete provést některé odkaz parametry, které přidávají další identifikační údaje. Ve službě WCF, jsou tyto parametry odkazů nemodelují jako instance `AddressHeader` třídy.  
  
 V této ukázce klienta přidá odkaz na parametr, aby `EndpointAddress` koncového bodu klienta. Služba hledá tento odkaz na parametr a použije její hodnotu v logice jeho operace služby "Hello".  
  
## <a name="client"></a>Klient  
 Pro klienta k odesílání referenční parametr, musíte přidat `AddressHeader` k `EndpointAddress` z `ServiceEndpoint`. Protože `EndpointAddress` třída je neměnný, je nutné provést úpravu adresy koncového bodu pomocí `EndpointAddressBuilder` třídy. Následující kód inicializuje klientovi umožní odeslat referenční parametr jako součást její zprávy.  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 Kód vytvoří `EndpointAddressBuilder` pomocí původní `EndpointAddress` jako počáteční hodnota. Potom přidá hlavičku adresu nově vytvořeného; volání `CreateAddressHeadercreates` záhlaví s konkrétním názvem, obor názvů a hodnotou. V tomto poli hodnota je "John". Po přidání záhlaví do Tvůrce `ToEndpointAddress()` metoda převede zpátky do adresy koncového bodu (neměnné), které je přiřazeno zpět do pole adresy koncový bod klienta (proměnlivé) Tvůrce.  
  
 Když klient teď volá `Console.WriteLine(client.Hello());`, služba je schopná k získání hodnoty tohoto parametru adresu, jak je vidět ve výsledném výstupu z klienta.  
  
 `Hello, John`  
  
## <a name="server"></a>Server  
 Provádění operace služby `Hello()` používá aktuální `OperationContext` ke kontrole hodnot hlavičky v příchozí zprávě.  
  
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
  
 Kód Iteruje přes všechny hlavičky v příchozí zprávě, hledá hlavičky, které jsou parametry odkazu s konkrétním názvem a. Po nalezení parametr přečte hodnotu parametru a uloží jej do proměnné "id".  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>Viz také
