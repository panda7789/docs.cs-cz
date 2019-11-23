---
title: 'Postupy: zabezpečení služby pomocí pověření systému Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: d02e697b23b6c745a59f3c9c37dd9c565f2f710e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320926"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Postupy: zabezpečení služby pomocí pověření systému Windows

V tomto tématu se dozvíte, jak povolit zabezpečení přenosu ve službě Windows Communication Foundation (WCF), která se nachází v doméně systému Windows a která je volána klienty ve stejné doméně. Další informace o tomto scénáři najdete v tématu [zabezpečení přenosu s ověřováním systému Windows](./feature-details/transport-security-with-windows-authentication.md). Ukázkovou aplikaci najdete v ukázce [WSHttpBinding](./samples/wshttpbinding.md) .

Toto téma předpokládá, že máte již definované existující rozhraní kontraktu a implementaci, a přidá k tomu. Můžete také upravit existující službu a klienta.

Službu s přihlašovacími údaji systému Windows můžete zabezpečit kompletně v kódu. Alternativně můžete vynechat část kódu pomocí konfiguračního souboru. Toto téma ukazuje oba způsoby. Ujistěte se, že používáte pouze jeden ze způsobů, nikoli obojí.

První tři postupy ukazují, jak službu zabezpečit pomocí kódu. Čtvrtý a pátý postup ukazuje, jak to provést s konfiguračním souborem.

## <a name="using-code"></a>Použití kódu

Úplný kód pro službu a klienta se nachází v části příklad na konci tohoto tématu.

První postup vás provede vytvořením a konfigurací <xref:System.ServiceModel.WSHttpBinding> třídy v kódu. Vazba používá přenos pomocí protokolu HTTP. Na straně klienta se používá stejná vazba.

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Vytvoření WSHttpBinding využívajícího přihlašovací údaje systému Windows a zabezpečení zpráv

1. Tento kód procedury je vložen na začátek metody `Run` třídy `Test` v kódu služby v části příklad.

2. Vytvořit instanci <xref:System.ServiceModel.WSHttpBinding> třídy.

3. Nastavte vlastnost <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> třídy <xref:System.ServiceModel.WSHttpSecurity> na <xref:System.ServiceModel.SecurityMode.Message>.

4. Nastavte vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> třídy <xref:System.ServiceModel.MessageSecurityOverHttp> na <xref:System.ServiceModel.MessageCredentialType.Windows>.

5. Kód pro tento postup je následující:

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a>Použití vazby ve službě

Toto je druhý postup, který ukazuje, jak použít vazbu v rámci samoobslužné služby. Další informace o hostitelských službách najdete v tématu [hostingové služby](hosting-services.md).

##### <a name="to-use-a-binding-in-a-service"></a>Použití vazby ve službě

1. Vložte kód této procedury za kód z předchozího postupu.

2. Vytvořte <xref:System.Type> proměnnou s názvem `contractType` a přiřaďte ji typu rozhraní (`ICalculator`). Při použití Visual Basic použijte operátor `GetType`; Při použití C#použijte klíčové slovo `typeof`.

3. Vytvořte druhou <xref:System.Type>ovou proměnnou s názvem `serviceType` a přiřaďte ji typu implementovaného kontraktu (`Calculator`).

