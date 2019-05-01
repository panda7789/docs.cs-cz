---
title: 'Postupy: Vytvoření vlastní vazby pro spolehlivou relaci s HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: f39325829cf4b548482a6a570a5aa1fd65e61a1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039530"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Postupy: Vytvoření vlastní vazby pro spolehlivou relaci s HTTPS

Toto téma popisuje použití vrstvy SSL (Secure Sockets) zabezpečení přenosu pomocí spolehlivé relace. Pokud chcete použít stabilní relace přes protokol HTTPS, musíte vytvořit vlastní vazby, který používá stabilní relace a přenos protokolu HTTPS. Spolehlivá relace povolíte imperativně pomocí kódu nebo deklarativně v konfiguračním souboru. Tento postup používá konfiguračních souborů klienta a služby povolit ve stabilní relaci a [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) elementu.

Klíčovou součástí tohoto postupu je, že  **\<koncový bod >** obsahovat element konfigurace `bindingConfiguration` atribut, který odkazuje na vlastní vazby konfigurace s názvem `reliableSessionOverHttps`. [  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) element konfigurace odkazuje na tento název k určení, že jsou používány stabilní relace a přenos protokolu HTTPS včetně  **\< reliableSession >** a  **\<httpsTransport >** elementy.

Pro zdrojovou kopii tohoto příkladu, naleznete v tématu [vlastní vazby stabilní relace přes protokol HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Nakonfigurovat službu pomocí třídě CustomBinding použití stabilní relaci s HTTPS

1. Definování kontraktu služby pro typ služby.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Implementace kontraktu služby ve třídě služby. Všimněte si, že informace o adresu nebo vazby není zadán uvnitř implementace služby. Nejste nutné napsat kód pro načtení informací adresu nebo vazby v konfiguračním souboru.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Vytvoření *Web.config* souboru nakonfigurujte koncový bod `CalculatorService` s vlastní vazby s názvem `reliableSessionOverHttps` , která používá stabilní relace a přenos protokolu HTTPS.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Vytvoření *Service.svc* soubor, který obsahuje řádek:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Místo *Service.svc* souboru ve virtuální adresář Internetové informační služby (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurace klienta s třídě CustomBinding použití stabilní relaci s HTTPS

1. Použití [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku pro generování kódu z metadat služby.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Klient, který je generován obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí splňovat implementace klienta.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Generovaný klientskou aplikací také obsahuje implementaci `ClientCalculator`. Všimněte si, že není zadat informace o adrese a vazby v rámci implementace služby. Můžete se nevyžadují psaní kódu načíst informace o adrese a vazby v konfiguračním souboru.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Konfigurace vlastních vazeb s názvem `reliableSessionOverHttps` používat přenos protokolu HTTPS a spolehlivé relace.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Vytvoření instance `ClientCalculator` v aplikaci a pak volání operací služby.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Kompilace a spuštění klienta.  

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework

Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořen s *Makecert.exe*, výstrahu zabezpečení se zobrazí při pokusu o přístup k adresu HTTPS, jako například `https://localhost/servicemodelsamples/service.svc`, v prohlížeči.

## <a name="see-also"></a>Viz také:

- [Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
