---
title: "Duplexní služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5c7cb9d963e56c6a6e06421afdb14427440643c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="duplex-services"></a>Duplexní služby
Kontrakt duplexní služby je vzorce výměny zpráv, ve kterém oba koncové body mohou zasílat zprávy do dalších nezávisle. Duplexní služby, proto mohou zasílat zprávy zpět do koncového bodu klienta, poskytuje podobné události chování. Duplexní komunikace nastane, když se klient připojuje ke službě a poskytuje službu s kanálem, na kterém služba mohou zasílat zprávy zpět do klienta. Všimněte si, že událost jako chování duplexní služby funguje pouze v rámci relace.  
  
 K vytvoření duplexního kontraktu vytvořit pár rozhraní. První je rozhraní kontraktu služby, které popisuje operace, které můžete vyvolat klienta. Musíte zadat Tento kontrakt služby *kontrakt zpětného volání* v <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> vlastnost. Kontrakt zpětného volání je rozhraní, které definuje operace, které služba můžete volat na koncovém bodu klienta. Duplexního kontraktu nevyžaduje relace, i když zkontrolujte duplexní vazby poskytované systémem použijte z nich.  
  
 Následuje příklad duplexního kontraktu.  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 `CalculatorService` Třída implementuje primární `ICalculatorDuplex` rozhraní. Služba používá <xref:System.ServiceModel.InstanceContextMode.PerSession> instance režimu zachování výsledek pro každou relaci. Soukromá vlastnost s názvem `Callback` přistupuje k kanál zpětného volání pro klienta. Služba používá zpětné volání pro odesílání zpráv zpět do klienta přes rozhraní zpětné volání, jak je znázorněno v následujícím ukázkovém kódu.  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 Klient musí poskytnout třídu, která implementuje rozhraní zpětné volání duplexního kontraktu pro příjem zpráv ze služby. Následující ukázkový kód ukazuje `CallbackHandler` třídu, která implementuje `ICalculatorDuplexCallback` rozhraní.  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Klienta, který se vygeneruje pro vyžaduje duplexního kontraktu <xref:System.ServiceModel.InstanceContext> třídy je třeba zadat při vytváření. To <xref:System.ServiceModel.InstanceContext> třída se používá jako lokality pro objekt, který implementuje rozhraní zpětného volání a zpracovává zprávy, které se odesílají zpět ze služby. <xref:System.ServiceModel.InstanceContext> Třída je vytvořený pomocí instance `CallbackHandler` třídy. Tento objekt zpracovává zprávy odeslané ze služby pro klienta v rozhraní zpětného volání.  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 Konfigurace služby musí ho nastavit má být poskytnuta vazba, která podporuje komunikaci relace a duplexní komunikace. `wsDualHttpBinding` Element podporuje komunikaci relace a umožňuje duplexní komunikace tím, že poskytuje duální připojení protokolu HTTP, jeden pro všechny směry.  
  
 Na klientovi je nutné nakonfigurovat adresu, která server můžete použít pro připojení ke klientovi, jak je znázorněno v následující ukázka konfigurace.  
  
  
  
> [!NOTE]
>  Duplexní bez klienty, kteří nepodaří ověřit pomocí zabezpečenou konverzaci obvykle throw <xref:System.ServiceModel.Security.MessageSecurityException>. Ale pokud se ověření nezdaří duplexní klienta, který používá zabezpečené konverzaci, klient přijme <xref:System.TimeoutException> místo.  
  
 Pokud vytvoříte klienta nebo službu pomocí `WSHttpBinding` elementu a nezahrnovat koncový bod zpětného volání klienta, zobrazí se následující chyba.  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 Následující vzorový kód ukazuje, jak zadat klienta adresa koncového bodu v kódu.  
  
```  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
  
 Následující vzorový kód ukazuje, jak zadat klienta adresa koncového bodu v konfiguraci.  
  
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
>  Duplexní modelu automaticky nerozpozná služba nebo klienta zavře jeho kanálu. Takže pokud klient neočekávaně ukončí, ve výchozím nastavení služba nebudete nijak upozorněni, nebo pokud neočekávaně ukončí klient služby nebudete nijak upozorněni. Služby a klienti můžete implementovat vlastní protokol navzájem upozorní, pokud si vyberou.  
  
## <a name="see-also"></a>Viz také  
 [Duplexní režim](../../../../docs/framework/wcf/samples/duplex.md)  
 [Určení chování klienta](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [Postupy: vytvoření postupu kanálu a použít ho k vytvoření a správě kanálů](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
