---
title: Zabezpečení zpráv pomocí zabezpečení přenosu
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
ms.openlocfilehash: f32e932bb6616911baa8991cb46a5940c8d285ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160885"
---
# <a name="securing-messages-using-transport-security"></a>Zabezpečení zpráv pomocí zabezpečení přenosu
Tato část popisuje zabezpečení přenosu služby Řízení front zpráv (MSMQ), který můžete použít k zabezpečení zprávy odeslané do fronty.  
  
> [!NOTE]
>  Před čtením prostřednictvím tohoto tématu, se doporučuje, abyste si přečetli [koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Následující obrázek poskytuje koncepční model komunikaci ve frontě pomocí Windows Communication Foundation (WCF). Tento obrázek a terminologie používá k popisu koncepty zabezpečení přenosu.  
  
 ![Ve frontě diagramu aplikace](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Při odesílání zpráv zařazených do fronty pomocí technologie WCF s <xref:System.ServiceModel.NetMsmqBinding>, zprávy WCF je připojen jako text zprávy služby MSMQ. Zabezpečení přenosu zabezpečí celou zprávu služby MSMQ (záhlaví zpráv MSMQ nebo vlastnosti a text zprávy). Protože je text zprávy služby MSMQ, pomocí zabezpečení přenosu také zabezpečuje zprávy WCF.  
  
 Klíčovým konceptem za zabezpečení přenosu je, že klient musí splňovat požadavky na zabezpečení, zobrazí se zpráva do cílové fronty. To je rozdíl oproti zabezpečení zpráv, ve kterém je zpráva zabezpečena pro aplikaci, která bude přijímat zprávy.  
  
 Pomocí zabezpečení přenosu <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ovlivňuje, jak jsou zabezpečené zprávy MSMQ během přenosu mezi fronty přenosu a cílová fronta tam, kde zabezpečené zahrnuje:  
  
-   Podepisování zpráv tak, aby byl nemanipulovalo.  
  
-   Zpráva, která má zajistěte, aby úmyslně viděli nebo šifrování. Toto je doporučená, ale volitelné.  
  
-   Správce front cílový označující, odesílatel zprávy pro popírání odpovědnosti.  
  
 Služby MSMQ nezávisle na ověřování, cílová fronta má seznam řízení přístupu (ACL), chcete-li zkontrolovat, zda klient má oprávnění k odeslání zprávy do cílové fronty. Přijímající aplikace je také kontroluje oprávnění přijímat zprávy z cílové fronty.  
  
## <a name="wcf-msmq-transport-security-properties"></a>WCF MSMQ Transport Security Properties  
 Zabezpečení Windows používaný službou MSMQ pro ověřování. Identifikátor zabezpečení Windows (SID) používá k identifikaci klienta a služby Active Directory jako certifikační autorita používá při ověřování klienta. To vyžaduje služba MSMQ nainstalovaná s integrací služby Active Directory. SID domény Windows, protože se používají k identifikaci klienta tato možnost zabezpečení je jenom smysluplné když klient a služba jsou součástí stejné domény Windows.  
  
 MSMQ také nabízí možnost připojit certifikát se zpráva, která není zaregistrované v Active Directory. V tomto případě zajišťuje, že zpráva byla podepsána pomocí certifikátu, který připojené.  
  
 WCF poskytuje jako součást zabezpečení přenosu služby MSMQ obě tyto možnosti a jejich klíče kontingenční tabulky pro zabezpečení přenosu.  
  
 Zabezpečení přenosu je ve výchozím nastavení zapnutá.  
  
 Zadaný tyto základy, v následujících částech vlastnosti zabezpečení přenosu podrobností součástí <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>Režim ověřování služby MSMQ  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> Určuje, jestli se má použít zabezpečení domény Windows nebo externího zabezpečení na základě certifikátů k zabezpečení zprávy. V obou režimech ověřování používá kanál zařazených do fronty přenosu WCF `CertificateValidationMode` zadaná v konfiguraci služby. Určuje režim ověřování certifikátu mechanismus, který se používá ke kontrole platnosti certifikátu.  
  
 Pokud je zapnuté zabezpečení přenosu, ve výchozím nastavení je <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Režim ověřování domény Windows  
 Na výběr mezi používáním zabezpečení Windows vyžaduje integrace služby Active Directory. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain> je výchozí režim zabezpečení transport. Když toto nastavení je nastaveno, kanál WCF připojí identifikátoru Windows SID zprávy služby MSMQ a používá svůj vnitřní certifikát získaný ze služby Active Directory. Tento vnitřní certifikát používaný službou MSMQ pro zabezpečení zprávy. Správce fronty používá službu Active Directory pro vyhledávání a nalezení odpovídajícího certifikátu ověřování klienta a ověří, že identifikátor SID také odpovídající jazyku klienta. Tento krok ověření se provede, pokud certifikát, buď generováno interně v případě třídy `WindowsDomain` režim ověřování nebo externě generované v případě třídy `Certificate` režim ověřování je připojen ke zprávě, i když je cílová fronta Neoznačeno jako vyžadující ověřování.  
  
> [!NOTE]
>  Při vytváření fronty, můžete označit fronty jako ověřený fronty k označení, že fronta vyžaduje ověřování klientů v odesílání zpráv do fronty. Tím se zajistí, že jsou přijaty žádné neověřené zprávy ve frontě.  
  
 Připojil se k němu identifikátor SID zprávy se také používá ke kontrole proti cílové fronty ACL, ujistěte se, že klient má oprávnění k odesílání zpráv do fronty.  
  
#### <a name="certificate-authentication-mode"></a>Režim ověřování certifikátu  
 Volba režimu ověřování certifikátu nevyžaduje, aby integrace služby Active Directory. Ve skutečnosti v některých případech, například když je služba MSMQ nainstalovaná v režimu pracovní skupiny (bez integrace služby Active Directory) nebo pomocí protokol spolehlivého zasílání zpráv SOAP (SRMP) při přenosu protokolu pro odesílání zpráv do fronty, pouze <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> funguje.  
  
 Při odesílání zprávy WCF s <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, kanál WCF se nepřipojí Windows SID zprávy služby MSMQ. V důsledku toho cílová fronta ACL musí povolovat `Anonymous` přístup uživatelů k odeslání do fronty. Správce fronty kontroluje, zda zprávy služby MSMQ byla podepsána pomocí certifikátu, ale neprovede žádné ověřování.  
  
 Certifikát s jeho deklarace identity a informací o identitě vložené <xref:System.ServiceModel.ServiceSecurityContext> kanálu zařazených do fronty přenosu WCF. Služby můžete použít tyto informace k provedení vlastní ověřování odesílatele.  
  
### <a name="msmq-protection-level"></a>Úroveň ochrany služby MSMQ  
 Úroveň ochrany Určuje, jak chránit zprávy služby MSMQ, ujistěte se, že není manipulováno. Je zadán v <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> vlastnost. Výchozí hodnota je <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>Úroveň ochrany přihlášení  
 Zprávy služby MSMQ je podepsaná pomocí certifikátu, který interně vygenerovanému, při použití `WindowsDomain` režim ověřování, nebo externě generovaného certifikát při použití `Certificate` režim ověřování.  
  
#### <a name="sign-and-encrypt-protection-level"></a>Podepisování a šifrování úroveň ochrany  
 Zprávy služby MSMQ je podepsaná pomocí certifikátu, který interně vygenerovanému, při použití `WindowsDomain` režim ověřování nebo externě vygenerovaný certifikát při použití `Certificate` režim ověřování.  
  
 Kromě podepsání zprávy zprávy služby MSMQ zašifrovaná pomocí veřejného klíče certifikátu získané ze služby Active Directory, který patří do Správce fronty, který je hostitelem cílové fronty. Odesílání správce fronty zajistí, že je při přenosu zašifrované zprávy služby MSMQ. Správce fronty dešifruje zprávy služby MSMQ pomocí soukromého klíče jeho vnitřní certifikát a uloží zprávu ve frontě (Pokud se ověří a autorizuje) ve formátu prostého textu.  
  
> [!NOTE]
>  Pro šifrování zprávy, je vyžadován přístup k Active Directory (`UseActiveDirectory` vlastnost <xref:System.ServiceModel.NetMsmqBinding> musí být nastaveno na `true`) a je možné s oběma <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> a <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Žádná úroveň ochrany  
 To je implicitní při <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> je nastavena na <xref:System.Net.Security.ProtectionLevel.None>. Nemůže to být platná hodnota pro jiné režimy ověřování.  
  
> [!NOTE]
>  Pokud zprávy služby MSMQ se znaménkem, MSMQ zkontroluje, zda zpráva je podepsané připojené certifikátem (interní nebo externí) bez ohledu na stav fronty, tedy ověřeného fronty, nebo ne.  
  
### <a name="msmq-encryption-algorithm"></a>Algoritmus šifrování služby MSMQ  
 Šifrovací algoritmus Určuje algoritmus použitý k šifrování zprávy služby MSMQ na lince. Tato vlastnost se používá jenom v případě <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> je nastavena na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Jsou podporované algoritmy `RC4Stream` a `AES` a výchozí hodnota je `RC4Stream`.  
  
 Můžete použít `AES` algoritmus pouze v případě, že má odesílatel služby MSMQ 4.0 nainstalované. Cílová fronta kromě toho musí být také hostovány na MSMQ 4.0.  
  
### <a name="msmq-hash-algorithm"></a>Algoritmus Hash MSMQ  
 Určuje algoritmus hash algoritmus použitý k vytvoření digitální podpis zprávy služby MSMQ. Správce fronty Tento stejný algoritmus používá k ověření zprávy služby MSMQ. Tato vlastnost se používá jenom v případě <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> je nastavena na <xref:System.Net.Security.ProtectionLevel.Sign> nebo <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Jsou podporované algoritmy `MD5`, `SHA1`, `SHA256`, a `SHA512`. Výchozí hodnota je `SHA1`.  
  
## <a name="see-also"></a>Viz také:

- [Přehled front](queues-overview.md)
- [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
