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
ms.openlocfilehash: a68a291b1974e86c9a4f16f9d90a879649076533
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595133"
---
# <a name="debugging-windows-authentication-errors"></a>Ladění chyb ověřování systému Windows
Pokud používáte ověřování Windows jako vhodný mechanismus zabezpečení, rozhraní zprostředkovatele podpory zabezpečení (SSPI) zpracovává procesy zabezpečení. Když dojde k chybě zabezpečení ve vrstvě rozhraní SSPI, zobrazují se ve Windows Communication Foundation (WCF). Toto téma obsahuje rozhraní framework a sadu otázky, které vám umožní diagnostikovat chyby.  
  
 Přehled protokolu Kerberos najdete v tématu [protokolu Kerberos](https://go.microsoft.com/fwlink/?LinkID=86946); najdete v tématu Přehled SSPI, [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941).  
  
 Ověřování Windows, WCF obvykle používá *Negotiate* zprostředkovatele podpory zabezpečení (SSP), který provádí vzájemné ověřování protokolu Kerberos mezi klientem a službou. Pokud není k dispozici protokol Kerberos, ve výchozím nastavení WCF spadne zpět na NT LAN Manager (NTLM). Můžete ale nakonfigurovat WCF pro použití protokolu Kerberos (a vyvolá výjimku, pokud není k dispozici protokol Kerberos). Můžete také nakonfigurovat WCF pro použití s omezeným přístupem formulářů protokolu Kerberos.  
  
## <a name="debugging-methodology"></a>Ladění metodologie  
 Základní metoda vypadá takto:  
  
1.  Určete, jestli používáte ověřování Windows. Pokud používáte jiné schéma, toto téma se nevztahuje.  
  
2.  Pokud jste si jistí, že používáte ověřování Windows, zjistěte, zda vaše konfigurace WCF používá přímo pomocí protokolu Kerberos nebo Negotiate.  
  
3.  Jakmile určíte, jestli používá konfigurace protokolu Kerberos nebo NTLM, vám umožní pochopit chybové zprávy ve správném kontextu.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Dostupnost protokolu Kerberos a NTLM  
 Zprostředkovatel zabezpečení protokolu Kerberos vyžaduje řadič domény tak, aby fungoval jako protokolu Kerberos distribuce Center KDC (Key). Protokol Kerberos je k dispozici pouze v případě, že klient a služba používáte doménu identit. V jiné kombinace účet se používá protokol NTLM, dle souhrnu v následující tabulce.  
  
 Záhlaví tabulky zobrazit typy možných účtu používaného serverem. V levém sloupci se zobrazuje možné typy účtů používaných klientem.  
  
||Místní uživatele|Místní systém|Domain User|Domain Machine|  
|-|----------------|------------------|-----------------|--------------------|  
|Místní uživatele|NTLM|NTLM|NTLM|NTLM|  
|Místní systém|Anonymní ověřování NTLM|Anonymní ověřování NTLM|Anonymní ověřování NTLM|Anonymní ověřování NTLM|  
|Domain User|NTLM|NTLM|Protokol Kerberos|Protokol Kerberos|  
|Domain Machine|NTLM|NTLM|Protokol Kerberos|Protokol Kerberos|  
  
 Konkrétně čtyři typy účtů patří:  
  
-   Místní uživatel: Profil uživatele jenom pro počítače. Příklad: `MachineName\Administrator` nebo `MachineName\ProfileName`.  
  
-   Místní systém: Předdefinovaný účet systému na počítači, který není připojený k doméně.  
  
-   Domain User: Uživatelský účet v doméně Windows. Například: `DomainName\ProfileName`.  
  
-   Domain Machine: Zpracování pomocí identitu počítače spuštěné na počítači připojený k doméně Windows. Například: `MachineName\Network Service`.  
  
> [!NOTE]
>  Přihlašovací údaje služby jsou zachyceny při <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.ServiceHost> třída se nazývá. Čtení přihlašovacích údajů klienta vždy, když klient odešle zprávu.  
  
## <a name="common-windows-authentication-problems"></a>Běžné potíže s ověřováním Windows  
 Tato část popisuje některé běžné problémy ověřování Windows a mezi možné nápravy.  
  
### <a name="kerberos-protocol"></a>Protokol Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Název SPN a UPN problémy s protokolem Kerberos  
 Pokud používáte ověřování Windows a je použít nebo vyjednaném rozhraní SSPI protokolu Kerberos, adresa URL používá koncový bod klienta musí obsahovat plně kvalifikovaný název hostitele služby uvnitř adresu URL služby. Předpokladem je, že účet, pod kterým běží služba má přístup ke klíči počítače (výchozí) služby hlavní název (SPN), který je vytvořen při přidání počítače do domény služby Active Directory, která se obvykle provádí spuštěním služby v rámci Účet síťových služeb. Pokud služba nemá přístup ke klíči počítače hlavní název služby, musíte zadat správný hlavní název služby nebo uživatele hlavní název (UPN) účtu, pod kterým běží služba v identitě koncového bodu klienta. Další informace o tom, jak funguje WCF s SPN a UPN najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 Ve službě Vyrovnávání zatížení scénáře, jako je webové farmy nebo webové zahrady běžnou praxí je definovat jedinečný účet pro každou aplikaci, přiřaďte název SPN pro tento účet a ujistěte se, že všechny aplikace služby spustili v tomto účtu.  
  
 Pokud chcete získat název SPN pro účet služby, musíte být správcem domény služby Active Directory. Další informace najdete v tématu [Kerberos technické Supplement pro Windows](https://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Protokol Kerberos přímo vyžaduje službu spustit pod účtem počítače domény  
 K tomu dojde při `ClientCredentialType` je nastavena na `Windows` a <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> je nastavena na `false`, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Chcete napravit, spusťte službu pomocí účtu počítače domény, například Síťová služba, v doméně připojené k počítači.  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegování vyžaduje vyjednávání přihlašovacích údajů  
 Delegování používat ověřování protokolu Kerberos, musí implementovat protokol Kerberos s vyjednávání přihlašovacích údajů (někdy nazývané "více větev" nebo "vícekrokový" protokolu Kerberos). Pokud se rozhodnete implementovat ověřování protokolem Kerberos bez vyjednávání přihlašovacích údajů (někdy nazývané "jednorázové" nebo "jedné fáze" protokolu Kerberos), bude vyvolána výjimka.  
  
 Implementace protokolu Kerberos s vyjednávání přihlašovacích údajů, proveďte následující kroky:  
  
1.  Implementace delegování tak, že nastavíte <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> k <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2.  Vyžadovat vyjednávání SSPI:  
  
    1.  Pokud používáte standardní vazby, nastavte `NegotiateServiceCredential` vlastnost `true`.  
  
    2.  Pokud používáte vlastní vazby, nastavte `AuthenticationMode` atribut `Security` elementu `SspiNegotiated`.  
  
3.  Vyžadovat vyjednávání SSPI pro použití protokolu Kerberos zakázáním použít protokol NTLM:  
  
    1.  To lze proveďte v kódu, pomocí následujícího příkazu: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2.  Nebo můžete provést v konfiguračním souboru tak, že nastavíte `allowNtlm` atribut `false`. Tento atribut je součástí [ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Protokol NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Vyjednávání vrátí zprostředkovatele sdílených služeb k protokolu NTLM, ale je zakázaný protokol NTLM  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Je nastavena na `false`, což způsobí, že Windows Communication Foundation (WCF), aby se snažíme vyvolá výjimku, pokud je použit protokol NTLM. Všimněte si, že nastavení této vlastnosti na `false` nemůže zabránit odeslání při přenosu přihlašovacích údajů protokolů NTLM.  
  
 Následující ukazuje, jak zakázat nouzového řešení ověření pomocí NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>NTLM přihlášení selže  
 Pověření klienta nejsou platné ve službě. Zkontrolujte, zda uživatelské jméno a heslo jsou správně nastavené a odpovídat účtu, který se označuje k počítači, kde je služba spuštěna. NTLM používá zadané přihlašovací údaje pro přihlášení k počítači služby. Přihlašovací údaje mohou být platné na počítači, na kterém je spuštěný klient, toto přihlášení se nezdaří, pokud přihlašovací údaje nejsou platné v počítači služby.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Dojde k přihlášení anonymní ověřování NTLM, ale anonymní přihlášení jsou ve výchozím nastavení zakázané.  
 Při vytváření klienta, <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> je nastavena na <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, jak je znázorněno v následujícím příkladu, ale ve výchozím nastavení zakazuje anonymní přihlášení k serveru. K tomu dochází, výchozí hodnota <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> vlastnost <xref:System.ServiceModel.Security.WindowsServiceCredential> třída je `false`.  
  
 Následující kód klienta se pokusí povolit anonymní přihlášení (Všimněte si, že vlastnost default je `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Následující kód služby změní výchozí povolit anonymní přihlášení server.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Další informace o zosobnění, naleznete v tématu [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Případně klient je spuštěný jako služba Windows pomocí předdefinovaného účtu SYSTEM.  
  
### <a name="other-problems"></a>Další problémy  
  
#### <a name="client-credentials-are-not-set-correctly"></a>Přihlašovací údaje pro klienta není správně nastaveno  
 Používá ověřování Windows <xref:System.ServiceModel.Security.WindowsClientCredential> instanci vrácenou <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy, ne <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Následuje příklad nesprávné.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Následuje příklad správný.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>Rozhraní SSPI není k dispozici  
 Následující operační systémy nepodporují ověřování Windows, když se použije jako server: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition a [!INCLUDE[wv](../../../../includes/wv-md.md)]domácí edice.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Vývoj a nasazení pomocí jiné identity  
 Pokud nasazení na jiném vývoj vaší aplikace na jednom počítači a použít různé typy účtu k ověření na každém počítači, můžete se setkat různé chování. Předpokládejme například, že při vývoji vaší aplikace na Windows XP Pro počítač používá `SSPI Negotiated` režim ověřování. Pokud používáte místní uživatelský účet k ověření, se používá protokol NTLM. Jakmile je aplikace, můžete nasadit službu pro počítače s Windows serverem 2003 tam, kde běží pod účtem domény. V tomto okamžiku klienta nebude možné ověření služby, protože se používá, pomocí protokolů Kerberos a řadičem domény.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
