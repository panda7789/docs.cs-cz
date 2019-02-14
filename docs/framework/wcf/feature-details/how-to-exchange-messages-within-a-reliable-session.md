---
title: 'Postupy: Výměna zpráv ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 145224655d1ec76c9deb5afc3c1a8ec9a1975f4f
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260683"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Postupy: Výměna zpráv ve spolehlivých relacích

Toto téma popisuje kroky potřebné k povolení stabilní relace pomocí jedné vazby poskytované systémem, které podporují tyto relace, ale není ve výchozím nastavení. Povolit stabilní relace imperativně pomocí kódu nebo deklarativně v konfiguračním souboru. Tento postup používá konfiguračních souborů klienta a služby, pokud chcete povolit ve stabilní relaci a stanovit, že zprávy dorazí ve stejném pořadí, ve kterém byly odeslány.

Klíčovou součástí tohoto postupu je, že obsahují element konfigurace koncového bodu `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem `Binding1`. [  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) element konfigurace odkazuje na tento název a povolit tak, že nastavíte spolehlivé relace `enabled` atribut [  **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) elementu `true`. Zadejte záruky doručení pro spolehlivé relace tak, že nastavíte `ordered` atribut `true`.

Pro zdrojovou kopii tohoto příkladu, naleznete v tématu [spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Nakonfigurovat službu pomocí WSHttpBinding používat spolehlivé relace

1. Definování kontraktu služby pro typ služby.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implementace kontraktu služby ve třídě služby. Všimněte si, že informace o adresu nebo vazby není zadán uvnitř implementace služby. Nejste nutné napsat kód pro načtení informací adresu nebo vazby v konfiguračním souboru.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Vytvoření *Web.config* souboru nakonfigurujte koncový bod `CalculatorService` , která používá <xref:System.ServiceModel.WSHttpBinding> s stabilní relace povolen a seřazené doručování zpráv vyžaduje.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Vytvoření *Service.svc* soubor, který obsahuje řádek:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  Místo *Service.svc* souboru ve virtuální adresář Internetové informační služby (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace klienta s WSHttpBinding používat spolehlivé relace

1. Použití [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Obsahuje generovaného klienta `ICalculator` rozhraní, které definuje kontrakt služby, který musí splňovat implementace klienta.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Generovaný klientskou aplikací také obsahuje implementaci `ClientCalculator`. Všimněte si, že informace o adrese a vazby není zadán kdekoli uvnitř implementace služby. Nejste nutné napsat kód pro načtení informací adresu nebo vazby v konfiguračním souboru.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* také generuje konfiguraci pro klienta, který se používá <xref:System.ServiceModel.WSHttpBinding> třídy. Název konfiguračního souboru *App.config* při používání sady Visual Studio.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Vytvoření instance `ClientCalculator` v aplikaci a volání operací služby.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Kompilace a spuštění klienta.

## <a name="example"></a>Příklad

Spolehlivé relace několik vazeb poskytovaných systémem podpory ve výchozím nastavení. Zde jsou některé z nich:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Příklad toho, jak vytvořit vlastní vazby, který podporuje spolehlivé relace, naleznete v tématu [jak: Vytvoření vazby vlastního stabilní relaci s HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Viz také:

- [Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
