---
title: "Postupy: Výměna zpráv ve spolehlivých relacích"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aad62d8532fff09157d53f8307fb2b9dcd506cd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Postupy: Výměna zpráv ve spolehlivých relacích

Toto téma popisuje kroky potřebné k povolení spolehlivé relace pomocí jedné vazby poskytované systémem, které podporují tyto relace, ale není ve výchozím nastavení. Povolit spolehlivé relace imperativní pomocí kódu nebo deklarativně v konfiguračním souboru. Tento postup používá konfigurační soubory klienta a služby, povolte spolehlivé relace a stanovení, zda doručení zpráv ve stejném pořadí, ve které byly odeslány.

Část klíče tohoto postupu je, že element konfigurace koncového bodu obsahovat `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem `Binding1`. [  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) konfigurační prvek odkazuje tento název pro nastavení Povolit spolehlivé relace `enabled` atribut [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element `true`. Zadejte záruky doručení pro spolehlivé relace nastavením `ordered` atribut `true`.

Zdroj kopírování tohoto příkladu, najdete v části [spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurovat službu s WSHttpBinding používat spolehlivé relace

1. Definování kontraktu služby pro typ služby.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implementujte kontrakt služby v třídě služby. Všimněte si, že není adresu nebo vazba informace zadat v rámci implementace služby. Budete se muset napsat kód pro načtení informací informace adresu nebo vazbu z konfiguračního souboru.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Vytvoření *Web.config* soubor konfigurace koncového bodu `CalculatorService` používající <xref:System.ServiceModel.WSHttpBinding> s spolehlivé relace povolen a seřazené doručení zpráv, které jsou potřeba.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Vytvoření *Service.svc* soubor, který obsahuje na řádku:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  Místo *Service.svc* souboru v virtuálního adresáře Internetové informační služby (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace klienta s WSHttpBinding používat spolehlivé relace

1. Použití [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Obsahuje generovaného klienta `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Generovaného klienta aplikace také obsahuje implementace `ClientCalculator`. Všimněte si, že informace o adrese a vazba není zadán kdekoli uvnitř implementace služby. Budete se muset napsat kód pro načtení informací informace adresu nebo vazbu z konfiguračního souboru.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* také generuje konfiguraci pro klienta, který používá <xref:System.ServiceModel.WSHttpBinding> třídy. Název konfiguračního souboru *App.config* při použití [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Vytvoření instance `ClientCalculator` v aplikaci a volání operací služby.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Zkompilování a spuštění klienta.

## <a name="example"></a>Příklad

Několik vazeb poskytovaných systémem podporují spolehlivé relace ve výchozím nastavení. Mezi ně patří:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Příklad vytvoření vlastní vazby, která podporuje spolehlivé relace, naleznete v části [postupy: vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Viz také

[Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
