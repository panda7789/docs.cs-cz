---
title: 'Postupy: zabezpečení služby pomocí pověření systému Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
caps.latest.revision: 26
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: c754a4ec57751b2ca5a809c771b2fb5235ec0510
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Postupy: zabezpečení služby pomocí pověření systému Windows
Toto téma ukazuje, jak povolit zabezpečení přenosu na [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služba, která se nachází v doméně systému Windows a je volána klienty ve stejné doméně. [!INCLUDE[crabout](../../../includes/crabout-md.md)] v tomto scénáři najdete v části [zabezpečení přenosu pomocí ověřování systému Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md). Ukázkovou aplikaci, najdete v článku [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) ukázka.  
  
 Toto téma předpokládá máte existující rozhraní kontrakt a implementaci již definována a přidá na který. Můžete také upravit existující službu a klienta.  
  
 Můžete zabezpečit služba pomocí přihlašovacích údajů Windows zcela v kódu. Alternativně můžete vynechat některé kódu pomocí konfiguračního souboru. Toto téma ukazuje obou směrech. Ujistěte se, že byste používat jenom jedním ze způsobů, nikoli oba dva.  
  
 První tři postupy ukazují, jak zabezpečit pomocí kódu. Čtvrtý a pátý postup ukazuje, jak to udělat pomocí konfiguračního souboru.  
  
## <a name="using-code"></a>Pomocí kódu  
 Kompletní kód pro tuto službu a klienta je v části příkladu na konci tohoto tématu.  
  
 První postup provede procesem vytvoření a konfiguraci <xref:System.ServiceModel.WSHttpBinding> – třída v kódu. Vazba používá přenos HTTP. Stejnou vazbu se používá na straně klienta.  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Chcete-li vytvořit WSHttpBinding, která používá přihlašovací údaje systému Windows a zabezpečení zpráv  
  
1.  Tento postup kód je vložen na začátku `Run` metodu `Test` – třída v kódu služby v části příklad.  
  
2.  Vytvořit instanci <xref:System.ServiceModel.WSHttpBinding> třídy.  
  
3.  Nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.WSHttpSecurity> třídy k <xref:System.ServiceModel.SecurityMode.Message>.  
  
4.  Nastavte <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp> třídy k <xref:System.ServiceModel.MessageCredentialType.Windows>.  
  
5.  Kód pro tento postup je následující:  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a>Pomocí vazby ve službě  
 Toto je druhý postup, který ukazuje způsob použití vazby v služba s vlastním hostováním. [!INCLUDE[crabout](../../../includes/crabout-md.md)] hostování služeb najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
##### <a name="to-use-a-binding-in-a-service"></a>Chcete-li použít vazbu ve službě  
  
1.  Vložení kódu tento postup po kód v předchozím postupu.  
  
2.  Vytvoření <xref:System.Type> proměnné s názvem `contractType` a přiřaďte ho typ rozhraní (`ICalculator`). Pokud používáte Visual Basic, použijte `GetType` operátor; při použití jazyka C#, použijte `typeof` – klíčové slovo.  
  
3.  Vytvořte druhý `Type` proměnné s názvem `serviceType` a přiřaďte ho typ implementovaná smlouvy (`Calculator`).  
  
4.  Vytvoření instance <xref:System.Uri> třídu s názvem `baseAddress` s základní adresa služby. Základní adresa musí mít schématu, která odpovídá přenosu. V takovém případě je schéma přenosu HTTP a adresu obsahuje speciální identifikátor URI (Uniform Resource) "localhost" a port number (8036) a také adresu základní koncový bod ("serviceModelSamples /): http://localhost:8036/serviceModelSamples/.  
  
5.  Vytvoření instance <xref:System.ServiceModel.ServiceHost> třídy s `serviceType` a `baseAddress` proměnné.  
  
6.  Přidání koncového bodu služby pomocí `contractType`, vazbu a název koncového bodu (secureCalculator). Při inicializaci volání služby musí klient řetězení základní adresu a název koncového bodu.  
  
7.  Volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda spuštění služby. Kód pro tento postup je uveden zde:  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a>Pomocí vazby v klientovi  
 Tento postup ukazuje, jak vygenerovat proxy server, který komunikuje se službou. Proxy server je generována [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , který používá metadata služby pro vytvoření proxy serveru.  
  
 Tento postup také vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy ke komunikaci se službou a potom zavolá službu.  
  
 Tento příklad používá jenom kód pro vytvoření klienta. Jako alternativu můžete konfigurační soubor, který se zobrazí v části tohoto postupu.  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a>Chcete-li použít vazby v klientovi s kódem  
  
1.  Použití nástroje SvcUtil.exe pro generování kódu proxy z metadat služby. Další informace najdete v tématu [postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Vygenerovaný proxy server kód dědí z <xref:System.ServiceModel.ClientBase%601> třídy, která zajistí, že má každý klient nezbytné konstruktory, metod a vlastností ke komunikaci s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. V tomto příkladu obsahuje generovaný kód `CalculatorClient` třídy, které implementuje `ICalculator` rozhraní, povolení kompatibilitu s kódu služby.  
  
2.  Tento postup kód je vložen na začátku `Main` metoda programu klienta.  
  
3.  Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte režim zabezpečení na `Message` a svého klienta na typ přihlašovacích údajů `Windows`. V příkladu názvy proměnnou `clientBinding`.  
  
4.  Vytvoření instance <xref:System.ServiceModel.EndpointAddress> třídu s názvem `serviceAddress`. Inicializaci instance s základní adresu zřetězen s název koncového bodu.  
  
5.  Vytvoření instance třídy generovaného klienta s `serviceAddress` a `clientBinding` proměnné.  
  
6.  Volání <xref:System.ServiceModel.ClientBase%601.Open%2A> metoda, jak je znázorněno v následujícím kódu.  
  
7.  Zavolá službu a zobrazit výsledky.  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a>Použití konfiguračního souboru  
 Místo vytvoření vazby s procedurální kódu, můžete použít následující kód ukazuje pro vazby oddíl konfiguračního souboru.  
  
 Pokud již službu definované nemáte, přečtěte si téma [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md), a [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
 **Poznámka:** tento kód konfigurace se používá v konfiguračních souborech na služby a klienta.  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Povolení služby v doméně systému Windows pomocí konfigurace zabezpečení přenosu  
  
1.  Přidat [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu, který chcete [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) části element konfiguračního souboru.  
  
2.  Přidat <`binding`> elementu, který chcete <`WSHttpBinding`> elementu a sadu `configurationName` vhodné pro vaše aplikace hodnotu atributu.  
  
3.  Přidat <`security`> elementu a sadu `mode` atribut zprávy.  
  
4.  Přidat <`message`> elementu a sadu `clientCredentialType` atribut systému Windows.  
  
5.  V konfiguračním souboru služby, nahraďte `<bindings>` oddíl následujícím kódem. Pokud již nemáte konfigurační soubor služby, přečtěte si téma [pomocí vazby na konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
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
 Tento postup ukazuje, jak vygenerovat dva soubory: proxy server, který komunikuje s službu a konfigurační soubor. Také popisuje změny v programu klienta, což je třetí soubor používá na klientovi.  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Chcete-li použít vazby v klientovi s konfigurací  
  
1.  Pomocí nástroje SvcUtil.exe vygenerujte soubor kódu a konfigurace proxy serveru z metadat služby. Další informace najdete v tématu [postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Nahraďte [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) části generovaného konfiguračního souboru s kódem konfigurace z předchozí části.  
  
3.  Na začátku je vložen procedurální kód `Main` metoda programu klienta.  
  
4.  Vytvoření instance třídy generovaného klienta předání názvu vazby v konfiguračním souboru jako vstupní parametr.  
  
5.  Volání <xref:System.ServiceModel.ClientBase%601.Open%2A> metoda, jak je znázorněno v následujícím kódu.  
  
6.  Zavolá službu a zobrazit výsledky.  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WSHttpBinding>  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)  
 [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)
