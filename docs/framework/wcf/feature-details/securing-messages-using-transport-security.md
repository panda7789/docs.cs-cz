---
title: "Zabezpečení zpráv pomocí zabezpečení přenosu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
caps.latest.revision: "21"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d40dc1540e4270fc0f80178207edf7b8277d7a73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="securing-messages-using-transport-security"></a>Zabezpečení zpráv pomocí zabezpečení přenosu
Tato část popisuje zabezpečení přenosu služby Řízení front zpráv (MSMQ), který vám pomůže zabezpečit zprávy odeslané do fronty.  
  
> [!NOTE]
>  Než si přečtete prostřednictvím tohoto tématu, doporučujeme, abyste si přečetli [koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Následující obrázek poskytuje koncepční model komunikace ve frontě pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Tento obrázek a terminologie používá k popisu koncepty zabezpečení přenosu.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Při odesílání zpráv zařazených do fronty pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s <xref:System.ServiceModel.NetMsmqBinding>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy je připojen jako text zprávy služby MSMQ. Zabezpečení přenosu zabezpečuje celé zprávy služby MSMQ (MSMQ hlavičky zpráv nebo vlastnosti a obsah zprávy). Protože se jedná do těla zprávy služby MSMQ, pomocí zabezpečení přenosu také zabezpečuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy.  
  
 Klíče koncept za zabezpečení přenosu je, že klient musí splňovat požadavky zabezpečení k získání zprávy do cílové fronty. To je rozdíl oproti zabezpečení zpráv, kde je pro aplikaci, která obdrží zprávu zabezpečené zprávy.  
  
 Pomocí zabezpečení přenosu <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ovlivňuje, jak jsou zabezpečené zprávy služby MSMQ během přenosu mezi fronty přenosu a cílová fronta kde zabezpečené znamená:  
  
-   Podepisování zpráv tak, aby byl není manipulováno.  
  
-   Zpráva, aby manipulováno vidět nebo šifrování. Toto je doporučená, ale volitelné.  
  
-   Správci cílové fronty, který identifikuje odesílatele zprávy pro zrušení odmítnutí.  
  
 V MSMQ nezávisle na ověřování, cílová fronta má seznam řízení přístupu (ACL) zkontrolujte, zda klient má oprávnění k odeslání zprávy do cílové fronty. Má přijímající aplikace se také kontroluje na oprávnění přijímat zprávy z cílové fronty.  
  
## <a name="wcf-msmq-transport-security-properties"></a>Vlastnosti zabezpečení přenos WCF MSMQ  
 MSMQ používá zabezpečení systému Windows pro ověřování. Identifikátor zabezpečení systému Windows (SID) používá k identifikaci klienta a používá adresářové služby Active Directory jako certifikační autority, pokud ověření klienta. To vyžaduje MSMQ nainstalovány s integrací služby Active Directory. Protože SID domény systému Windows slouží k identifikaci klienta, tato možnost zabezpečení má smysl pouze pokud klient a služba jsou součástí stejné domény systému Windows.  
  
 MSMQ taky poskytuje možnost pro připojení certifikátu se zprávou, který není zaregistrován u služby Active Directory. V takovém případě zajišťuje zpráva byla podepsána pomocí certifikátu připojené.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nabízí tyto možnosti jako součást služby MSMQ přenosu zabezpečení a jsou klíče pivot pro zabezpečení přenosu.  
  
 Zabezpečení přenosu je ve výchozím nastavení zapnutá.  
  
 Zadána tyto základní informace v následujících částech jsou vlastnosti zabezpečení přenosu podrobností dodávat s <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>Režim ověřování služby MSMQ  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> Stanoví, zda chcete použít zabezpečení domény systému Windows nebo externí zabezpečení založené na certifikátech zabezpečit zprávy. V obou režimech ověřování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá kanál zařazených do fronty přenosu `CertificateValidationMode` zadaný v konfiguraci služby. Režim ověření certifikátu určuje mechanismus používá k ověření platnosti certifikátu.  
  
 Když je zapnuté zabezpečení přenosu, výchozí nastavení je <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Režim ověřování domény systému Windows  
 Možnost použití zabezpečení systému Windows vyžaduje integrace služby Active Directory. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>je výchozí režim zabezpečení přenosu. Pokud je toto nastaveno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanál připojí k zprávy služby MSMQ SID systému Windows a používá svůj vnitřní certifikát získaný ze služby Active Directory. MSMQ používá tento vnitřní certifikát k zabezpečení zprávy. Přijímající správce front služby Active Directory používá k vyhledávání a najít certifikát odpovídající ověřit klienta a kontroluje, zda SID také odpovídá u klienta. Tento krok ověřování se spustí, pokud certifikát, buď generované interně u `WindowsDomain` režim ověřování nebo externě vygenerovat u `Certificate` režim ověřování, je připojen ke zprávě, i když je cílové fronty není označena jako vyžadování ověřování.  
  
> [!NOTE]
>  Při vytváření fronty, můžete označit fronty jako ověřený fronty k označení, že fronty vyžaduje ověření klienta odesílání zpráv do fronty. Tím se zajistí, že jsou přijaty žádné neověřené zprávy ve frontě.  
  
 Identifikátor SID připojené k zprávy se také používá ke kontrole proti seznamu ACL cílová fronta zajistit, že klient má oprávnění pro odesílání zpráv do fronty.  
  
#### <a name="certificate-authentication-mode"></a>Režim ověřování certifikátu  
 Možnost použití režimu ověřování certifikátu nevyžaduje, aby integrace služby Active Directory. Ve skutečnosti, v některých případech, například při instalaci služby MSMQ v režimu pracovní skupiny (bez integrace služby Active Directory) nebo pomocí protokol spolehlivého zasílání zpráv protokolu SOAP (SRMP) při přenosu protokolu k odesílání zpráv do fronty, pouze <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> funguje.  
  
 Při odesílání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpráv s <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanál nepřipojí identifikátor SID systému Windows ke zprávy služby MSMQ. Jako takový cílová fronta seznamu ACL musí povolovat `Anonymous` přístup uživatelů k odeslání do fronty. Přijímající správce front kontroluje, zda zprávy služby MSMQ byla podepsána pomocí certifikátu, ale neprovádí žádné ověřování.  
  
 Certifikát s jeho deklarace identity a informací o identitě se naplní v <xref:System.ServiceModel.ServiceSecurityContext> pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zařazených do fronty přenosu kanál. Služba možné využít tyto informace k vlastnímu ověřování odesílatele.  
  
### <a name="msmq-protection-level"></a>Úroveň ochrany služby MSMQ  
 Úroveň ochrany Určuje, jak chránit, ujistěte se, že není manipulováno zprávy služby MSMQ. Není zadán v <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> vlastnost. Výchozí hodnota je <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>Úroveň ochrany přihlášení  
 Zprávy služby MSMQ je podepsaná pomocí interně vygenerovaný certifikát při použití `WindowsDomain` režim ověřování nebo certifikát externě vygenerované při použití `Certificate` režim ověřování.  
  
#### <a name="sign-and-encrypt-protection-level"></a>Podepisování a šifrování úroveň ochrany  
 Zprávy služby MSMQ je podepsaná pomocí interně vygenerovaný certifikát při použití `WindowsDomain` režim ověřování nebo externě vygenerovaný certifikát při použití `Certificate` režim ověřování.  
  
 Kromě podpis zprávy, je zpráva MSMQ zašifrována pomocí veřejného klíče certifikátu získané ze služby Active Directory, který patří do přijímajícího správce front, který je hostitelem cílové fronty. Správce odesílání fronty zajišťuje, aby zprávy služby MSMQ šifrovala při přenosu. Využívá správce fronty pomocí soukromého klíče jeho vnitřní certifikát služby MSMQ zprávu dešifruje a ukládá zprávy ve frontě (Pokud ověřený a autorizovaný) ve formátu prostého textu.  
  
> [!NOTE]
>  Pro šifrování zprávy, je vyžadován přístup služby Active Directory (`UseActiveDirectory` vlastnost <xref:System.ServiceModel.NetMsmqBinding> musí být nastavena na `true`) a může být použit s oběma <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> a <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Žádné úrovně ochrany  
 To je zahrnuta, když <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> je nastaven na <xref:System.Net.Security.ProtectionLevel.None>. To nemůže být platná hodnota pro další režimy ověřování.  
  
> [!NOTE]
>  Pokud je podepsaný zprávy služby MSMQ, MSMQ zkontroluje, jestli zprávy je podepsaný certifikátem připojené (interní nebo externí) bez ohledu na stav fronty, který je ověřeného fronty nebo ne.  
  
### <a name="msmq-encryption-algorithm"></a>Algoritmus šifrování služby MSMQ  
 Šifrovací algoritmus Určuje algoritmus použitý k šifrování zpráv služby MSMQ v drátové síti. Tato vlastnost se používá pouze v případě <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> je nastaven na <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Podporované algoritmy jsou `RC4Stream` a `AES` a výchozí hodnota je `RC4Stream`.  
  
 Můžete použít `AES` algoritmus pouze v případě, že odesílatel má MSMQ 4.0 nainstalované. Kromě toho musí být cílová fronta také hostované na MSMQ 4.0.  
  
### <a name="msmq-hash-algorithm"></a>Algoritmus Hash MSMQ  
 Algoritmus hash určuje algoritmus použitý k vytvoření digitální podpis zprávy služby MSMQ. Přijímající správce front Tento stejný algoritmus používá k ověření zprávy služby MSMQ. Tato vlastnost se používá pouze v případě <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> je nastaven na <xref:System.Net.Security.ProtectionLevel.Sign> nebo <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Podporované algoritmy jsou `MD5`, `SHA1`, `SHA256`, a `SHA512`. Výchozí hodnota je `SHA1`.  
  
## <a name="see-also"></a>Viz také  
 [Služba Řízení front zpráv](http://msdn.microsoft.com/en-us/ff917e87-05d5-478f-9430-0f560675ece1)  
 [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
