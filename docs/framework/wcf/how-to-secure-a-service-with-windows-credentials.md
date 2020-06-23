---
title: 'Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows'
description: Naučte se, jak povolit zabezpečení přenosu ve službě WCF, která se nachází v doméně systému Windows a která je volána klienty ve stejné doméně.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 8ef164e1475bfd5f047a99426a2bed43a7aa7353
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244630"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows

V tomto tématu se dozvíte, jak povolit zabezpečení přenosu ve službě Windows Communication Foundation (WCF), která se nachází v doméně systému Windows a která je volána klienty ve stejné doméně. Další informace o tomto scénáři najdete v tématu [zabezpečení přenosu s ověřováním systému Windows](./feature-details/transport-security-with-windows-authentication.md). Ukázkovou aplikaci najdete v ukázce [WSHttpBinding](./samples/wshttpbinding.md) .

Toto téma předpokládá, že máte již definované existující rozhraní kontraktu a implementaci, a přidá k tomu. Můžete také upravit existující službu a klienta.

Službu s přihlašovacími údaji systému Windows můžete zabezpečit kompletně v kódu. Alternativně můžete vynechat část kódu pomocí konfiguračního souboru. Toto téma ukazuje oba způsoby. Ujistěte se, že používáte pouze jeden ze způsobů, nikoli obojí.

První tři postupy ukazují, jak službu zabezpečit pomocí kódu. Čtvrtý a pátý postup ukazuje, jak to provést s konfiguračním souborem.

## <a name="using-code"></a>Použití kódu

Úplný kód pro službu a klienta se nachází v části příklad na konci tohoto tématu.

První postup vás provede vytvořením a konfigurací <xref:System.ServiceModel.WSHttpBinding> třídy v kódu. Vazba používá přenos pomocí protokolu HTTP. Na straně klienta se používá stejná vazba.

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Vytvoření WSHttpBinding využívajícího přihlašovací údaje systému Windows a zabezpečení zpráv

1. Kód této procedury je vložen na začátek `Run` metody `Test` třídy v kódu služby v části příklad.

2. Vytvořit instanci <xref:System.ServiceModel.WSHttpBinding> třídy.

3. Nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.WSHttpSecurity> třídy na <xref:System.ServiceModel.SecurityMode.Message> .

4. Nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp> třídy na <xref:System.ServiceModel.MessageCredentialType.Windows> .

5. Kód pro tento postup je následující:

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a>Použití vazby ve službě

Toto je druhý postup, který ukazuje, jak použít vazbu v rámci samoobslužné služby. Další informace o hostitelských službách najdete v tématu [hostingové služby](hosting-services.md).

##### <a name="to-use-a-binding-in-a-service"></a>Použití vazby ve službě

1. Vložte kód této procedury za kód z předchozího postupu.

2. Vytvořte <xref:System.Type> proměnnou s názvem `contractType` a přiřaďte ji typu rozhraní ( `ICalculator` ). Při použití Visual Basic použijte `GetType` operátor; při použití jazyka C# použijte `typeof` klíčové slovo.

3. Vytvořte druhou <xref:System.Type> proměnnou s názvem `serviceType` a přiřaďte ji typu implementovaného kontraktu ( `Calculator` ).

4. Vytvořte instanci <xref:System.Uri> třídy s názvem `baseAddress` se základní adresou služby. Základní adresa musí mít schéma, které odpovídá přenosu. V tomto případě je přenosové schéma HTTP a adresa zahrnuje speciální identifikátor URI (Uniform Resource Identifier) "localhost" a číslo portu (8036) a také adresu základního koncového bodu (serviceModelSamples/): `http://localhost:8036/serviceModelSamples/` .

5. Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy s `serviceType` `baseAddress` proměnnými a.

6. Přidejte koncový bod ke službě pomocí `contractType` , vazby a názvu koncového bodu (secureCalculator). Klient musí při inicializaci volání služby zřetězit základní adresu a název koncového bodu.

7. Zavolejte <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodu pro spuštění služby. Kód pro tento postup je zobrazen zde:

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a>Použití vazby v klientovi

