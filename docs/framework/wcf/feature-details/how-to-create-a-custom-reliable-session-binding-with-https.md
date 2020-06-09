---
title: 'Postupy: Vytvoření vlastní vazby pro spolehlivou relaci s HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 70f8f4f33626ab0d1705e03750bfd9baa324e60a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598993"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Postupy: Vytvoření vlastní vazby pro spolehlivou relaci s HTTPS

Toto téma ukazuje použití zabezpečení přenosu SSL (Secure Sockets Layer) (SSL) u spolehlivých relací. Pokud chcete používat spolehlivou relaci přes protokol HTTPS, musíte vytvořit vlastní vazbu, která používá spolehlivou relaci a přenos HTTPS. Spolehlivou relaci povolíte buď imperativně, a to pomocí kódu nebo deklarativního v konfiguračním souboru. Tento postup používá konfigurační soubory klienta a služby k povolení spolehlivé relace a [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) elementu.

Klíčovou částí tohoto postupu je, že **\<endpoint>** element Configuration obsahuje `bindingConfiguration` atribut, který odkazuje na vlastní konfiguraci vazby s názvem `reliableSessionOverHttps` . [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element Configuration odkazuje na tento název a určí, že se bude používat Spolehlivá relace a přenos HTTPS, a to včetně **\<reliableSession>** **\<httpsTransport>** prvků a.

Pro zdrojovou kopii tohoto příkladu si přečtěte téma [vlastní vázání spolehlivé relace přes HTTPS](../samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurace služby s CustomBinding pro použití spolehlivé relace s protokolem HTTPS

1. Definujte kontrakt služby pro typ služby.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Implementujte kontrakt služby ve třídě služby. Všimněte si, že informace o adrese nebo vazbě nejsou určeny v rámci implementace služby. Nemusíte psát kód, který načte adresu nebo informace o vazbě z konfiguračního souboru.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Vytvořte soubor *Web. config* pro konfiguraci koncového bodu `CalculatorService` s vlastní vazbou s názvem `reliableSessionOverHttps` , který používá spolehlivou relaci a přenos HTTPS.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Vytvořte soubor *Service. svc* , který obsahuje řádek:

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. Soubor *Service. svc* umístěte do virtuálního adresáře Internetová informační služba (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Konfigurace klienta s CustomBinding pro použití spolehlivé relace s protokolem HTTPS

1. K vygenerování kódu z metadat služby použijte [Nástroj*Svcutil. exe*(ServiceModel Metadata Utility)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z příkazového řádku.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Generovaný klient obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí implementace klienta splňovat.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. Vygenerovaná klientská aplikace také obsahuje implementaci `ClientCalculator` . Všimněte si, že informace o adrese a vazbě nejsou určeny v rámci implementace služby. Nemusíte psát kód, který načte adresu a informace o vazbě z konfiguračního souboru.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Nakonfigurujte vlastní vazbu s názvem `reliableSessionOverHttps` tak, aby používala přenos HTTPS a spolehlivé relace.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Vytvořte instanci `ClientCalculator` v aplikaci a potom zavolejte operace služby.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Zkompilujte a spusťte klienta.  

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework

Vzhledem k tomu, že certifikát použitý v této ukázce je testovací certifikát vytvořený pomocí nástroje *Makecert. exe*, zobrazí se výstraha zabezpečení při pokusu o přístup k adrese https, jako `https://localhost/servicemodelsamples/service.svc` je například, z prohlížeče.

## <a name="see-also"></a>Viz také

- [Spolehlivé relace](reliable-sessions.md)
