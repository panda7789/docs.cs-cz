---
title: Hlavičky adresy
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 133826bbbea62b660bdcdd884ce657528ad30873
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576002"
---
# <a name="address-headers"></a>Hlavičky adresy

Ukázka hlaviček adres ukazuje, jak mohou klienti předat parametry odkazu do služby pomocí Windows Communication Foundation (WCF).

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Specifikace WS-Addressing definuje pojem reference koncového bodu jako způsob, jak adresovat konkrétní koncový bod webové služby. V rámci WCF jsou odkazy na koncový bod modelovány pomocí `EndpointAddress` třídy – `EndpointAddress` je typ pole adresa `ServiceEndpoint` třídy.

Součástí referenčního modelu koncového bodu je, že každý odkaz může mít několik referenčních parametrů, které přidávají dodatečné identifikační informace. V rámci WCF jsou tyto parametry odkazu modelovány jako instance `AddressHeader` třídy.

V této ukázce klient přidá parametr reference do `EndpointAddress` koncového bodu klienta. Služba vyhledá tento parametr odkazu a použije jeho hodnotu v logice jeho operace služby Hello.

## <a name="client"></a>Klient

Aby mohl klient odeslat parametr odkazu, musí přidat `AddressHeader` do `EndpointAddress` `ServiceEndpoint` . Vzhledem k tomu `EndpointAddress` , že třída je neměnná, musí být úprava adresy koncového bodu provedena pomocí `EndpointAddressBuilder` třídy. Následující kód inicializuje klienta, aby odesílal parametr reference jako součást jeho zprávy.

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

Kód vytvoří `EndpointAddressBuilder` `EndpointAddress` jako počáteční hodnotu původní hodnotu. Pak přidá nově vytvořenou hlavičku adresy; volání pro `CreateAddressHeader` vytvoří hlavičku s určitým názvem, oborem názvů a hodnotou. Tady je hodnota "Jan". Po přidání hlavičky do Tvůrce `ToEndpointAddress()` Metoda převede (mutable) tvůrce zpátky na (neměnný) adresu koncového bodu, která se přiřadí zpátky do pole Adresa koncového bodu klienta.

Když nyní klient volá `Console.WriteLine(client.Hello());` , služba dokáže získat hodnotu tohoto parametru adresy, jak je vidět ve výsledném výstupu klienta.

`Hello, John`

## <a name="server"></a>Server

Implementace operace služby `Hello()` používá aktuální `OperationContext` pro kontrolu hodnot hlaviček v příchozí zprávě.

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

Kód projde všemi záhlavími příchozí zprávy a hledá hlavičky, které jsou referenčními parametry s konkrétním názvem a. Když je parametr nalezen, přečte hodnotu parametru a uloží jej do proměnné "ID".

#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
