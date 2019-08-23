---
title: Zabezpečení zpráv pomocí zabezpečení přenosu
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
ms.openlocfilehash: b0507590914e2e8cda7e5e599914a9e3d7b0acd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911710"
---
# <a name="securing-messages-using-transport-security"></a>Zabezpečení zpráv pomocí zabezpečení přenosu
Tato část popisuje zabezpečení přenosu služby Řízení front zpráv (MSMQ), které můžete použít k zabezpečení zpráv odesílaných do fronty.  
  
> [!NOTE]
> Než si přečtete toto téma, doporučujeme, abyste si přečetli [koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Následující ilustrace poskytuje koncepční model komunikace ve frontě pomocí Windows Communication Foundation (WCF). Tato ilustrace a terminologie slouží k vysvětlení konceptů zabezpečení přenosu.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distribuované – fronta – obrázek")  
  
 Při posílání zpráv ve frontě pomocí <xref:System.ServiceModel.NetMsmqBinding>WCF s, je zpráva WCF připojená jako tělo zprávy služby MSMQ. Zabezpečení přenosu zabezpečuje celou zprávu služby MSMQ (záhlaví zpráv služby MSMQ nebo vlastnosti a tělo zprávy). Vzhledem k tomu, že se jedná o tělo zprávy služby MSMQ, používá zabezpečení přenosu také zprávu WCF.  
  
 Klíčovým konceptem zabezpečení přenosu je, že klient musí splňovat požadavky na zabezpečení a získat tak zprávu do cílové fronty. To je na rozdíl od zabezpečení zpráv, kde je zpráva zabezpečená pro aplikaci, která zprávu přijímá.  
  
 Zabezpečení přenosu pomocí <xref:System.ServiceModel.NetMsmqBinding> a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ovlivňuje způsob, jakým jsou zprávy MSMQ zabezpečeny během přenosu mezi frontou přenosů a cílovou frontou, kde zabezpečení implikuje:  
  
- Podpis zprávy, aby se zajistilo, že není úmyslně poškozen.  
  
- Šifrování zprávy, aby se zajistilo, že se nedá zobrazit ani úmyslně neoprávněně. Toto doporučení je doporučené, ale nepovinné.  
  
- Cílový správce fronty, který identifikuje odesílatele zprávy pro Neodmítnutí.  
  
 V případě služby MSMQ, která nezávisí na ověřování, má cílová fronta seznam řízení přístupu (ACL), který kontroluje, zda má klient oprávnění Odeslat zprávu do cílové fronty. U přijímající aplikace je také zaškrtnuto oprávnění k přijetí zprávy z cílové fronty.  
  
## <a name="wcf-msmq-transport-security-properties"></a>WCF – vlastnosti zabezpečení přenosu MSMQ  
 Služba MSMQ používá pro ověřování zabezpečení systému Windows. Pomocí identifikátoru zabezpečení systému Windows (SID) identifikuje klienta a při ověřování klienta používá adresářovou službu Active Directory jako certifikační autoritu. K tomu je potřeba nainstalovat službu MSMQ s integrací služby Active Directory. Vzhledem k tomu, že se k identifikaci klienta používá identifikátor SID domény Windows, je tato možnost zabezpečení smysluplná jenom v případě, že je klient i služba součástí stejné domény systému Windows.  
  
 Služba MSMQ taky umožňuje připojit certifikát se zprávou, která není zaregistrovaná ve službě Active Directory. V takovém případě zajišťuje, aby byla zpráva podepsána pomocí připojeného certifikátu.  
  
 Služba WCF poskytuje obě tyto možnosti jako součást zabezpečení přenosu ve službě MSMQ a jsou klíčem pro zabezpečení přenosu.  
  
 Ve výchozím nastavení je zabezpečení přenosu zapnuté.  
  
 Následující části obsahují podrobné informace o vlastnostech transportního zabezpečení, které jsou součástí <xref:System.ServiceModel.NetMsmqBinding> sady <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>a.  
  
#### <a name="msmq-authentication-mode"></a>Režim ověřování MSMQ  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> Určí, zda se má zabezpečit zpráva pomocí zabezpečení domény systému Windows nebo externího zabezpečení založeného na certifikátech. V obou režimech ověřování používá `CertificateValidationMode` transportní kanál zařazený do fronty WCF zadaný v konfiguraci služby. Režim ověřování certifikátu určuje mechanismus, který slouží ke kontrole platnosti certifikátu.  
  
 Když je zapnuté zabezpečení přenosu, výchozí nastavení je <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Režim ověřování domény systému Windows  
 Možnost použití zabezpečení systému Windows vyžaduje integraci služby Active Directory. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>je výchozím režimem zabezpečení přenosu. Pokud je tato nastavení nastavena, kanál WCF připojí ke zprávě služby MSMQ identifikátor Windows SID a použije svůj vnitřní certifikát získaný ze služby Active Directory. Služba MSMQ používá tento interní certifikát k zabezpečení zprávy. Příjmový správce fronty používá službu Active Directory k vyhledávání a hledání odpovídajícího certifikátu pro ověření klienta a kontroluje, zda identifikátor SID odpovídá také tomuto klientovi. Tento krok ověřování se spustí, pokud je certifikát, který se buď interně vygeneroval v případě `WindowsDomain` režimu ověřování nebo externě generovaný v `Certificate` případě režimu ověřování, připojený ke zprávě i v případě, že cílová fronta je není označen jako vyžadování ověřování.  
  
> [!NOTE]
> Při vytváření fronty můžete označit frontu jako ověřenou frontu a označit tak, že fronta vyžaduje ověření klienta odesílajícího zprávy do fronty. Tím se zajistí, že ve frontě nebudou přijaty žádné neověřené zprávy.  
  
 Identifikátor SID připojený ke zprávě se také používá ke kontrole seznamu ACL cílové fronty, aby bylo zajištěno, že klient bude mít oprávnění odesílat zprávy do fronty.  
  
#### <a name="certificate-authentication-mode"></a>Režim ověřování certifikátu  
 Volba použití režimu ověřování certifikátů nevyžaduje integraci služby Active Directory. V některých případech, například když je služba MSMQ nainstalována v režimu pracovní skupiny (bez integrace služby Active Directory) nebo při odesílání zpráv do fronty pomocí protokolu přenosu protokolu SOAP Reliable Messaging Protocol (SRMP), funguje pouze <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> funkce.  
  
 Při odesílání zprávy WCF pomocí <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>kanálu WCF nepřipojí ke zprávě služby MSMQ identifikátor zabezpečení systému Windows. V takovém případě musí seznam ACL cílové fronty umožňovat `Anonymous` uživateli přístup k odeslání do fronty. Správce přijímací fronty ověří, zda byla zpráva služby MSMQ podepsána certifikátem, ale neprovede žádné ověření.  
  
 Certifikát s jeho deklaracemi a informacemi o identitě vyplní <xref:System.ServiceModel.ServiceSecurityContext> transportní kanál WCF ve frontě. Služba může tyto informace použít k provedení vlastního ověření odesílatele.  
  
### <a name="msmq-protection-level"></a>Úroveň ochrany MSMQ  
 Úroveň ochrany určuje, jak chránit zprávu služby MSMQ, aby se zajistilo, že není úmyslně poškozena. Je určena ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> vlastnosti. Výchozí hodnota je <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>Úroveň ochrany při podepisování  
 Zpráva služby MSMQ je podepsána pomocí vnitřně generovaného certifikátu `WindowsDomain` při použití režimu ověřování nebo externě vygenerovaného `Certificate` certifikátu při použití režimu ověřování.  
  
#### <a name="sign-and-encrypt-protection-level"></a>Úroveň ochrany podepsat a šifrovat  
 Zpráva služby MSMQ je podepsána pomocí vnitřně generovaného certifikátu `WindowsDomain` při použití režimu ověřování nebo externě vygenerovaného certifikátu při použití `Certificate` režimu ověřování.  
  
 Kromě podepisování zprávy je zpráva služby MSMQ zašifrovaná pomocí veřejného klíče certifikátu získaného ze služby Active Directory, která patří k přijímacímu Správci front, který hostuje cílovou frontu. Správce odesílající fronty zajišťuje, aby zpráva MSMQ byla při přenosu zašifrovaná. Správce fronty příjmu dešifruje zprávu služby MSMQ pomocí privátního klíče jeho interního certifikátu a uloží zprávu do fronty (Pokud je to ověřeno a autorizováno) ve formě prostého textu.  
  
> [!NOTE]
> Chcete-li zašifrovat zprávu, je požadován přístup ke`UseActiveDirectory` službě Active <xref:System.ServiceModel.NetMsmqBinding> Directory (vlastnost musí `true`být nastavena na hodnotu) a lze <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> ji <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>použít s oběma i.  
  
#### <a name="none-protection-level"></a>Žádná úroveň ochrany  
 To je implicitní, pokud <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> je nastavena na <xref:System.Net.Security.ProtectionLevel.None>. Nejedná se o platnou hodnotu pro žádné jiné režimy ověřování.  
  
> [!NOTE]
> Pokud je zpráva služby MSMQ podepsaná, služba MSMQ ověří, zda je zpráva podepsána připojeným certifikátem (interní nebo externí) nezávisle na stavu fronty, tj. v ověřované frontě.  
  
### <a name="msmq-encryption-algorithm"></a>Šifrovací algoritmus služby MSMQ  
 Šifrovací algoritmus Určuje algoritmus, který se použije k šifrování zprávy služby MSMQ na lince. Tato vlastnost se používá pouze v <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> případě, že <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>je nastavena na.  
  
 Podporované algoritmy jsou `RC4Stream` a `AES` a výchozí hodnota je `RC4Stream`.  
  
 `AES` Algoritmus lze použít pouze v případě, že je v počítači nainstalováno rozhraní MSMQ 4,0. Kromě toho musí být cílová fronta taky hostovaná ve službě MSMQ 4,0.  
  
### <a name="msmq-hash-algorithm"></a>Algoritmus hash služby MSMQ  
 Algoritmus hash určuje algoritmus použitý k vytvoření digitálního podpisu zprávy služby MSMQ. Správce fronty příjmu používá stejný algoritmus k ověření zprávy služby MSMQ. Tato vlastnost se používá pouze v <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> případě, že <xref:System.Net.Security.ProtectionLevel.Sign> je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>nastavena na nebo.  
  
 Podporované algoritmy jsou `MD5`, `SHA1`, `SHA256`a. `SHA512` Výchozí hodnota je `SHA1`.

 Microsoft doporučuje SHA256 nebo lepší vzhledem k problémům s kolize MD5/SHA1.
  
## <a name="see-also"></a>Viz také:

- [Přehled front](queues-overview.md)
- [Koncepty zabezpečení](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