4. Vytvořte instanci <xref:System.Uri> třídy s názvem `baseAddress` se základní adresou služby. Základní adresa musí mít schéma, které odpovídá přenosu. V tomto případě je přenosové schéma HTTP a adresa zahrnuje speciální identifikátor URI (Uniform Resource Identifier) "localhost" a číslo portu (8036) a také adresu základního koncového bodu (serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.

5. Vytvořte instanci třídy <xref:System.ServiceModel.ServiceHost> s proměnnými `serviceType` a `baseAddress`.

6. Přidejte koncový bod ke službě pomocí `contractType`, vazby a názvu koncového bodu (secureCalculator). Klient musí při inicializaci volání služby zřetězit základní adresu a název koncového bodu.

7. Pro spuštění služby volejte metodu <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Kód pro tento postup je zobrazen zde:

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a>Použití vazby v klientovi

Tento postup ukazuje, jak vygenerovat proxy server, který komunikuje se službou. Proxy se generuje pomocí nástroje pro tvorbu [metadat ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , který používá metadata služby k vytvoření proxy serveru.

Tento postup také vytvoří instanci třídy <xref:System.ServiceModel.WSHttpBinding> ke komunikaci se službou a poté volá službu.

Tento příklad používá pouze kód k vytvoření klienta. Alternativně můžete použít konfigurační soubor, který je uveden v části následující postup.

#### <a name="to-use-a-binding-in-a-client-with-code"></a>Použití vazby v klientovi s kódem

1. K vygenerování kódu proxy z metadat služby použijte nástroj SvcUtil. exe. Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md). Generovaný proxy kód dědí z třídy <xref:System.ServiceModel.ClientBase%601>, která zajišťuje, že každý klient má potřebné konstruktory, metody a vlastnosti ke komunikaci se službou WCF. V tomto příkladu vygenerovaný kód obsahuje třídu `CalculatorClient`, která implementuje rozhraní `ICalculator` a povoluje kompatibilitu s kódem služby.

2. Kód této procedury je vložen na začátek `Main` metody klientského programu.

3. Vytvořte instanci třídy <xref:System.ServiceModel.WSHttpBinding> a nastavte její režim zabezpečení na hodnotu `Message` a její typ pověření klienta na `Windows`. Příklad pojmenuje proměnnou `clientBinding`.

4. Vytvořte instanci <xref:System.ServiceModel.EndpointAddress> třídy s názvem `serviceAddress`. Inicializujte instanci se základní adresou zřetězenou s názvem koncového bodu.

5. Vytvořte instanci generované třídy klienta pomocí `serviceAddress` a proměnných `clientBinding`.

6. Zavolejte metodu <xref:System.ServiceModel.ClientBase%601.Open%2A>, jak je znázorněno v následujícím kódu.

7. Zavolejte službu a zobrazte výsledky.

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a>Použití konfiguračního souboru

Místo vytvoření vazby pomocí procedurálního kódu můžete použít následující kód, který je zobrazen pro oddíl Bindings konfiguračního souboru.

Pokud ještě nemáte definovanou službu, přečtěte si téma [navrhování a implementace služeb](designing-and-implementing-services.md)a [Konfigurace služeb](configuring-services.md).

> [!NOTE]
> Tento konfigurační kód se používá v konfiguračních souborech služby i klienta.

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Postup povolení přenosu zabezpečení ve službě v doméně systému Windows pomocí konfigurace

1. Přidejte [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) elementu do oddílu [\<vazby >](../configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru.

2. Do <`WSHttpBinding`> elementu přidejte prvek <`binding`> a nastavte atribut `configurationName` na hodnotu vhodnou pro vaši aplikaci.

3. Přidejte prvek <`security`> a nastavte atribut `mode` na Message.

4. Přidejte prvek <`message`> a nastavte atribut `clientCredentialType` na hodnotu Windows.

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

1. K vygenerování kódu a konfiguračního souboru proxy serveru z metadat služby použijte nástroj SvcUtil. exe. Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md).

2. Nahraďte část [\<vazby >](../configure-apps/file-schema/wcf/bindings.md) generovaného konfiguračního souboru kódem konfigurace z předchozí části.

3. Kód procedurální je vložen na začátek `Main` metody klientského programu.

4. Vytvořte instanci generované třídy klienta předáním názvu vazby v konfiguračním souboru jako vstupní parametr.

5. Zavolejte metodu <xref:System.ServiceModel.ClientBase%601.Open%2A>, jak je znázorněno v následujícím kódu.

6. Zavolejte službu a zobrazte výsledky.

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a>Příklad

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WSHttpBinding>
- [Nástroj metadat modelu služby (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Vytvoření klienta](how-to-create-a-wcf-client.md)
- [Zabezpečení služeb](securing-services.md)
- [Přehled zabezpečení](./feature-details/security-overview.md)
