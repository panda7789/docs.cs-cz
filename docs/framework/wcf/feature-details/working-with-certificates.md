---
title: Práce s certifikáty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
ms.openlocfilehash: f5566eacaabb5d3eb5579d015fad8149a2ed4f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-certificates"></a>Práce s certifikáty
Do programu zabezpečení Windows Communication Foundation (WCF), digitální certifikáty X.509 běžně se používají k ověřování klientů a serverů, šifrování a digitálnímu podepisování zpráv. Toto téma stručně popisuje funkce digitální certifikát X.509 a jejich použití v WCF a obsahuje odkazy na témata, která popisují tyto další koncepty nebo která ukazují, jak provádět běžné úlohy pomocí WCF a certifikáty.  
  
 Stručně řečeno, digitální certifikát je součástí *infrastruktury veřejných klíčů* (PKI), který je systém digitální certifikáty, certifikačních autorit a dalších registračním autoritám, které k ověřování platnosti každé strany zúčastněné v elektronické transakce pomocí kryptografie využívající veřejného klíče. Certifikační autorita vydává certifikáty a každý certifikát má sadu pole, které obsahují data, jako například *subjektu* (entit, ke kterému je certifikát vystavený), data platnosti (Pokud je certifikát platný), vystavitele (na Entita, která vydala certifikát) a veřejný klíč. Ve službě WCF, každý z těchto vlastností zpracovávány jako <xref:System.IdentityModel.Claims.Claim>, a jednotlivých deklarací identity se dále dělí do dvou typů: identity a doprava. Další informace o X.509 certifikátů najdete v části [veřejný klíč certifikáty X.509](http://go.microsoft.com/fwlink/?LinkId=209952)Další informace o deklaracích identity a autorizace ve WCF najdete [správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md). Další informace o implementaci infrastruktury veřejných KLÍČŮ najdete v tématu [Windows Server 2008 R2 - Certificate Services](http://go.microsoft.com/fwlink/?LinkId=209949).  
  
 Primární funkce certifikátu je ověřovat identitu vlastníka certifikátu ostatním uživatelům. Obsahuje certifikát *veřejný klíč* vlastníka, zatímco vlastník uchovává privátní klíč. Veřejný klíč slouží k šifrování zpráv posílaných vlastník certifikátu. Pouze vlastník má přístup k privátnímu klíči, takže pouze vlastník může dešifrovat tyto zprávy.  
  
 Certifikáty musí být vydaný certifikační autoritou, což se často stává třetích stran vystavitelů certifikátů. V doméně systému Windows, je součástí certifikační autority, slouží k vydávání certifikátů pro počítače v doméně.  
  
## <a name="viewing-certificates"></a>Zobrazení certifikátů  
 Pro práci s certifikáty, je často potřeba zobrazit a zkontrolovat jejich vlastnosti. Snadno se provádí pomocí modulu snap-in nástroje Microsoft Management Console (MMC). Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="certificate-stores"></a>Úložiště certifikátů  
 Certifikáty se nacházejí v úložištích. Dva hlavní úložiště umístění zabývajících se dále dělí do dílčí úložiště. Pokud jste správce v počítači, můžete zobrazit oba hlavní úložiště pomocí modulu snap-in nástroje konzoly MMC. Všichni uživatelé můžete zobrazit pouze aktuální úložiště uživatele.  
  
-   **Úložiště místního počítače**. Tato položka obsahuje certifikáty přístup procesy, počítače, jako například [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Používá toto umístění pro uložení certifikáty, které ověření serveru vůči klientům.  
  
-   **Úložiště aktuálního uživatele**. Interaktivní aplikace obvykle umístit certifikáty pro aktuálního uživatele počítače. Pokud vytváříte klientskou aplikaci, to je třeba obvykle umístit certifikáty, které ověření uživatele ke službě.  
  
 Tyto dvě úložiště se dále dělí do dílčí úložiště. Nejdůležitější z těchto při programování s použitím technologie WCF patří:  
  
-   **Důvěryhodné kořenové certifikační autority**. Certifikáty v tomto úložišti vám pomůže vytvořit řetěz certifikátů, které lze sledovat zpět k certifikátu certifikačního úřadu v tomto úložišti.  
  
    > [!IMPORTANT]
    >  Místní počítač implicitně důvěřuje některý z certifikátů umístěny v tomto úložišti, i v případě, že certifikát nepochází od důvěryhodné certifikační autority. Z tohoto důvodu Neumísťujte některý z certifikátů do tohoto úložiště Pokud plně důvěřovat vystavitele a chápu důsledky.  
  
-   **Osobní**. Toto úložiště se používá pro certifikáty, které jsou přidružené uživateli počítače. Toto úložiště se obvykle používá pro certifikáty vystavené pomocí jedné z certifikátů certifikační autority v úložišti důvěryhodných kořenových certifikačních autorit nalezen. Certifikát je zde uveden Alternativně může samoobslužné vydané a důvěryhodná aplikace.  
  
 Další informace o úložištích certifikátů najdete v tématu [úložiště certifikátů](http://go.microsoft.com/fwlink/?LinkId=88912).  
  
### <a name="selecting-a-store"></a>Výběr úložiště  
 Výběr umístění pro uložení certifikátu závisí, jak a kdy běží služba nebo klienta. Použít následující obecná pravidla:  
  
-   Pokud je služba WCF hostovaná k využívání služby systému Windows **místního počítače** uložit. Všimněte si, že jsou vyžadována oprávnění správce k instalaci certifikátů do úložiště místního počítače.  
  
-   Pokud se služba nebo klienta je aplikace, která běží pod účtem uživatele, použijte **aktuální uživatel** uložit.  
  
### <a name="accessing-stores"></a>Přístup k úložiště  
 Úložiště jsou chráněné pomocí seznamů řízení přístupu (ACL), stejně jako složky v počítači. Při vytváření služby hostované pomocí Internetové informační služby (IIS), [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proces běží pod [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] účtu. Služba se používá, musí mít účet přístup k úložišti, které obsahuje certifikáty. Každou z hlavních úložiště je chráněný pomocí seznamu výchozí přístupu, ale mohou být upravena seznamy. Pokud vytvoříte samostatné role pro přístup úložišti, musí udělit oprávnění k této roli. Další postupy k úpravě seznamu přístupu pomocí nástroje WinHttpCertConfig.exe najdete v tématu [postupy: vytvoření dočasné certifikáty pro použití při vývoji](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md). Další informace o klientských certifikátů pomocí služby IIS najdete v tématu [postup volání webové služby pomocí klientského certifikátu pro ověřování v aplikaci ASP.NET Web](http://go.microsoft.com/fwlink/?LinkId=88914).  
  
## <a name="chain-trust-and-certificate-authorities"></a>Řetězec důvěryhodnosti a certifikačních autorit  
 Certifikáty budou vytvořeny v hierarchii, kde je každý jednotlivý certifikát propojený certifikační autoritu, která certifikát vydala. Tento odkaz je certifikát Certifikační autority. Certifikát Certifikační autority a odkazy na certifikační Autoritu, která vydala certifikát originálu Certifikační autority. Tento proces se opakuje, dokud je dosaženo certifikát kořenové certifikační Autority. Certifikát kořenové certifikační Autority je automaticky důvěryhodné.  
  
 Digitální certifikáty se používají k ověřování entity podle tuto hierarchii, označované taky jako *řetěz certifikátů*. Můžete zobrazit řetěz všech certifikátů pomocí modulu snap-in konzoly MMC dvakrát klikněte na libovolný certifikát a potom klepnutím **cesta certifikátu** kartě. Další informace o importování řetězů certifikátů certifikační autority najdete v tématu [postup: Zadejte certifikátu autority certifikát řetězu používá k ověření podpisů](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Všechny vystavitele lze označit umístěním vystavitele certifikátu do úložiště důvěryhodných kořenových certifikátů autority důvěryhodnou kořenovou autoritou.  
  
### <a name="disabling-chain-trust"></a>Zakázání řetěz důvěryhodnosti  
 Při vytváření nové služby, pravděpodobně používáte certifikát, který není vystavený důvěryhodný kořenový certifikát, nebo vlastní certifikát vydávající nemusí být v úložišti Důvěryhodné kořenové certifikační autority. Pro účely vývoje lze dočasně zakázat mechanismus, který kontroluje řetěz certifikátů pro certifikát. Chcete-li to provést, nastavte `CertificateValidationMode` vlastnost, která má buď `PeerTrust` nebo `PeerOrChainTrust`. Buď režimu určuje, že certifikát můžete buď samoobslužné vydat (peer vztahu důvěryhodnosti) nebo jeho část řetěz certifikátů. Vlastnost můžete nastavit na žádném z následujících tříd.  
  
|Třída|Vlastnost|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 Můžete také nastavit vlastnost pomocí konfigurace. K určení režimu ověřování se používají následující prvky:  
  
-   [\<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>Vlastního ověřování  
 `CertificateValidationMode` Vlastnost také umožňuje přizpůsobit, jak se ověřují certifikáty. Ve výchozím nastavení je úroveň nastavena na `ChainTrust`. Použít <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> hodnotu, je nutné také nastavit `CustomCertificateValidatorType` atribut sestavení a typ použitý k ověření certifikátu. Pokud chcete vytvořit vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.  
  
 Při vytváření vlastní ověřovací, je nejdůležitější metodu pro přepsání <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metoda. Příklad vlastní ověřování, naleznete v části [validátor certifikátu X.509](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) ukázka. Další informace najdete v tématu [vlastní pověření a ověřování pověření](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## <a name="using-makecertexe-to-build-a-certificate-chain"></a>Pomocí Makecert.exe vytvořit řetěz certifikátů  
 Nástroj pro vytvoření certifikátu (Makecert.exe) vytvoří certifikáty X.509 a privátní klíč a veřejného páry klíčů. Můžete uložit privátní klíč, aby na disku a použít ho k vystavování a podepsat nové certifikáty, proto simulaci hierarchie zřetězené certifikáty. Nástroj je určen pro použití pouze jako pomocný při vývoji služeb a by měl být nikdy použit k vytvoření certifikátů, pro skutečné nasazení. Při vývoji služby WCF, použijte následující kroky k vytvoření řetěz s Makecert.exe.  
  
#### <a name="to-build-a-chain-of-trust-with-makecertexe"></a>Chcete-li vytvořit řetěz vztah důvěryhodnosti s Makecert.exe  
  
1.  Vytvořte dočasný kořenové autority (certifikát podepsaný svým držitelem) pomocí nástroje MakeCert.exe. Privátní klíč uložte na disk.  
  
2.  Použití nového certifikátu k vystavení dalšího certifikátu, který obsahuje veřejný klíč.  
  
3.  Importujte certifikát kořenové autority do úložiště důvěryhodných kořenových certifikačních autorit.  
  
4.  Podrobné pokyny najdete v tématu [postupy: vytvoření dočasné certifikáty pro použití při vývoji](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
## <a name="which-certificate-to-use"></a>Který certifikát má použít?  
 Časté otázky týkající se certifikátů jsou který certifikát má použít a proč. Odpověď závisí na tom, jestli jsou programování klienta nebo služby. Následující informace poskytuje obecných pokynů a není vyčerpávající odpověď na tyto otázky.  
  
### <a name="service-certificates"></a>Certifikáty služby  
 Certifikáty služby mít úlohu primární ověřování serveru vůči klientům. Jeden počáteční kontrol, když se klient ověřuje serveru je k porovnání hodnota **subjektu** pole k identifikátor URI (Uniform Resource) používá ke kontaktování služby: DNS i se musí shodovat. Například pokud je identifikátor URI služby "http://www.contoso.com/endpoint/" potom **subjektu** pole musí obsahovat také hodnotu "www.contoso.com".  
  
 Všimněte si, že pole může obsahovat několik hodnot každou předponu inicializaci označení hodnoty. Nejčastěji inicializace je "CN" pro běžný název, například "CN = www.contoso.com". Je také možné, **subjektu** pole jako pole prázdné, v takovém případě **alternativní název subjektu** pole může obsahovat **název DNS** hodnotu.  
  
 Všimněte si také hodnotu **zamýšlené účely** pole certifikátu by měla obsahovat odpovídající hodnotu, jako je například "Ověřování serveru" nebo "Ověření klienta".  
  
### <a name="client-certificates"></a>Klientské certifikáty  
 Klientské certifikáty nejsou obvykle vystavované certifikační autority. Místo toho osobním úložišti aktuální umístění uživatele obvykle obsahuje certifikáty umísťují kořenovou autoritou, s zamýšlený účel "Ověření klienta". Klienta můžete použít tento certifikát, pokud se vyžaduje vzájemné ověření.  
  
## <a name="online-revocation-and-offline-revocation"></a>Odvolání online a Offline odvolání  
  
### <a name="certificate-validity"></a>Platnost certifikátu.  
 Každý certifikát je platný pouze pro danou dobu volat *období platnosti*. Doba platnosti je definována **platné od** a **platné do** pole certifikátu X.509. Při ověřování certifikátu se kontroluje k určení, zda je certifikát stále v období platnosti.  
  
### <a name="certificate-revocation-list"></a>Seznam odvolaných certifikátů  
 Kdykoli během doby platnosti certifikační autority můžete odvolat certifikát. Tato situace může nastat z mnoha důvodů, jako je například ohrožení privátní klíč certifikátu.  
  
 V takovém případě všechny řetězy, které sestup z odvolaný certifikát jsou neplatné a během ověřování postupů nejsou důvěryhodné. Pokud chcete zjistit, které certifikáty byly odvolány, každý Vystavitel publikuje, a čas a datum označením *seznam odvolaných certifikátů* (CRL). V seznamu můžete zkontrolovat pomocí nastavení odvolání online nebo offline odvolání `RevocationMode` nebo `DefaultRevocationMode` vlastnost na jednu z následujících tříd <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> hodnot výčtu: <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> třídy. Výchozí hodnota pro všechny vlastnosti je `Online`.  
  
 Můžete také nastavit režim do konfigurace pomocí `revocationMode` atribut i [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (z [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) a [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).  
  
## <a name="the-setcertificate-method"></a>Metoda SetCertificate  
 Ve službě WCF často musíte zadat certifikát nebo nastavit certifikátů službu nebo klienta, je použít k ověření, šifrování nebo digitálně podepsat zprávu. To můžete provést programově pomocí `SetCertificate` metoda různých tříd, které představují certifikáty X.509. Následující třídy pomocí `SetCertificate` metoda k určení certifikátu.  
  
|Třída|Metoda|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 `SetCertificate` Metoda funguje tak, že určení umístění úložiště a úložiště, typu "najít" (`x509FindType` parametr) určující pole certifikátu a hodnotu k vyhledání v poli. Například následující kód vytvoří <xref:System.ServiceModel.ServiceHost> instance a nastaví certifikát služby používaný k ověřování klientů `SetCertificate` metoda.  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>Víc certifikátů se stejnou hodnotou  
 Úložiště může obsahovat víc certifikátů se stejným názvem subjektu. To znamená, že pokud určíte `x509FindType` je <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> nebo <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>a více než jeden certifikát má stejnou hodnotu, protože neexistuje žádný způsob k rozlišení, který certifikát je vyžadován, je vyvolána výjimka. To lze zmírnit nastavením `x509FindType` k <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. Kryptografický otisk pole obsahuje jedinečnou hodnotu, která můžete použít k vyhledání konkrétní certifikát v úložišti. To má však vlastní nevýhodou: Pokud certifikát je odvolaný nebo obnovit, `SetCertificate` metoda nezdaří, protože je také pryč kryptografický otisk. Nebo, pokud již není platný certifikát, se ověřování nezdaří. Způsob, jak toto riziko lze je nastavit `x590FindType` parametru <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> a zadejte název vystavitele. Pokud je potřeba žádné konkrétní vystavitele, můžete také nastavit jednu z dalších <xref:System.Security.Cryptography.X509Certificates.X509FindType> hodnot výčtu, například <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.  
  
## <a name="certificates-in-configuration"></a>Certifikáty v konfiguraci  
 Certifikáty můžete vytvořit také pomocí konfigurace. Pokud vytváříte službu, v části jsou zadané přihlašovací údaje, včetně certifikátů, [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Pokud programujete klienta, jsou v části zadat certifikátů [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>Mapování certifikátu na uživatelský účet  
 Funkce služby IIS a služby Active Directory je možnost mapovat certifikát na uživatelský účet systému Windows. Další informace o funkci najdete v tématu [mapování certifikátů na uživatelské účty](http://go.microsoft.com/fwlink/?LinkId=88917).  
  
 Další informace o používání služby Active Directory mapování najdete v tématu [mapování klientských certifikátů pomocí mapování adresářových služeb](http://go.microsoft.com/fwlink/?LinkId=88918).  
  
 Tato funkce povolená, můžete nastavit <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> vlastnost <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy k `true`. V konfiguraci, můžete nastavit `mapClientCertificateToWindowsAccount` atribut [ \<ověřování >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element `true`, jak je znázorněno v následujícím kódu.  
  
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
  
 Mapování certifikátu X.509. certifikát na token, který představuje uživatelský účet systému Windows se považuje zvýšení úrovně oprávnění, protože po namapované, tokenu systému Windows lze použít k získání přístupu k chráněným prostředkům. Proto zásada domény vyžaduje certifikát X.509 ke splnění svých zásad před mapování. *SChannel* balíček zabezpečení vynucuje tento požadavek.  
  
 Při použití [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] nebo novější, WCF zajišťuje certifikátu odpovídá zásadám domény předtím, než je namapován na účet systému Windows.  
  
 V první verzi služby WCF se provádí mapování bez konzultace ohledně zásad domény. Proto je možné, že starší aplikace, které používají k práci při spuštění v první verzi nepovede, pokud je povoleno mapování a certifikátu X.509 nesplňuje zásady domény.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels>  
 <xref:System.ServiceModel.Security>  
 <xref:System.ServiceModel>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
