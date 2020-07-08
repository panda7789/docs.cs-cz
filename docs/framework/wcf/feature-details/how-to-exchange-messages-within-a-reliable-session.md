---
title: 'Postupy: Výměna zpráv ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 39dd6636f80b107ced1caac29869c6c66e67e21e
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052036"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Postupy: Výměna zpráv ve spolehlivých relacích

Toto téma popisuje kroky potřebné k povolení spolehlivé relace pomocí jedné z vazeb poskytovaných systémem, které podporují takovou relaci, ale nejsou ve výchozím nastavení. Spolehlivou relaci povolíte imperativně pomocí kódu nebo deklarativně v konfiguračním souboru. Tento postup používá konfigurační soubory klienta a služby k povolení spolehlivé relace a k určení toho, že zprávy přicházejí ve stejném pořadí, v jakém byly odeslány.

Klíčovou částí tohoto postupu je, že element konfigurace koncového bodu obsahuje `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem `Binding1` . [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element Configuration odkazuje na tento název, aby povoloval spolehlivé relace nastavením `enabled` atributu [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) elementu na `true` . Určete seřazené záruky doručení pro spolehlivou relaci nastavením `ordered` atributu na `true` .

Zdrojovou kopii tohoto příkladu najdete v tématu o [spolehlivé relaci WS](../samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace služby s WSHttpBinding pro použití spolehlivé relace

1. Definujte kontrakt služby pro typ služby.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implementujte kontrakt služby ve třídě služby. Všimněte si, že informace o adrese nebo vazbě nejsou určeny v rámci implementace služby. Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Vytvořte soubor *Web.config* pro konfiguraci koncového bodu pro `CalculatorService` , který používá možnost <xref:System.ServiceModel.WSHttpBinding> s povolenou spolehlivou relací a seřazeným doručením požadovaných zpráv.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Vytvořte soubor *Service. svc* , který obsahuje řádek:

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Soubor *Service. svc* umístěte do virtuálního adresáře Internetová informační služba (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace klienta s WSHttpBinding pro použití spolehlivé relace

1. Pro generování kódu z metadat služby použijte nástroj pro dodané [metadata (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Vygenerovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Vygenerovaná klientská aplikace také obsahuje implementaci `ClientCalculator` . Všimněte si, že informace o adrese a vazbě nejsou určeny nikde v implementaci služby. Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* také generuje konfiguraci pro klienta, který používá <xref:System.ServiceModel.WSHttpBinding> třídu. Při použití sady Visual Studio pojmenujte konfigurační soubor *App.config* .

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Vytvořte instanci `ClientCalculator` v aplikaci a zavolejte operace služby.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Zkompilujte a spusťte klienta.

## <a name="example"></a>Příklad

Několik vazeb poskytovaných systémem podporuje ve výchozím nastavení spolehlivé relace. Tady jsou některé z nich:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Příklad vytvoření vlastní vazby, která podporuje spolehlivé relace, najdete v tématu [Postupy: Vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Viz také

- [Spolehlivé relace](reliable-sessions.md)
