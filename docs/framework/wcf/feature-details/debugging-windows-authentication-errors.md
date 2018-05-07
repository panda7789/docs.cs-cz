---
title: Ladění chyb ověřování systému Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: d9226324b69e5c27738abb35bb155a43964b9127
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-windows-authentication-errors"></a>Ladění chyb ověřování systému Windows
Pokud používáte ověřování systému Windows jako vhodný mechanismus zabezpečení, rozhraní pro zprostředkovatele podpory zabezpečení (SSPI) zpracovává procesy zabezpečení. Při výskytu chyb zabezpečení ve vrstvě rozhraní SSPI, že jsou prezentované podle Windows Communication Foundation (WCF). Toto téma obsahuje framework a sadu otázky, které pomohou diagnostikovat chyby.  
  
 Přehled protokolu Kerberos najdete v tématu [protokolu Kerberos](http://go.microsoft.com/fwlink/?LinkID=86946); najdete v tématu Přehled SSPI, [SSPI](http://go.microsoft.com/fwlink/?LinkId=88941).  
  
 Pro ověřování systému Windows, se většinou používá WCF *Negotiate* zprostředkovatele podpory zabezpečení (SSP), který provádí vzájemné ověřování protokolem Kerberos mezi klientem a službou. Pokud protokol Kerberos není k dispozici, ve výchozím nastavení WCF přejde k NT LAN Manager (NTLM). Můžete ale nakonfigurovat WCF používají pouze protokol Kerberos, (a způsobí výjimku, pokud protokolu Kerberos není k dispozici). Můžete také nakonfigurovat WCF pro použití s omezeným přístupem formulářů protokolu Kerberos.  
  
## <a name="debugging-methodology"></a>Ladění metody  
 Základní metoda vypadá takto:  
  
1.  Určí, jestli používáte ověřování systému Windows. Pokud používáte jiné schéma, toto téma se nevztahuje.  
  
2.  Pokud jste si jistí, že používáte ověřování systému Windows, zjistěte, zda konfiguraci WCF používá přímo pomocí protokolu Kerberos nebo Negotiate.  
  
3.  Jakmile zjistíte, zda je vaše konfigurace pomocí protokolu Kerberos nebo NTLM, rozumíte chybové zprávy v rámci správné.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Dostupnost protokolu Kerberos a NTLM  
 Zprostředkovatel zabezpečení protokolu Kerberos vyžaduje řadič domény tak, aby fungoval jako protokolu Kerberos Center KDC (Key Distribution). Protokol Kerberos je k dispozici pouze v případě, že klient a služba používáte domény identity. V jiné kombinace účet se používá protokol NTLM, dle souhrnu v následující tabulce.  
  
 Záhlaví tabulky zobrazit typy účet možných používaná na serveru. V levém sloupci uvádí možné typy účtů používaných klientem.  
  
||Místní uživatele|Místní systém|Uživatel domény|Počítače domény|  
|-|----------------|------------------|-----------------|--------------------|  
|Místní uživatele|NTLM|NTLM|NTLM|NTLM|  
|Místní systém|Anonymní ověřování NTLM|Anonymní ověřování NTLM|Anonymní ověřování NTLM|Anonymní ověřování NTLM|  
|Uživatel domény|NTLM|NTLM|Pomocí protokolu Kerberos|Pomocí protokolu Kerberos|  
|Počítače domény|NTLM|NTLM|Pomocí protokolu Kerberos|Pomocí protokolu Kerberos|  
  
 Konkrétně čtyři typy účtů patří:  
  
-   Místní uživatel: Profil uživatele pouze počítače. Příklad: `MachineName\Administrator` nebo `MachineName\ProfileName`.  
  
-   Místní systém: Předdefinovaný účet systému na počítači, který není připojený k doméně.  
  
-   Uživatel domény: Uživatelský účet v doméně systému Windows. Příklad: `DomainName\ProfileName`.  
  
-   Počítač domény: Proces s identitu počítače spuštěný na počítači připojený k doméně systému Windows. Příklad: `MachineName\Network Service`.  
  
> [!NOTE]
>  Přihlašovací údaje služby pořízen při <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.ServiceHost> třídy se nazývá. Pověření klienta je pro čtení vždy, když klient odešle zprávu.  
  
## <a name="common-windows-authentication-problems"></a>Běžné problémy ověřování systému Windows  
 Tato část popisuje některé běžné problémy ověřování systému Windows a možné způsoby.  
  
### <a name="kerberos-protocol"></a>Protokol Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Hlavní název služby/UPN problémy s protokolem Kerberos  
 Pokud používáte ověřování systému Windows a protokol je použít nebo vyjednaném rozhraní SSPI protokolu Kerberos, musí obsahovat adresu URL koncového bodu klienta používá plně kvalifikovaný název domény hostitele služby uvnitř adresu URL služby. Předpokladem je, že účet, pod kterým běží služba má přístup k klíč služby (SPN) pro hlavní název počítače (výchozí), který se vytvoří, když je počítač přidán do domény Active Directory, která se nejčastěji provádí spuštěním služby v rámci Účet služby sítě. Pokud služba nemá přístup ke klíči počítače hlavní název služby, je třeba zadat správný hlavní název služby nebo uživatele hlavní název (UPN) účtu, pod kterým je služba spuštěná v identitu koncového bodu klienta. Další informace o fungování WCF s SPN a UPN najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 Ve službě Vyrovnávání zatížení případech, například webových farem nebo webové zahrada běžnou praxí je definovat jedinečný účet pro každou aplikaci, k tomuto účtu přiřadit název SPN a ujistěte se, že všechny aplikace služby spuštěny v daném účtu.  
  
 Pokud chcete získat název SPN pro účet služby, musíte být správcem domény služby Active Directory. Další informace najdete v tématu [Kerberos technické Supplement pro Windows](http://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Protokol Kerberos Direct vyžaduje službu, kterou chcete spustit pod účtem počítače domény  
 K tomu dojde při `ClientCredentialType` je nastavena na `Windows` a <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> je nastavena na `false`, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 K nápravě, spusťte službu pomocí účtu domény počítače, například síťové služby v doméně připojené k počítači.  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegování vyžaduje vyjednávání pověření  
 Pokud chcete používat ověřování protokolu Kerberos s delegováním, musí implementovat protokol Kerberos s vyjednávání pověření (někdy nazývané "služby větev" nebo "vícekrokový" Kerberos). Pokud budete implementovat ověřování protokolem Kerberos bez vyjednávání pověření (někdy nazývané "jednorázové" nebo "single větev" Kerberos), bude vyvolána výjimka.  
  
 K implementaci protokolu Kerberos s vyjednávání pověření, proveďte následující kroky:  
  
1.  Implementace delegování nastavením <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> k <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2.  Vyžadovat vyjednávání SSPI:  
  
    1.  Pokud používáte standard vazby, nastavte `NegotiateServiceCredential` vlastnost `true`.  
  
    2.  Pokud používáte vlastní vazby, nastavte `AuthenticationMode` atribut `Security` element `SspiNegotiated`.  
  
3.  Vyžadovat vyjednávání SSPI pro použití protokolu Kerberos, protože je zakázáno použití protokolu NTLM:  
  
    1.  To lze proveďte v kódu, pomocí následujícího příkazu: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2.  Nebo můžete provést v konfiguračním souboru nastavením `allowNtlm` atribut `false`. Tento atribut je součástí [ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Protokol NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Vyjednávání vrátí zprostředkovatele sdílených služeb k protokolu NTLM, ale je zakázaný protokol NTLM  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Je nastavena na `false`, což způsobí, že Windows Communication Foundation (WCF), aby best effort vyvolá výjimku, pokud se používá protokol NTLM. Všimněte si, že nastavení této vlastnosti na `false` nemusí zabránit odesílány prostřednictvím sítě pověření NTLM.  
  
 Následující ukazuje, jak zakázat nouzového řešení ověření pomocí protokolu NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Selhání přihlášení protokolem NTLM  
 Pověření klienta nejsou platné ve službě. Zkontrolujte, zda uživatelské jméno a heslo jsou správně nastavena a odpovídat na účet, který se označuje k počítači, kde je služba spuštěná. NTLM používá zadaná pověření pro přihlášení k počítači služby. Přihlašovací údaje mohou být na počítači, na kterém je spuštěný klient platná, toto přihlášení se nezdaří, pokud přihlašovací údaje nejsou platné v počítači služby.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Dojde k přihlášení anonymní NTLM, ale anonymní přihlášení jsou ve výchozím nastavení zakázaná.  
 Při vytváření klienta, <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> je nastavena na <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, jak je znázorněno v následujícím příkladu, ale ve výchozím nastavení serveru zakáže anonymní přihlášení. K tomu dochází, protože výchozí hodnota <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> vlastnost <xref:System.ServiceModel.Security.WindowsServiceCredential> třída je `false`.  
  
 Následující kód klienta se pokusí je povolit (Všimněte si, že je vlastnost výchozí `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Následující kód služby změní výchozí server povolit anonymní přihlášení.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Další informace o zosobnění najdete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Můžete taky klient používá jako služby systému Windows, pomocí předdefinovaného účtu SYSTEM.  
  
### <a name="other-problems"></a>Jiné problémy  
  
#### <a name="client-credentials-are-not-set-correctly"></a>Pověření klienta není správného nastavení  
 Ověřování systému Windows používá <xref:System.ServiceModel.Security.WindowsClientCredential> vrácené instance <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy, ne <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Následující ukazuje příklad nesprávné.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Následující obrázek znázorňuje příklad správné.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>Rozhraní SSPI není k dispozici  
 Následující operační systémy nepodporují ověřování systému Windows, když se použije jako server: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition a [!INCLUDE[wv](../../../../includes/wv-md.md)]domácí edice.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Vývoj a nasazení s různými identitami  
 Pokud nasazení na jiném vyvíjet aplikaci na jednom počítači a používají různé typy účtu k ověření na každém počítači, můžete se setkat různé chování. Předpokládejme například, vývoj aplikace v systému Windows XP Pro počítač pomocí `SSPI Negotiated` režim ověřování. Pokud používáte k ověřování pro účet místního uživatele, se používat protokol NTLM. Jakmile je aplikace, můžete nasadit službu pro počítače s Windows Server 2003, kde běží pod účtem domény. V tomto okamžiku klienta nebude možné k ověření služby, protože pomocí protokolu Kerberos a řadič domény se používá.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