Tento postup ukazuje, jak vygenerovat proxy server, který komunikuje se službou. Proxy se generuje pomocí nástroje pro tvorbu [metadat ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , který používá metadata služby k vytvoření proxy serveru.

Tento postup také vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy ke komunikaci se službou a poté zavolá službu.

Tento příklad používá pouze kód k vytvoření klienta. Alternativně můžete použít konfigurační soubor, který je uveden v části následující postup.

#### <a name="to-use-a-binding-in-a-client-with-code"></a>Použití vazby v klientovi s kódem

1. K vygenerování kódu proxy z metadat služby použijte nástroj SvcUtil.exe. Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md). Generovaný proxy kód dědí z <xref:System.ServiceModel.ClientBase%601> třídy, která zajišťuje, že každý klient má potřebné konstruktory, metody a vlastnosti ke komunikaci se službou WCF. V tomto příkladu vygenerovaný kód obsahuje `CalculatorClient` třídu, která implementuje `ICalculator` rozhraní a povoluje kompatibilitu s kódem služby.

2. Kód této procedury je vložen na začátek `Main` metody klientského programu.

3. Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte její režim zabezpečení na hodnotu `Message` a typ přihlašovacích údajů klienta na `Windows` . Příklad pojmenuje proměnnou `clientBinding` .

4. Vytvořte instanci <xref:System.ServiceModel.EndpointAddress> třídy s názvem `serviceAddress` . Inicializujte instanci se základní adresou zřetězenou s názvem koncového bodu.

5. Vytvořte instanci generované třídy klienta s `serviceAddress` `clientBinding` proměnnými a.

6. Zavolejte <xref:System.ServiceModel.ClientBase%601.Open%2A> metodu, jak je znázorněno v následujícím kódu.

7. Zavolejte službu a zobrazte výsledky.

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a>Použití konfiguračního souboru

Místo vytvoření vazby pomocí procedurálního kódu můžete použít následující kód, který je zobrazen pro oddíl Bindings konfiguračního souboru.

Pokud ještě nemáte definovanou službu, přečtěte si téma [navrhování a implementace služeb](designing-and-implementing-services.md)a [Konfigurace služeb](configuring-services.md).

> [!NOTE]
> Tento konfigurační kód se používá v konfiguračních souborech služby i klienta.

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Postup povolení přenosu zabezpečení ve službě v doméně systému Windows pomocí konfigurace

1. Přidejte [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element do [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) oddílu element konfiguračního souboru.

2. `binding`Do prvku <> přidejte prvek <> `WSHttpBinding` a nastavte `configurationName` atribut na hodnotu odpovídající vaší aplikaci.

3. Přidejte prvek <`security`> a nastavte `mode` atribut na Message.

4. Přidejte prvek <`message`> a nastavte `clientCredentialType` atribut na hodnotu Windows.

5. V konfiguračním souboru služby nahraďte `<bindings>` oddíl následujícím kódem. Pokud ještě nemáte konfigurační soubor služby, přečtěte si téma [použití vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md).

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a>Použití vazby v klientovi

Tento postup ukazuje, jak vygenerovat dva soubory: proxy server, který komunikuje se službou a konfiguračním souborem. Popisuje také změny v klientském programu, což je třetí soubor, který se používá na klientovi.

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Použití vazby v klientovi s konfigurací

1. Použijte nástroj SvcUtil.exe k vygenerování kódu a konfiguračního souboru proxy serveru z metadat služby. Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md).

2. Nahraďte [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) oddíl generovaného konfiguračního souboru konfiguračním kódem z předchozí části.

3. Kód procedurální je vložen na začátek `Main` metody klientského programu.

4. Vytvořte instanci generované třídy klienta předáním názvu vazby v konfiguračním souboru jako vstupní parametr.

5. Zavolejte <xref:System.ServiceModel.ClientBase%601.Open%2A> metodu, jak je znázorněno v následujícím kódu.

6. Zavolejte službu a zobrazte výsledky.

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a>Příklad

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.WSHttpBinding>
- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Vytvoření klienta](how-to-create-a-wcf-client.md)
- [Zabezpečení služeb](securing-services.md)
- [Přehled zabezpečení](./feature-details/security-overview.md)
