---
title: Práce s certifikáty
description: Přečtěte si o funkcích digitálního certifikátu X. 509 a o tom, jak je používat ve službě WCF. Zdroje informací v tomto článku vám můžou podrobněji vysvětlit tyto koncepty.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
ms.openlocfilehash: 8090e84b33e2a6f442d387c7012e6ccdc2900dd1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246399"
---
# <a name="working-with-certificates"></a>Práce s certifikáty

Pro programové zabezpečení služby Windows Communication Foundation (WCF) se běžně používají digitální certifikáty X. 509 k ověřování klientů a serverů, k šifrování a digitálnímu podepisování zpráv. Toto téma stručně vysvětluje funkce digitálního certifikátu X. 509 a jejich použití ve službě WCF a obsahuje odkazy na témata, která tyto koncepce vysvětlují, nebo které ukazují, jak provádět běžné úlohy pomocí WCF a certifikátů.

V krátké době je digitální certifikát součástí *infrastruktury veřejných klíčů* (PKI), která je systémem digitálních certifikátů, certifikačních autorit a dalších registračních autorit, které ověřují a ověřují platnost všech smluvních stran zapojených do elektronické transakce pomocí kryptografie s veřejným klíčem. Certifikační autorita vystavuje certifikáty a každý certifikát obsahuje sadu polí, která obsahují data, jako je například *Předmět* (entita, na kterou je certifikát vystavený), data platnosti (Pokud je certifikát platný), Vystavitel (entita, která certifikát vystavila), a veřejný klíč. V rámci WCF je každá z těchto vlastností zpracována jako a <xref:System.IdentityModel.Claims.Claim> každá deklarace je dále rozdělena do dvou typů: identita a právo. Další informace o certifikátech X. 509 najdete v tématu [certifikáty s veřejným klíčem x. 509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Další informace o deklaracích identity a autorizaci v WCF najdete v tématu [Správa deklarací identity a autorizace pomocí modelu identity](managing-claims-and-authorization-with-the-identity-model.md). Další informace o implementaci infrastruktury veřejných klíčů najdete v tématu [Infrastruktura veřejných klíčů rozlehlé sítě s Windows serverem 2012 R2 Active Directory Certificate Services](https://docs.microsoft.com/archive/blogs/yungchou/enterprise-pki-with-windows-server-2012-r2-active-directory-certificate-services-part-1-of-2).

Primární funkcí certifikátu je ověření identity vlastníka certifikátu ostatním uživatelům. Certifikát obsahuje *veřejný klíč* vlastníka, zatímco vlastník zachovává privátní klíč. Veřejný klíč lze použít k šifrování zpráv odesílaných vlastníkovi certifikátu. Pouze vlastník má přístup k privátnímu klíči, takže pouze vlastník může tyto zprávy dešifrovat.

Certifikáty musí vystavit certifikační autorita, což je často Vystavitel certifikátů třetích stran. V doméně systému Windows je k dispozici certifikační autorita, která se dá použít k vystavování certifikátů počítačům v doméně.

## <a name="viewing-certificates"></a>Zobrazení certifikátů

Pro práci s certifikáty je často nutné je zobrazit a prozkoumávat jejich vlastnosti. To se dá snadno udělat pomocí nástroje pro modul snap-in konzoly MMC (Microsoft Management Console). Další informace najdete v tématu [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md).

## <a name="certificate-stores"></a>Úložiště certifikátů

Certifikáty se nacházejí v úložištích. Existují dvě hlavní umístění úložiště, která jsou dále rozdělena do dílčích obchodů. Pokud jste správcem počítače, můžete si prohlédnout hlavní úložiště pomocí nástroje pro modul snap-in konzoly MMC. Uživatelé bez oprávnění správce můžou zobrazit jenom úložiště aktuálního uživatele.

- **Úložiště v místním počítači**. Obsahuje certifikáty, ke kterým přistupovaly počítačové procesy, jako je ASP.NET. Toto umístění použijte k ukládání certifikátů, které ověřují server pro klienty.

- **Aktuální uživatelské úložiště** Interaktivní aplikace obvykle umísťují certifikáty pro aktuálního uživatele počítače. Pokud vytváříte klientskou aplikaci, je to místo, kde obvykle umístíte certifikáty, které ověřují uživatele pro službu.

Tyto dva obchody jsou dále rozděleny do dílčích obchodů. Nejdůležitější z nich při programování v rámci WCF zahrnují:

- **Důvěryhodné kořenové certifikační autority**. Certifikáty v tomto úložišti můžete použít k vytvoření řetězce certifikátů, které se dají trasovat zpátky do certifikátu certifikační autority v tomto úložišti.

  > [!IMPORTANT]
  > Místní počítač implicitně důvěřuje jakémukoli certifikátu umístěnému v tomto úložišti, a to i v případě, že certifikát nepochází od důvěryhodné certifikační autority třetí strany. Z tohoto důvodu neumísťujte do tohoto úložiště žádné certifikáty, pokud plně nedůvěřujete vystaviteli a pochopíte důsledky.

- **Osobní**. Toto úložiště se používá pro certifikáty přidružené k uživateli počítače. Toto úložiště se obvykle používá pro certifikáty vydané jedním z certifikátů certifikační autority, které se nacházejí v úložišti důvěryhodných kořenových certifikačních autorit. Případně může certifikát, který tady najde, být vystavený svým držitelem a důvěryhodný pro aplikaci.

Další informace o úložištích certifikátů najdete v tématu [úložiště certifikátů](/windows/desktop/secauthn/certificate-stores).

### <a name="selecting-a-store"></a>Výběr úložiště

Výběr místa uložení certifikátu závisí na tom, jak a kdy se služba nebo klient spouští. Platí následující obecná pravidla:

- Pokud je služba WCF hostovaná ve službě systému Windows, použijte úložiště **místního počítače** . Mějte na paměti, že k instalaci certifikátů do úložiště místního počítače jsou nutná oprávnění správce.

- Pokud je služba nebo klient aplikace, která běží pod uživatelským účtem, použijte úložiště **aktuálního uživatele** .

### <a name="accessing-stores"></a>Přístup k obchodům

Úložiště jsou chráněná pomocí seznamů řízení přístupu (ACL), stejně jako složky v počítači. Při vytváření služby hostované službou Internetová informační služba (IIS) se proces ASP.NET spouští pod účtem ASP.NET. Tento účet musí mít přístup k úložišti, které obsahuje certifikáty, které služba používá. Každé z hlavních úložišť je chráněno pomocí výchozího seznamu přístupu, ale seznamy lze upravit. Pokud vytvoříte samostatnou roli pro přístup k úložišti, musíte této roli udělit oprávnění k přístupu. Informace o tom, jak upravit seznam přístupu pomocí nástroje WinHttpCertConfig.exe, najdete v tématu [Postupy: vytváření dočasných certifikátů pro použití během vývoje](how-to-create-temporary-certificates-for-use-during-development.md).

## <a name="chain-trust-and-certificate-authorities"></a>Důvěryhodnost řetězení a certifikační autority

Certifikáty se vytvářejí v hierarchii, kde je každý jednotlivý certifikát propojený s certifikační autoritou, která certifikát vystavila. Tento odkaz je na certifikát certifikační autority. Certifikát certifikační autority potom odkazuje na certifikační autoritu, která vydala certifikát původní certifikační autority. Tento proces se opakuje, dokud nedosáhnete certifikátu kořenové certifikační autority. Certifikát kořenové certifikační autority je v podstatě důvěryhodný.

Digitální certifikáty slouží k ověřování entity, které se spoléhají na tuto hierarchii, která se označuje také jako *řetěz důvěryhodnosti*. Řetěz certifikátů můžete zobrazit pomocí modulu snap-in konzoly MMC tak, že dvakrát kliknete na libovolný certifikát a potom kliknete na kartu **cesta k certifikátu** . Další informace o importu řetězů certifikátů certifikační autority najdete v tématu [Postupy: určení řetězu certifikátů certifikační autority používaného k ověřování podpisů](specify-the-certificate-authority-chain-verify-signatures-wcf.md).

> [!NOTE]
> V úložišti certifikátů důvěryhodné kořenové certifikační autority je možné určit každého vystavitele důvěryhodnou kořenovou autoritu tím, že umístíte certifikát vystavitele.

### <a name="disabling-chain-trust"></a>Zakázání vztahu důvěryhodnosti řetězu

Při vytváření nové služby můžete použít certifikát, který není vydán důvěryhodným kořenovým certifikátem, nebo samotný vydávající certifikát nemusí být v úložišti důvěryhodných kořenových certifikačních autorit. Pouze pro účely vývoje můžete dočasně zakázat mechanismus, který kontroluje řetěz důvěryhodnosti pro certifikát. Chcete-li to provést, nastavte `CertificateValidationMode` vlastnost na hodnotu `PeerTrust` nebo `PeerOrChainTrust` . V obou režimech se určuje, že certifikát může být vystavený svým držitelem (vztah důvěryhodnosti partnera) nebo část řetězu důvěryhodnosti. Vlastnost lze nastavit na kterékoli z následujících tříd.

|Třída|Vlastnost|
|-----------|--------------|
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|

Vlastnost můžete také nastavit pomocí konfigurace. K určení režimu ověřování se používají následující elementy:

- [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)

- [\<peerAuthentication>](../../configure-apps/file-schema/wcf/peerauthentication-element.md)

- [\<messageSenderAuthentication>](../../configure-apps/file-schema/wcf/messagesenderauthentication-element.md)

## <a name="custom-authentication"></a>Vlastní ověřování

`CertificateValidationMode`Vlastnost také umožňuje upravit způsob ověřování certifikátů. Ve výchozím nastavení je úroveň nastavena na `ChainTrust` . Chcete-li použít <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> hodnotu, je nutné také nastavit `CustomCertificateValidatorType` atribut na sestavení a typ použitý k ověření certifikátu. Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.

Při vytváření vlastního ověřovatele je nejdůležitější metodou přepsání <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metoda. Příklad vlastního ověřování najdete v ukázce ověřování [certifikátů X. 509](../samples/x-509-certificate-validator.md) . Další informace najdete v tématu [vlastní ověření přihlašovacích údajů a přihlašovacích údajů](../extending/custom-credential-and-credential-validation.md).

## <a name="using-the-powershell-new-selfsignedcertificate-cmdlet-to-build-a-certificate-chain"></a>Vytvoření řetězu certifikátů pomocí rutiny New-SelfSignedCertificate prostředí PowerShell

Rutina New-SelfSignedCertificate pro PowerShell vytváří páry certifikátů X. 509 a privátního klíče/veřejného klíče. Privátní klíč můžete uložit na disk a pak ho použít k vystavení a podepsání nových certifikátů, což simuluje hierarchii zřetězených certifikátů. Rutina je určena pouze pro použití jako pomůcka při vývoji služeb a neměla by být používána k vytváření certifikátů pro skutečné nasazení. Při vývoji služby WCF použijte následující postup k vytvoření řetězu důvěry pomocí rutiny New-SelfSignedCertificate.

#### <a name="to-build-a-chain-of-trust-with-the-new-selfsignedcertificate-cmdlet"></a>Sestavení řetězu vztahu důvěryhodnosti pomocí rutiny New-SelfSignedCertificate

1. Pomocí rutiny New-SelfSignedCertificate vytvořte dočasný certifikát kořenové autority (s podpisem držitele). Uložte privátní klíč na disk.

2. Pomocí nového certifikátu vydejte jiný certifikát, který obsahuje veřejný klíč.

3. Importujte certifikát kořenové autority do úložiště důvěryhodných kořenových certifikačních autorit.

4. Podrobné pokyny najdete v tématu [Postup: vytváření dočasných certifikátů pro použití během vývoje](how-to-create-temporary-certificates-for-use-during-development.md).

## <a name="which-certificate-to-use"></a>Který certifikát se má použít?

Nejčastější dotazy k certifikátům, které certifikát použít a proč. Odpověď závisí na tom, jestli programujete klienta nebo službu. Následující informace obsahují obecný pokyn a nejedná se o vyčerpávající odpověď na tyto otázky.

### <a name="service-certificates"></a>Certifikáty služby

Certifikáty služeb mají primární úlohu ověřování serveru pro klienty. Jedna z počátečních kontrol, kdy klient ověřuje server, je porovnat hodnotu pole **subjekt** s IDENTIFIKÁTORem URI, který se používá ke kontaktování služby: DNS obou musí odpovídat. Například pokud je identifikátor URI služby, `http://www.contoso.com/endpoint/` pak pole **subjektu** musí obsahovat také hodnotu `www.contoso.com` .

Všimněte si, že pole může obsahovat několik hodnot, každý s předponou inicializace k označení hodnoty. Nejčastěji je inicializace "CN" pro běžný název, například `CN = www.contoso.com` . Je také možné, že pole **subjekt** bude prázdné. v takovém případě může pole **alternativní název subjektu** obsahovat hodnotu **názvu DNS** .

Všimněte si také, že hodnota pole **zamýšlené účely** certifikátu by měla obsahovat odpovídající hodnotu, například "ověřování serveru" nebo "ověřování klientů".

### <a name="client-certificates"></a>Klientské certifikáty

Klientské certifikáty nejsou většinou vydávány certifikační autoritou jiného výrobce. Místo toho osobní úložiště aktuálního umístění uživatele obvykle obsahuje certifikáty, které jsou umístěny v kořenové autoritě, s určeným účelem "ověřování klienta". Klient může takový certifikát použít, pokud je vyžadováno vzájemné ověření.

## <a name="online-revocation-and-offline-revocation"></a>Online odvolání a odvolání offline

### <a name="certificate-validity"></a>Platnost certifikátu

Každý certifikát je platný jenom po určitou dobu, která se nazývá *období platnosti*. Období platnosti je definováno poli **platné od** a **platné k** certifikátu X. 509. Při ověřování se certifikát kontroluje, aby se zjistilo, jestli je certifikát stále v období platnosti.

### <a name="certificate-revocation-list"></a>Seznam odvolaných certifikátů

Certifikační autorita může během období platnosti certifikát odvolat. K tomu může dojít z mnoha důvodů, jako je například ohrožení soukromého klíče certifikátu.

V takovém případě jsou všechny řetězy od odvolaného certifikátu také neplatné a během ověřovacích procedur nejsou důvěryhodné. Chcete-li zjistit, které certifikáty byly odvolány, každý Vystavitel zveřejňuje *seznam odvolaných certifikátů* s časovým razítkem (CRL). Seznam lze kontrolovat buď pomocí online odvolání, nebo pomocí offline odvolání nastavením `RevocationMode` vlastnosti nebo v `DefaultRevocationMode` následujících třídách na jednu z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnot výčtu: <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> , <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> , <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třídy. Výchozí hodnota pro všechny vlastnosti je `Online` .

Můžete také nastavit režim v konfiguraci pomocí `revocationMode` atributu [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (z [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) ) i [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (z [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) ).

## <a name="the-setcertificate-method"></a>Metoda SetCertificate

V rámci WCF musíte často zadat certifikát nebo sadu certifikátů, které služba nebo klient používá k ověřování, šifrování nebo digitálnímu podepisování zprávy. To můžete provést programově pomocí `SetCertificate` metody různých tříd, které reprezentují certifikáty X. 509. Následující třídy používají `SetCertificate` metodu k určení certifikátu.

|Třída|Metoda|
|-----------|------------|
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|

`SetCertificate`Metoda funguje podle určení umístění úložiště a úložiště, typu "Find" ( `x509FindType` parametr), který určuje pole certifikátu a hodnotu, která se má najít v poli. Například následující kód vytvoří <xref:System.ServiceModel.ServiceHost> instanci a nastaví certifikát služby použitý k ověření služby pro klienty s `SetCertificate` metodou.

[!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
[!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]

### <a name="multiple-certificates-with-the-same-value"></a>Víc certifikátů se stejnou hodnotou

Úložiště může obsahovat více certifikátů se stejným názvem subjektu. To znamená, že pokud určíte, že `x509FindType` je <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> nebo a <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName> více než jeden certifikát má stejnou hodnotu, je vyvolána výjimka, protože neexistuje způsob, jak rozlišovat požadovaný certifikát. Můžete to zmírnit nastavením na `x509FindType` <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> . Pole kryptografický otisk obsahuje jedinečnou hodnotu, která se dá použít k vyhledání konkrétního certifikátu v úložišti. Má však svou vlastní nevýhodu: Pokud je certifikát odvolán nebo obnoven, `SetCertificate` metoda se nezdařila, protože kryptografický otisk je také pryč. Nebo, pokud certifikát již není platný, ověřování se nezdařilo. Způsob, jak to zmírnit, je nastavení `x590FindType` parametru na <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> a zadání názvu vystavitele. Pokud není vyžadován žádný konkrétní Vydavatel, můžete také nastavit jednu z dalších <xref:System.Security.Cryptography.X509Certificates.X509FindType> hodnot výčtu, například <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid> .

## <a name="certificates-in-configuration"></a>Certifikáty v konfiguraci

Můžete také nastavit certifikáty pomocí konfigurace. Pokud vytváříte službu, jsou pověření včetně certifikátů uvedena v části [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) . Při programování klienta jsou certifikáty zadány v části [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) .

## <a name="mapping-a-certificate-to-a-user-account"></a>Mapování certifikátu na uživatelský účet

Funkce služby IIS a Active Directory umožňuje mapovat certifikát na uživatelský účet systému Windows. Další informace o této funkci najdete v tématu [mapování certifikátů na uživatelské účty](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc736706(v=ws.10)).

Další informace o použití mapování služby Active Directory najdete v tématu [mapování klientských certifikátů pomocí mapování adresářových služeb](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc758484(v=ws.10)).

Když je tato funkce povolená, můžete nastavit <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> vlastnost <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy na `true` . V části konfigurace můžete nastavit `mapClientCertificateToWindowsAccount` atribut [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) prvku na `true` , jak je znázorněno v následujícím kódu.

```xml
<serviceBehaviors>
 <behavior name="MappingBehavior">
  <serviceCredentials>
   <clientCertificate>
    <authentication certificateValidationMode="None" mapClientCertificateToWindowsAccount="true" />
   </clientCertificate>
  </serviceCredentials>
 </behavior>
</serviceBehaviors>
```

Mapování certifikátu X. 509 na token, který představuje uživatelský účet systému Windows, se považuje za zvýšení oprávnění, protože po namapování se token systému Windows dá použít k získání přístupu k chráněným prostředkům. Proto zásady domény před mapováním vyžadují, aby byl certifikát X. 509 dodržen zásadou. Balíček zabezpečení *Schannel* tento požadavek vynutil.

Pokud používáte .NET Framework 3,5 nebo novější verze, WCF zajišťuje, že certifikát bude v souladu se zásadami domény předtím, než se namapuje na účet systému Windows.

V první verzi služby WCF se mapování provádí bez konzultace s doménovou zásadou. Proto je možné, že starší aplikace, které se používají při práci v rámci první verze, selžou, pokud je mapování povolené a certifikát X. 509 nevyhovuje zásadám domény.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Security>
- <xref:System.ServiceModel>
- <xref:System.Security.Cryptography.X509Certificates.X509FindType>
- [Zabezpečení služeb a klientů](securing-services-and-clients.md)
