---
title: 'Postupy: Vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 26466a97ae44e6852c189d0b72bdba1b93d86141
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141732"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Postupy: Vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS

Toto téma ukazuje použití zabezpečení přenosu SSL (Secure Sockets Layer) (SSL) u spolehlivých relací. Pokud chcete používat spolehlivou relaci přes protokol HTTPS, musíte vytvořit vlastní vazbu, která používá spolehlivou relaci a přenos HTTPS. Spolehlivou relaci povolíte buď imperativně, a to pomocí kódu nebo deklarativního v konfiguračním souboru. Tento postup používá konfigurační soubory klienta a služby k povolení spolehlivé relace a [ **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) elementu.

Klíčovou částí tohoto postupu je, že **\<koncový bod >** konfigurační element obsahuje atribut `bindingConfiguration`, který odkazuje na vlastní konfiguraci vazby s názvem `reliableSessionOverHttps`. [ **\<vazba >** ](../../configure-apps/file-schema/wcf/bindings.md) elementu konfigurace odkazuje na tento název a určí, že se bude používat Spolehlivá relace a přenos HTTPS, a to zahrnutím **\<reliableSession >** a **\<ch >ch prvků httpsTransport** .

Pro zdrojovou kopii tohoto příkladu si přečtěte téma [vlastní vázání spolehlivé relace přes HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurace služby s CustomBinding pro použití spolehlivé relace s protokolem HTTPS

1. Definujte kontrakt služby pro typ služby.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Implementujte kontrakt služby ve třídě služby. Všimněte si, že informace o adrese nebo vazbě nejsou určeny v rámci implementace služby. Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Vytvořte soubor *Web. config* pro konfiguraci koncového bodu pro `CalculatorService` s vlastní vazbou s názvem `reliableSessionOverHttps`, která používá spolehlivou relaci a přenos HTTPS.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Vytvořte soubor *Service. svc* , který obsahuje řádek:

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. Soubor *Service. svc* umístěte do virtuálního adresáře Internetová informační služba (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurace klienta s CustomBinding pro použití spolehlivé relace s protokolem HTTPS

1. K vygenerování kódu z metadat služby použijte [Nástroj*Svcutil. exe*(ServiceModel Metadata Utility)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Vygenerovaný klient obsahuje rozhraní `ICalculator` definující kontrakt služby, který musí implementace klienta splňovat.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Vygenerovaná klientská aplikace obsahuje také implementaci `ClientCalculator`. Všimněte si, že informace o adrese a vazbě nejsou určeny v rámci implementace služby. Nemusíte psát kód, který načte adresu a informace o vazbě z konfiguračního souboru.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Nakonfigurujte vlastní vazbu s názvem `reliableSessionOverHttps`, aby používala přenos HTTPS a spolehlivé relace.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Vytvořte v aplikaci instanci `ClientCalculator` a potom zavolejte operace služby.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Zkompilujte a spusťte klienta.  

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework

Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje *Makecert. exe*, zobrazí se výstraha zabezpečení při pokusu o přístup k adrese https, například `https://localhost/servicemodelsamples/service.svc`, z prohlížeče.

## <a name="see-also"></a>Viz také:

- [Spolehlivé relace](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
