---
title: Duplexní služby
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a8197dfc877842be824a5b10c742ef4fb7792858
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592744"
---
# <a name="duplex-services"></a>Duplexní služby

Duplexní kontrakt služeb je vzoru výměny zpráv, ve kterém oba koncové body můžete odesílat zprávy do jiné nezávisle na sobě. Duplexní služby proto může odesílat zprávy zpět do koncový bod klienta, poskytování podobně jako události. Duplexní komunikaci nastane, pokud se klient připojí ke službě a poskytuje službu s kanálem, na kterém služba odesílat zprávy o zpět do klienta. Všimněte si, že události podobně duplexní služby funguje jenom v rámci relace.

K vytvoření duplexního kontraktu vytvořit dvojici rozhraní. První je rozhraní kontraktu služby, který popisuje operace, které může klient vyvolat. Musíte zadat Tento kontrakt služby *kontrakt zpětného volání* v <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> vlastnost. Smlouva zpětného volání je rozhraní, které definuje operace, které můžete volat službu na koncový bod klienta. Duplexní kontrakt nevyžaduje relace, i když duplexní vazeb poskytovaných systémem Ujistěte se, jejich použití.

Následuje příklad duplexního kontraktu.

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

`CalculatorService` Třída implementuje primární `ICalculatorDuplex` rozhraní. Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> režimu instance udržovat výsledek pro každou relaci. Soukromá vlastnost s názvem `Callback` přistupuje k zpětného volání kanálu ke klientovi. Služba používá zpětné volání pro odesílání zpráv zpět do klienta prostřednictvím rozhraní zpětného volání, jak je znázorněno v následujícím ukázkovém kódu.

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

Klient musí poskytnout třídu, která implementuje rozhraní zpětného volání duplexní kontrakt pro příjem zpráv ze služby. Následující ukázkový kód ukazuje `CallbackHandler` třídu, která implementuje `ICalculatorDuplexCallback` rozhraní.

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

Klient WCF, který je vygenerován pro duplexní kontrakt vyžaduje <xref:System.ServiceModel.InstanceContext> poskytované při konstrukci třídy. To <xref:System.ServiceModel.InstanceContext> třída se používá jako web pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy odeslané ze služby. <xref:System.ServiceModel.InstanceContext> Třídy je vytvořený pomocí instance `CallbackHandler` třídy. Tento objekt zpracovává zprávy odeslané do klienta v rozhraní zpětného volání ze služby.

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

Konfigurace pro službu, musíte nastavit má být poskytnuta vazba, která podporuje komunikace relace a duplexní komunikaci. `wsDualHttpBinding` Element podporuje komunikaci relace a umožňuje duplexní komunikaci poskytnutím duální připojení pomocí protokolu HTTP, jeden pro každý směr.

Na straně klienta je nutné nakonfigurovat adresu serveru můžete použít pro připojení ke klientovi, jak je znázorněno v následující ukázková konfigurace.

> [!NOTE]
> Throw bez duplexní klienty, kteří neumožňuje ověřovat, obvykle pomocí zabezpečené konverzace <xref:System.ServiceModel.Security.MessageSecurityException>. Ale pokud se ověření nezdaří duplexní klienta, který využívá zabezpečené konverzace, klient přijme <xref:System.TimeoutException> místo.

Pokud vytvoříte klienta a služby pomocí `WSHttpBinding` elementu a nezahrnují koncový bod klienta zpětné volání, zobrazí se následující chybová zpráva.

```
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

Následující ukázkový kód ukazuje, jak zadat klienta adresy koncového bodu prostřednictvím kódu programu.

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

Následující ukázkový kód ukazuje, jak zadat klienta adresy koncového bodu v konfiguraci.

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
> Když služba nebo klient ukončí její kanál duplexní modelu nerozpozná automaticky. Proto pokud klient neočekávaně ukončí, ve výchozím nastavení službu nedostanou nebo pokud je služba neočekávaně ukončena, klient nebude upozorněni. Služby a klienti můžou implementovat vlastní protokol na sebe navzájem upozornit, pokud se tedy rozhodne. Další informace o zpracování chyb, naleznete v tématu [zpracování chyb WCF](../wcf-error-handling.md)

## <a name="see-also"></a>Viz také:

- [Duplex](../samples/duplex.md)
- [Nastavení chování klienta za běhu](../specifying-client-run-time-behavior.md)
- [Postupy: Vytvoření objektu pro vytváření kanálů a jeho použití k vytvoření a správě kanálů](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
