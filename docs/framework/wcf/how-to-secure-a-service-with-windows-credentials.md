---
title: 'Postupy: Zabezpečení služby pomocí pověření systému Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: b5fece86dca524cb3f94f64dcb98361a93bf84a3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410924"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Postupy: Zabezpečení služby pomocí pověření systému Windows
Toto téma ukazuje, jak povolit zabezpečení přenosu pro službu Windows Communication Foundation (WCF), která se nachází v doméně Windows a je volán klienty ve stejné doméně. Další informace o tomto scénáři najdete v tématu [zabezpečení přenosu pomocí ověřování Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md). Ukázková aplikace, najdete v článku [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) vzorku.  
  
 Toto téma předpokládá máte existující rozhraní kontrakt a implementaci již definována a přidává ke, který. Můžete také upravit existující služby a služby klienta.  
  
 Můžete zabezpečení služby pomocí pověření Windows zcela v kódu. Alternativně můžete vynechat kód pomocí konfiguračního souboru. Toto téma ukazuje oba způsoby. Ujistěte se, že budete používat pouze jedním ze způsobů, ne obojí.  
  
 První tři postupy ukazují, jak zabezpečit pomocí kódu. Čtvrtý a pátý postup ukazuje, jak provést v konfiguračním souboru.  
  
## <a name="using-code"></a>Pomocí kódu  
 V části příklad na konci tohoto tématu je kompletní kód pro službu a klienta.  
  
 První postup vás provede vytvořením a konfigurací <xref:System.ServiceModel.WSHttpBinding> třídu v kódu. Vazba používá přenos pomocí protokolu HTTP. Stejnou vazbu se používá na straně klienta.  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Chcete-li vytvořit WSHttpBinding, používající Windows přihlašovacích údajů a zabezpečení zpráv  
  
1.  Tento postup kód je vložen na začátek `Run` metodu `Test` třídy v kódu služby v oddíle Příklad.  
  
2.  Vytvořit instanci <xref:System.ServiceModel.WSHttpBinding> třídy.  
  
3.  Nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.WSHttpSecurity> třídu <xref:System.ServiceModel.SecurityMode.Message>.  
  
4.  Nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp> třídu <xref:System.ServiceModel.MessageCredentialType.Windows>.  
  
