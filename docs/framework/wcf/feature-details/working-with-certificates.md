---
title: Práce s certifikáty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
ms.openlocfilehash: 1b4451b11fed2fd138985824d5f139e192c51f45
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331712"
---
# <a name="working-with-certificates"></a>Práce s certifikáty
Programování zabezpečení Windows Communication Foundation (WCF), digitální certifikáty X.509 běžně slouží k ověřování klientů a serverů, šifrování a digitálnímu podepisování zpráv. V tomto tématu stručně popisuje funkce digitální certifikát X.509 a jak je používat v WCF a obsahuje odkazy na témata, která popisují tyto koncepty další nebo, která ukazují, jak provádět běžné úlohy pomocí WCF a certifikáty.  
  
 Stručně řečeno, digitálního certifikátu je součástí *infrastruktury veřejných klíčů* (PKI), což je systém digitální certifikáty, certifikační autority a další registrační autority, které ověřují platnost Každá ze smluvních stran součástí elektronické transakce pomocí kryptografii využívající veřejného klíče. Certifikační autorita vydává certifikáty a každý certifikát má sadu polí, které obsahují data, jako například *subjektu* (entity, ke kterému je vydaný certifikát), data platnosti (Pokud je certifikát platný), Vystavitel () entity, která vydala certifikát) a veřejný klíč. Ve službě WCF, každá z těchto vlastností je zpracován jako <xref:System.IdentityModel.Claims.Claim>, a každá deklarace je dále rozdělen do dvou typů: identity a doprava. Další informace o X.509 certifikátů najdete v části [veřejný klíč certifikátů X.509](https://go.microsoft.com/fwlink/?LinkId=209952). Další informace o deklaracích identity a autorizace ve WCF najdete v části [správa deklarací identity a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md). Další informace o implementaci infrastruktury veřejných KLÍČŮ najdete v tématu [systému Windows Server 2008 R2 - Certificate Services](https://go.microsoft.com/fwlink/?LinkId=209949).  
  
 Primární funkce certifikát je k ověření identity vlastníka certifikátu ostatním uživatelům. Certifikát obsahuje *veřejný klíč* vlastníka, zatímco vlastníkem ponechá privátní klíč. Veřejný klíč slouží k šifrování zpráv, pošle se vlastníkovi certifikátu. Pouze vlastník má přístup k privátnímu klíči, takže pouze vlastník může dešifrovat tyto zprávy.  
  
 Certifikáty musí být vystavené certifikační autority, což se často stává třetích stran vystavitelů certifikátů. V doméně Windows je součástí certifikační autority, který slouží k vydávání certifikátů pro počítače v doméně.  
  
## <a name="viewing-certificates"></a>Zobrazení certifikátů  
 Pro práci s certifikáty, je často potřeba je zobrazit a prozkoumat jejich vlastnosti. Snadno to provádí pomocí modulu snap-in nástroje Microsoft Management Console (MMC). Další informace najdete v tématu [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="certificate-stores"></a>Úložiště certifikátů  
 Certifikáty se nacházejí v úložištích. Dvěma umístěními velké úložiště existují, které se dále dělí do dílčí úložišť. Pokud jste správce v počítači, se zobrazí oba hlavní úložiště pomocí nástroje modulu snap-in konzoly MMC. Bez správci mohou zobrazit pouze aktuální úložiště uživatele.  
  
-   **Úložiště místního počítače**. Tato položka obsahuje certifikáty přistupuje počítač procesy, jako například [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Toto umístění slouží k ukládání certifikátů, které ověření serveru vůči klientům.  
  
-   **Úložiště pro aktuálního uživatele**. Interaktivní aplikace obvykle umístit certifikáty pro aktuálního uživatele počítače. Pokud vytvoříte klientskou aplikaci, je obvykle umístění certifikáty, které se ověřují uživatele ke službě.  
  
 Tyto dvě úložiště se dále dělí do dílčí úložišť. Nejdůležitější z těchto při programování s použitím technologie WCF patří:  
  
-   **Důvěryhodné kořenové certifikační autority**. Certifikáty můžete použít v tomto úložišti vytvořit řetěz certifikátů, které lze sledovat zpět k certifikátu certifikačního úřadu v tomto úložišti.  
  
    > [!IMPORTANT]
    >  Místní počítač některý z certifikátů umístěny v tomto úložišti implicitně důvěřuje i v případě, že certifikát nepochází od důvěryhodné certifikační autority. Z tohoto důvodu Neumísťujte některý z certifikátů do tohoto úložiště není-li plně důvěřovat vystavitele a nerozumíte jeho následkům.  
  
-   **Osobní**. Toto úložiště se používá pro certifikáty, které jsou spojeny s konkrétním uživatelem počítače. Toto úložiště se obvykle používá pro certifikáty vydané certifikáty certifikační autority v úložišti Důvěryhodné kořenové certifikační autority. Certifikát, najdete tady také může samostatně vydané a důvěryhodné aplikace.  
  
 Další informace o úložištích certifikátů najdete v tématu [úložišť certifikátů](/windows/desktop/secauthn/certificate-stores).  
  
### <a name="selecting-a-store"></a>Výběr Store  
 Výběr umístění pro uložení certifikátu závisí jak a kdy bude spuštěna služba nebo klient. Platí následující obecná pravidla:  
  
-   Pokud je služba WCF hostovaná používá službu Windows **místního počítače** ukládat. Všimněte si, že jsou nutná oprávnění správce k instalaci certifikátů do úložiště místního počítače.  
  
-   Pokud služba nebo klient je aplikace, na kterém běží pod účtem uživatele, použijte **aktuálního uživatele** ukládat.  
  
### <a name="accessing-stores"></a>Přístup k úložišti  
 Úložiště jsou chráněné pomocí seznamů řízení přístupu (ACL), podobně jako složky v počítači. Při vytváření služby podle Internetové informační služby (IIS) hostovaných [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proces běží pod [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účtu. Služba se používá, musí mít přístup k úložišti, který obsahuje certifikáty. Všechny hlavní obchody je pak chráněn rozhraním výchozí seznam, ale seznamy je možné upravit. Pokud vytvoříte samostatné role pro přístup k úložišti, je nutné udělit přístupová oprávnění této role. Zjistěte, jak upravit seznam přístupu pomocí nástroje WinHttpCertConfig.exe, najdete v článku [jak: Vytváření dočasných certifikátů pro použití během vývoje](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md). Další informace o používání certifikátů klienta se službou IIS najdete v tématu [volání webové služby pomocí klientského certifikátu pro ověřování ve webové aplikaci ASP.NET](https://go.microsoft.com/fwlink/?LinkId=88914).  
  
## <a name="chain-trust-and-certificate-authorities"></a>Řetězce důvěryhodnosti a certifikační autority  
 Certifikáty jsou vytvořeny v hierarchii, kde je každý jednotlivý certifikát certifikační Autority, která vydala certifikát propojen. Tento odkaz je certifikát Certifikační autority. Certifikát Certifikační autority pak odkazy na certifikační Autoritu, která vydala certifikát původní CA. Tento postup se opakuje, dokud nenastane certifikát kořenové certifikační Autority. Certifikát kořenové certifikační Autority je ze své podstaty důvěryhodný.  
  
 Digitální certifikáty se používají k ověřování entity spoléhání se na tuto hierarchii, také nazývané *řetězu certifikátů*. Můžete zobrazit řetězec některý z certifikátů pomocí modulu snap-in konzoly MMC poklepáním na některý z certifikátů a pak kliknete **cesta k certifikátu** kartu. Další informace o importu řetězy certifikátů certifikační autority najdete v tématu [jak: Zadejte řetězu certifikátů certifikační autority certifikátu používaného k ověřování podpisů](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Všechny vystavitele lze označit důvěryhodné kořenové autority tak, že vystavitele certifikátu v úložišti certifikátů důvěryhodných kořenových autorit.  
  
### <a name="disabling-chain-trust"></a>Zakázání řetězce důvěryhodnosti  
 Při vytváření nové služby, pravděpodobně používáte certifikát, který není vystavený důvěryhodný kořenový certifikát, nebo vlastní certifikát vydávající nemusí být v úložišti Důvěryhodné kořenové certifikační autority. Pro účely vývoje můžete dočasně zakázat mechanismus, který kontroluje, řetěz certifikátů pro certifikát. Chcete-li to provést, nastavte `CertificateValidationMode` vlastnost buď `PeerTrust` nebo `PeerOrChainTrust`. Režim určuje, že certifikát můžete buď samostatně vydat (peer vztahu důvěryhodnosti) nebo jeho část řetěz certifikátů. Nastavte vlastnost na žádném z následujících tříd.  
  
|Třída|Vlastnost|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 Můžete také nastavit vlastnost pomocí konfigurace. Tyto prvky se používají k určení režimu ověřování:  
  
-   [\<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>Vlastní ověřování  
 `CertificateValidationMode` Vlastnost také umožňuje přizpůsobit způsob ověřování certifikátů. Ve výchozím nastavení, úroveň je nastavena `ChainTrust`. Použít <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> hodnotu, je nutné nastavit také `CustomCertificateValidatorType` atribut na sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
 Při vytváření vlastní ověřovací data, je nejdůležitější metodu pro přepsání <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metody. Příklad vlastní ověřování, najdete v článku [validátor certifikátu X.509](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) vzorku. Další informace najdete v tématu [vlastní pověření a ověřování pověření](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## <a name="using-the-powershell-new-selfsignedcertificate-cmdlet-to-build-a-certificate-chain"></a>Pomocí rutiny Powershellu New-SelfSignedCertificate Sestavit řetěz certifikátů  
 Rutiny Powershellu New-SelfSignedCertificate vytvoří privátní klíče párů klíč/veřejný a certifikáty X.509. Můžete uložit privátní klíč, aby na disku a použít ho k vystavení a podepsat nové certifikáty, proto budete jen simulovat hierarchii zřetězené certifikátů. Rutina je určena pro použití pouze jako vodítko při vývoji služeb a byste nikdy neměli používat k vytvoření certifikátů pro skutečné nasazení. Při vývoji služeb WCF, sestavit řetěz certifikátů pomocí rutiny New-SelfSignedCertificate pomocí následujících kroků.  
  
#### <a name="to-build-a-chain-of-trust-with-the-new-selfsignedcertificate-cmdlet"></a>Sestavit řetěz certifikátů pomocí rutiny New-SelfSignedCertificate  
  
1. Vytvořte dočasný kořenové autoritě (certifikát podepsaný svým držitelem) pomocí rutiny New-SelfSignedCertificate. Privátní klíč uložte na disk.  
  
2. Použití nového certifikátu k vystavení dalšího certifikátu, který obsahuje veřejný klíč.  
  
3. Kořenový certifikát autority naimportujte do úložiště Důvěryhodné kořenové certifikační autority.  
  
4. Podrobné pokyny najdete v tématu [jak: Vytváření dočasných certifikátů pro použití během vývoje](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
## <a name="which-certificate-to-use"></a>Který certifikát se má použít?  
 Běžné dotazy týkající se certifikátů jsou který certifikát se má použít a proč. Odpověď závisí na tom, jestli jsou programování klienta nebo služby. Tyto informace obsahuje obecných pokynů a není vyčerpávající odpovědi na tyto otázky.  
  
### <a name="service-certificates"></a>Certifikáty služeb  
 Certifikáty služby mají primární úlohy ověřování serveru vůči klientům. Jedním z úvodních kontrol, když se klient ověřuje server je porovnat hodnotu **subjektu** pole na identifikátor URI (Uniform Resource) používá ke kontaktování služby: DNS obou se musí shodovat. Například, pokud je identifikátor URI služby `http://www.contoso.com/endpoint/` pak bude **subjektu** pole musí obsahovat také hodnota `www.contoso.com`.  
  
 Všimněte si, že pole může obsahovat několik hodnot, každý s předponou inicializace k označení hodnoty. Nejčastěji inicializace je "CN" pro běžný název, například `CN = www.contoso.com`. Je také možné, **subjektu** pole jako prázdné, v takovém případě **alternativní název předmětu** pole může obsahovat **název DNS** hodnotu.  
  
 Všimněte si také hodnotu **zamýšlené účely** pole certifikátu by měl obsahovat správnou hodnotu, jako je například "Ověřování serveru" nebo "Ověření klienta".  
  
### <a name="client-certificates"></a>Klientské certifikáty  
 Klientské certifikáty nejsou obvykle vydaný certifikační autoritou. Místo toho osobním úložišti aktuální polohu uživatele obvykle obsahuje certifikáty umísťují kořenovou autoritou, zamýšlený účel "Ověření klienta". Klienta můžete použít tento certifikát, pokud je nutné použít vzájemného ověřování.  
  
## <a name="online-revocation-and-offline-revocation"></a>Odvolání online a Offline odvolání  
  
### <a name="certificate-validity"></a>Platnost certifikátu.  
 Každý certifikát je platný pouze pro daný časový úsek, volá se, *období platnosti*. Doba platnosti je definován **platné od** a **platné do** pole certifikátu X.509. Během ověřování je certifikát zkontrolována k určení, zda certifikát je stále v rámci doby platnosti.  
  
### <a name="certificate-revocation-list"></a>Seznam odvolaných certifikátů  
 Kdykoli během doby platnosti certifikační autority můžete odvolat certifikát. Tato situace může nastat z mnoha důvodů, jako je například ohrožení zabezpečení privátní klíč certifikátu.  
  
 V takovém případě všechny řetězce, které sestup od odvolaný certifikát jsou neplatné a nejsou důvěryhodné během postupů ověřování. Chcete-li zjistit, které certifikáty byly odvolány, každý Vystavitel publikuje čas a datum razítkem *seznam odvolaných certifikátů* (CRL). Seznamu můžete zkontrolovat pomocí odvolání online nebo offline odvolání nastavením `RevocationMode` nebo `DefaultRevocationMode` vlastnost na jednu z následujících tříd <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnot výčtu: <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třídy. Výchozí hodnota pro všechny vlastnosti je `Online`.  
  
 Můžete také nastavit režim konfigurace pomocí `revocationMode` atribut obou [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (nástroje [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) a [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (nástroje [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).  
  
## <a name="the-setcertificate-method"></a>SetCertificate – metoda  
 Ve službě WCF často musíte zadat certifikát nebo nastavit certifikátů službu nebo klienta je nutné použít k ověření, šifrování nebo podepsání zprávy. Můžete to provést prostřednictvím kódu programu pomocí `SetCertificate` metoda různých tříd, které představují certifikáty X.509. Následující třídy použijte `SetCertificate` metoda zadat certifikát.  
  
|Třída|Metoda|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 `SetCertificate` Metoda funguje tak, že označující umístění úložiště a úložiště typu "najít" (`x509FindType` parametr), který určuje pole certifikátu a hodnotu k vyhledání v poli. Například následující kód vytvoří <xref:System.ServiceModel.ServiceHost> instance a certifikát služby používaný k ověření služby klientů, kteří se nastaví `SetCertificate` metoda.  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>Více certifikátů se stejnou hodnotou  
 Úložiště může obsahovat více certifikátů se stejným názvem subjektu. To znamená, že pokud určíte, `x509FindType` je <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> nebo <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>a více než jeden certifikát má stejnou hodnotu, je vyvolána výjimka, protože neexistuje žádný způsob k rozlišení, který certifikát se vyžaduje. To můžete zmírnit tím, že nastavíte `x509FindType` k <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. Kryptografický otisk pole obsahuje jedinečnou hodnotu, která slouží k vyhledání konkrétního certifikátu v úložišti. Tato akce však nemá vlastní nevýhodou: Pokud je certifikát odvolán nebo obnovení `SetCertificate` metoda selže, protože kryptografický otisk je pryč. Nebo, pokud již není platný certifikát, ověření se nezdaří. Způsob, jak tento problém zmírnit, je nastavit `x590FindType` parametr <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> a zadejte název vystavitele. Pokud žádný konkrétní vydavatel je potřeba, můžete také nastavit jednoho z jiných <xref:System.Security.Cryptography.X509Certificates.X509FindType> hodnot výčtu, například <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.  
  
## <a name="certificates-in-configuration"></a>Certifikáty v konfiguraci  
 Můžete také nastavit certifikáty pomocí konfigurace. Při vytváření služby, přihlašovací údaje, včetně certifikátů jsou specifikovány pod [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Při programování klienta, certifikáty jsou určené v rámci [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>Mapování certifikátu s uživatelskými účty  
 Funkce služby IIS a služby Active Directory je schopnost mapování certifikátu uživatelský účet Windows. Další informace o funkci najdete v tématu [mapování certifikátů uživatelským účtům](https://go.microsoft.com/fwlink/?LinkId=88917).  
  
 Další informace o používání služby Active Directory mapování najdete v tématu [mapování klientských certifikátů pomocí mapování adresářových služeb](https://go.microsoft.com/fwlink/?LinkId=88918).  
  
 Díky této funkci povoleny, můžete nastavit <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> vlastnost <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídu `true`. V konfiguraci, můžete nastavit `mapClientCertificateToWindowsAccount` atribut [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element `true`, jak je znázorněno v následujícím kódu.  
  
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
  
 Mapování certifikátu X.509 na token, který představuje uživatelský účet Windows se považuje za zvýšení úrovně oprávnění proto, že jakmile mapován, Windows token je možné získat přístup k chráněným prostředkům. Proto se zásada domény vyžaduje certifikát X.509 dodržovat její zásady před mapování. *SChannel* balíček zabezpečení vynucuje tento požadavek.  
  
 Při použití [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] nebo později, WCF zajišťuje certifikát odpovídá zásada domény předtím, než je namapován na účet Windows.  
  
 V první verzi WCF mapování se provádí bez konzultace zásada domény. Proto je možné, že starší aplikace, které používají k práci při spuštění v prvním vydání se nepovede, pokud je povoleno mapování a certifikát X.509 nesplňuje zásady domény.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Security>
- <xref:System.ServiceModel>
- <xref:System.Security.Cryptography.X509Certificates.X509FindType>
- [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
