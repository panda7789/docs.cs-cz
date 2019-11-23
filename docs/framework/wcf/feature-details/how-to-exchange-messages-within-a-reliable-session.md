---
title: 'Postupy: Výměna zpráv ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 58a392fc6295e82f41e08c80a3343b4059afad7e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141674"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Postupy: Výměna zpráv ve spolehlivých relacích

Toto téma popisuje kroky potřebné k povolení spolehlivé relace pomocí jedné z vazeb poskytovaných systémem, které podporují takovou relaci, ale nejsou ve výchozím nastavení. Spolehlivou relaci povolíte imperativně pomocí kódu nebo deklarativně v konfiguračním souboru. Tento postup používá konfigurační soubory klienta a služby k povolení spolehlivé relace a k určení toho, že zprávy přicházejí ve stejném pořadí, v jakém byly odeslány.

Klíčovou částí tohoto postupu je, že element konfigurace koncového bodu obsahuje atribut `bindingConfiguration`, který odkazuje na konfiguraci vazby s názvem `Binding1`. [ **\<vazba >** ](../../configure-apps/file-schema/wcf/bindings.md) element konfigurace odkazuje na tento název, aby povoloval spolehlivé relace nastavením atributu `enabled` [ **\<> elementu ReliableSession**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) na `true`. Určete seřazené záruky doručení pro spolehlivou relaci nastavením atributu `ordered` na `true`.

Zdrojovou kopii tohoto příkladu najdete v tématu o [spolehlivé relaci WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace služby s WSHttpBinding pro použití spolehlivé relace

1. Definujte kontrakt služby pro typ služby.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implementujte kontrakt služby ve třídě služby. Všimněte si, že informace o adrese nebo vazbě nejsou určeny v rámci implementace služby. Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Vytvořte soubor *Web. config* pro konfiguraci koncového bodu pro `CalculatorService`, který používá <xref:System.ServiceModel.WSHttpBinding> se zapnutou spolehlivou relací a objednané doručování požadovaných zpráv.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Vytvořte soubor *Service. svc* , který obsahuje řádek:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Soubor *Service. svc* umístěte do virtuálního adresáře Internetová informační služba (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace klienta s WSHttpBinding pro použití spolehlivé relace

1. K vygenerování kódu z metadat služby použijte [Nástroj*Svcutil. exe*(ServiceModel Metadata Utility)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Vygenerovaný klient obsahuje rozhraní `ICalculator` definující kontrakt služby, který musí implementace klienta splňovat.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Vygenerovaná klientská aplikace obsahuje také implementaci `ClientCalculator`. Všimněte si, že informace o adrese a vazbě nejsou určeny nikde v implementaci služby. Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil. exe* také generuje konfiguraci pro klienta, který používá třídu <xref:System.ServiceModel.WSHttpBinding>. Pojmenujte konfigurační soubor *App. config* při použití sady Visual Studio.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Vytvoření instance `ClientCalculator` v aplikaci a volání operací služby.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Zkompilujte a spusťte klienta.

## <a name="example"></a>Příklad

Několik vazeb poskytovaných systémem podporuje ve výchozím nastavení spolehlivé relace. Zde jsou některé z nich:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Příklad vytvoření vlastní vazby, která podporuje spolehlivé relace, najdete v tématu [Postupy: Vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Viz také:

- [Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
