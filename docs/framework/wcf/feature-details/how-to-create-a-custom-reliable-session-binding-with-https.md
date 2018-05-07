---
title: 'Postupy: vytvoření vazby vlastní spolehlivé relace s protokolem HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: b3699593f783fff1227ec51194956e0cc8577dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Postupy: vytvoření vazby vlastní spolehlivé relace s protokolem HTTPS

Toto téma ukazuje použití Secure Sockets Layer (SSL) zabezpečení přenosu s spolehlivé relace. Pokud chcete používat spolehlivé relace přes protokol HTTPS, musíte vytvořit vlastní vazby, které používá spolehlivé relace a přenos HTTPS. Spolehlivá relace povolíte imperativní pomocí kódu nebo deklarativně v konfiguračním souboru. Tento postup používá konfigurační soubory, které klient a služba umožňující spolehlivé relace a [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.

Část klíče tohoto postupu je, že  **\<endpoint >** konfigurace element obsahovat `bindingConfiguration` atribut, který odkazuje na vlastní vazby konfigurace s názvem `reliableSessionOverHttps`. [  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) konfigurační prvek odkazuje tento název zadat, že jsou používány spolehlivé relace a přenos HTTPS včetně  **\< reliableSession >** a  **\<httpsTransport >** elementy.

Zdroj kopírování tohoto příkladu, najdete v části [vlastní vazby spolehlivé relace HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurovat službu s CustomBinding používat spolehlivé relace s protokolem HTTPS

1. Definování kontraktu služby pro typ služby.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Implementujte kontrakt služby v třídě služby. Všimněte si, že není adresu nebo vazba informace zadat v rámci implementace služby. Budete se muset napsat kód pro načtení informací adresu nebo vazbu z konfiguračního souboru.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Vytvoření *Web.config* soubor konfigurace koncového bodu `CalculatorService` s vlastní vazby s názvem `reliableSessionOverHttps` používající spolehlivé relace a přenos HTTPS.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Vytvoření *Service.svc* soubor, který obsahuje na řádku:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Místo *Service.svc* souboru v virtuálního adresáře Internetové informační služby (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurace klienta s CustomBinding používat spolehlivé relace s protokolem HTTPS

1. Použití [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Obsahuje klienta, který se generuje `ICalculator` rozhraní, které definuje kontrakt služby, které musí splňovat implementace klienta.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Generovaného klienta aplikace také obsahuje implementace `ClientCalculator`. Všimněte si, že není zadat informace o adrese a vazbu v rámci implementace služby. Budete se muset napsat kód pro načtení informací adresu a vazbu z konfiguračního souboru.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Konfigurace vlastní vazby s názvem `reliableSessionOverHttps` pro přenos HTTPS a spolehlivé relace.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Vytvoření instance `ClientCalculator` v aplikaci a pak volání operací služby.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Zkompilování a spuštění klienta.  

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework

Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s *Makecert.exe*, při pokusu o přístupu, jako například adresou protokolu HTTPS se zobrazí výstraha zabezpečení `https://localhost/servicemodelsamples/service.svc`, z prohlížeče.

## <a name="see-also"></a>Viz také

[Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
