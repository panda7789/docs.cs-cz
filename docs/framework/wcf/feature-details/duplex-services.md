---
title: Duplexní služby
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: 4fd8b679dcd4ac9efce5fa915118736b15206068
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834772"
---
# <a name="duplex-services"></a>Duplexní služby

Duplexní kontrakt služby je vzor výměny zpráv, ve kterém oba koncové body mohou odesílat zprávy jiným způsobem nezávisle. Duplexní služba, proto může odesílat zprávy zpátky do koncového bodu klienta a poskytovat tak chování podobné událostem. Duplexní komunikace probíhá při připojení klienta ke službě a poskytování služby s kanálem, ve kterém služba může odesílat zprávy zpět klientovi. Všimněte si, že chování funkcí duplexní služby funguje pouze v rámci relace.

Pro vytvoření duplexního kontraktu vytvoříte dvojici rozhraní. První je rozhraní kontraktu služby, které popisuje operace, které může klient vyvolat. Tento kontrakt služby musí ve vlastnosti <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> zadat *kontrakt zpětného volání* . Kontrakt zpětného volání je rozhraní, které definuje operace, které může služba volat na koncový bod klienta. Duplexní kontrakt nevyžaduje relaci, i když se systémem zajištěné duplexní vazby využívají.

Následuje příklad duplexního kontraktu.

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

Třída `CalculatorService` implementuje primární rozhraní `ICalculatorDuplex`. Služba používá režim instance <xref:System.ServiceModel.InstanceContextMode.PerSession> k udržení výsledku pro každou relaci. Soukromá vlastnost s názvem `Callback` přistupuje ke kanálu zpětného volání klientovi. Služba používá zpětné volání pro posílání zpráv zpátky do klienta prostřednictvím rozhraní zpětného volání, jak je znázorněno v následujícím ukázkovém kódu.

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

Klient musí poskytnout třídu, která implementuje rozhraní zpětného volání pro oboustrannou smlouvu pro příjem zpráv ze služby. Následující vzorový kód ukazuje třídu `CallbackHandler`, která implementuje rozhraní `ICalculatorDuplexCallback`.

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

Klient služby WCF, který je generován pro duplexní smlouvu, vyžaduje, aby při konstrukci poskytoval třídu <xref:System.ServiceModel.InstanceContext>. Tato třída <xref:System.ServiceModel.InstanceContext> slouží jako web pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy odesílané zpět ze služby. Třída <xref:System.ServiceModel.InstanceContext> je vytvořena s instancí třídy `CallbackHandler`. Tento objekt zpracovává zprávy odesílané ze služby klientovi na rozhraní zpětného volání.

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

Aby bylo možné vytvořit vazbu, která podporuje komunikaci relace i duplexní komunikaci, musí být nastavena konfigurace služby. Element `wsDualHttpBinding` podporuje komunikaci relací a umožňuje duplexní komunikaci tím, že poskytuje duální připojení HTTP, jedno pro každý směr.

Na straně klienta je nutné nakonfigurovat adresu, kterou může server použít pro připojení ke klientovi, jak je znázorněno v následující ukázkové konfiguraci.

> [!NOTE]
> Neduplexní klienti, kteří se nedaří ověřit pomocí zabezpečené konverzace, obvykle vyvolají <xref:System.ServiceModel.Security.MessageSecurityException>. Pokud však dojde k ověření duplexního klienta, který používá zabezpečenou konverzaci, klient obdrží místo toho <xref:System.TimeoutException>.

Pokud vytvoříte klienta nebo službu pomocí elementu `WSHttpBinding` a nezahrnete koncový bod zpětného volání klienta, zobrazí se následující chyba.

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

Následující vzorový kód ukazuje, jak zadat adresu koncového bodu klienta programově.

```csharp
WSDualHttpBinding binding = new WSDualHttpBinding();
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");
```

```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")
```

Následující vzorový kód ukazuje, jak zadat adresu koncového bodu klienta v konfiguraci.

```xml
<client>
    <endpoint name ="ServerEndpoint"
          address="http://localhost:12000/DuplexTestUsingConfig/Server"
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"
            binding="wsDualHttpBinding"
           contract="IDuplexTest" />
</client>
<bindings>
    <wsDualHttpBinding>
        <binding name="WSDualHttpBinding_IDuplexTest"
          clientBaseAddress="http://localhost:8000/myClient/" >
            <security mode="None"/>
         </binding>
    </wsDualHttpBinding>
</bindings>
```

> [!WARNING]
> Duplexní model se automaticky nerozpozná, když služba nebo klient ukončí svůj kanál. Takže pokud se klient neočekávaně ukončí, služba se ve výchozím nastavení nebude informovat nebo pokud se služba neočekávaně ukončí, klient nebude upozorněn. Pokud používáte službu, která je odpojena, je vyvolána výjimka <xref:System.ServiceModel.CommunicationException>. Klienti a služby můžou implementovat svůj vlastní protokol, aby si je vzájemně oznámili. Další informace o zpracování chyb naleznete v tématu [zpracování chyb WCF](../wcf-error-handling.md).

## <a name="see-also"></a>Viz také:

- [Duplex](../samples/duplex.md)
- [Nastavení chování klienta za běhu](../specifying-client-run-time-behavior.md)
- [Postupy: Vytvoření objektu pro vytváření kanálů a jeho použití k vytvoření a správě kanálů](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