5.  Kód pro tento postup je následující:  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a>Pomocí vazby ve službě  
 Toto je druhý postup ukazuje, jak tuto vazbu využíval v místním prostředí služby. Další informace o hostování služeb najdete v části [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
##### <a name="to-use-a-binding-in-a-service"></a>Chcete-li použít vazbu ve službě  
  
1.  Vložte tento postup kód za kód z předchozího postupu.  
  
2.  Vytvoření <xref:System.Type> proměnnou s názvem `contractType` a přiřaďte ho typu rozhraní (`ICalculator`). Při použití jazyka Visual Basic, použijte `GetType` operátor; při použití jazyka C#, použijte `typeof` – klíčové slovo.  
  
3.  Vytvořte druhý <xref:System.Type> proměnnou s názvem `serviceType` a přiřaďte ho typu implementovaného kontraktu (`Calculator`).  
  
4.  Vytvoření instance <xref:System.Uri> třídu s názvem `baseAddress` základní adresu služby. Základní adresa musí mít schéma, které odpovídá přenos. V takovém případě je schéma přenosu HTTP a adresa obsahuje speciální identifikátor URI (Uniform Resource) "localhost" a port číslo (8036) a také adresu základního koncového bodu ("serviceModelSamples /): `http://localhost:8036/serviceModelSamples/`.  
  
5.  Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy s `serviceType` a `baseAddress` proměnné.  
  
6.  Přidání koncového bodu služby pomocí `contractType`, vazby a název koncového bodu (secureCalculator). Klient musí při zahájení volání služby zřetězit základní adresu a název koncového bodu.  
  
7.  Volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda ke spuštění služby. Kód pro tento postup je znázorněna zde:  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a>Pomocí vazby v klientovi  
 Tento postup ukazuje, jak generovat proxy server, který komunikuje se službou. Generuje proxy server s použitím [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření proxy serveru používá metadata služby.  
  
 Tento postup také vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy ke komunikaci se službou a pak zavolá služba.  
  
 Tento příklad používá pouze kód pro vytvoření klienta. Jako alternativu můžete použít konfigurační soubor, který se zobrazí v části tohoto postupu.  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a>Pro použití vazby v klientovi s kódem  
  
1.  Pomocí nástroje SvcUtil.exe generovat proxy kód z metadat služby. Další informace najdete v tématu [jak: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Vygenerovaný proxy kód dědí z <xref:System.ServiceModel.ClientBase%601> třídu, která zajistí, že má každý klient nezbytné konstruktory, metody a vlastnosti komunikovat se službou WCF. V tomto příkladu obsahuje generovaného kódu `CalculatorClient` třídy, která implementuje `ICalculator` rozhraní, povolení kompatibility se kódu služby.  
  
2.  Tento postup kód je vložen na začátek `Main` metoda klientskou aplikaci.  
  
3.  Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte jeho režim zabezpečení na `Message` a typ do přihlašovacích údajů klienta `Windows`. Příklad názvy proměnné `clientBinding`.  
  
4.  Vytvoření instance <xref:System.ServiceModel.EndpointAddress> třídu s názvem `serviceAddress`. Inicializuje instanci se základní adresou zřetězená s název koncového bodu.  
  
5.  Vytvoření instance třídy generovaného klienta s `serviceAddress` a `clientBinding` proměnné.  
  
6.  Volání <xref:System.ServiceModel.ClientBase%601.Open%2A> způsob, jak je znázorněno v následujícím kódu.  
  
7.  Volání služby a zobrazí výsledky.  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a>Použití konfiguračního souboru  
 Místo vytváření vazby z kódu procedury, můžete použít následující kód pro části vazeb konfiguračního souboru.  
  
 Pokud již nemáte službě definované, najdete v článku [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md), a [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
 **Poznámka:** tento kód konfigurace se používá v konfiguračních souborech na služby a klienta.  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Povolit přenos zabezpečení ve službě service v doméně Windows pomocí konfigurace  
  
1.  Přidat [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element oddílu konfiguračního souboru.  
  
2.  Přidat <`binding`> element <`WSHttpBinding`> elementu a nastavte `configurationName` atribut na hodnotu vhodné pro vaši aplikaci.  
  
3.  Přidat <`security`> element a nastavte `mode` atribut na zprávu.  
  
4.  Přidat <`message`> element a nastavte `clientCredentialType` atribut pro Windows.  
  
5.  V konfiguračním souboru služby, nahraďte `<bindings>` oddíl s následujícím kódem. Pokud již nemáte konfigurační soubor služby, přečtěte si téma [pomocí vazby na konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
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
  
### <a name="using-the-binding-in-a-client"></a>Pomocí vazby v klientovi  
 Tento postup ukazuje, jak vytvořit dva soubory: proxy server, který komunikuje s služby a konfigurační soubor. Také popisuje změny klientský program, který je třetí souboru použít na straně klienta.  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Pro použití vazby v klientovi s konfigurací  
  
1.  Pomocí nástroje SvcUtil.exe pro generování souboru kódu a konfigurace proxy serveru z metadat služby. Další informace najdete v tématu [jak: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Nahradit [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) část vygenerovaný konfigurační soubor s kódem konfigurace z předchozí části.  
  
3.  Vložení kódu procedury na začátku `Main` metoda klientský program.  
  
4.  Vytvoření instance třídy generovaného klienta předejte název vazby v konfiguračním souboru jako vstupní parametr.  
  
5.  Volání <xref:System.ServiceModel.ClientBase%601.Open%2A> způsob, jak je znázorněno v následujícím kódu.  
  
6.  Volání služby a zobrazí výsledky.  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.WSHttpBinding>
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)
- [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)
