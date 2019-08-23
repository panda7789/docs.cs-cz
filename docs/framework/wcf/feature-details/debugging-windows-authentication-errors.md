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
ms.openlocfilehash: 20ca8f049298f75412da4c8a7e58975954f67741
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968863"
---
# <a name="debugging-windows-authentication-errors"></a>Ladění chyb ověřování systému Windows
Při použití ověřování systému Windows jako mechanismu zabezpečení zpracovává rozhraní SSPI (Security Support Provider Interface) procesy zabezpečení. Pokud dojde k chybám zabezpečení ve vrstvě SSPI, jsou umístěny na základě Windows Communication Foundation (WCF). Toto téma poskytuje strukturu a sadu otázek, které vám pomůžou diagnostikovat chyby.  
  
 Přehled protokolu Kerberos najdete v tématu [Vysvětlení protokolu Kerberos](https://go.microsoft.com/fwlink/?LinkID=86946). Přehled rozhraní SSPI naleznete v tématu [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941).  
  
 Pro ověřování systému Windows WCF typicky používá zprostředkovatele zabezpečení (SSP), který provádí vzájemné ověřování protokolu Kerberos mezi klientem a službou. Pokud protokol Kerberos není k dispozici, ve výchozím nastavení se služba WCF vrátí do programu NT LAN Manager (NTLM). Můžete ale nakonfigurovat WCF na použití jenom protokolu Kerberos (a vyvolat výjimku, pokud není k dispozici protokol Kerberos). Můžete také nakonfigurovat WCF tak, aby používal omezené formuláře protokolu Kerberos.  
  
## <a name="debugging-methodology"></a>Metodologie ladění  
 Základní metoda je následující:  
  
1. Určete, zda používáte ověřování systému Windows. Pokud používáte jiné schéma, toto téma se nevztahuje.  
  
2. Pokud jste si jisti, že používáte ověřování systému Windows, určete, zda konfigurace WCF používá metodu Kerberos Direct nebo Negotiate.  
  
3. Jakmile zjistíte, jestli vaše konfigurace používá protokol Kerberos nebo NTLM, můžete pochopit chybové zprávy ve správném kontextu.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Dostupnost protokolu Kerberos a protokolu NTLM  
 Zprostředkovatel zabezpečení protokolu Kerberos vyžaduje, aby řadič domény fungoval jako služba KDC (Key Distribution Center) protokolu Kerberos (KDC). Protokol Kerberos je k dispozici pouze v případě, že klient i služba používají identity domény. V kombinaci s jinými účty se používá protokol NTLM, jak je shrnuto v následující tabulce.  
  
 Záhlaví tabulky zobrazují možné typy účtů používané serverem. V levém sloupci se zobrazují možné typy účtů používané klientem.  
  
||Místní uživatel|Místní systém|Uživatel domény|Počítač domény|  
|-|----------------|------------------|-----------------|--------------------|  
|Místní uživatel|NTLM|NTLM|NTLM|NTLM|  
|Místní systém|Anonymní protokol NTLM|Anonymní protokol NTLM|Anonymní protokol NTLM|Anonymní protokol NTLM|  
|Uživatel domény|NTLM|NTLM|Sdílené|Sdílené|  
|Počítač domény|NTLM|NTLM|Sdílené|Sdílené|  
  
 Mezi ně patří konkrétně tyto čtyři typy účtů:  
  
- Místní uživatel: Jenom počítač – profil uživatele. Například: `MachineName\Administrator` nebo `MachineName\ProfileName`.  
  
- Místní systém: Integrovaný systém účtů na počítači, který není připojený k doméně.  
  
- Uživatel domény: Uživatelský účet v doméně systému Windows. Například: `DomainName\ProfileName`.  
  
- Počítač domény: Proces s identitou počítače běžící na počítači připojeném k doméně systému Windows. Například: `MachineName\Network Service`.  
  
> [!NOTE]
> Pověření služby je zachyceno při <xref:System.ServiceModel.ICommunicationObject.Open%2A> volání metody <xref:System.ServiceModel.ServiceHost> třídy. Přihlašovací údaje klienta se čtou při každém odeslání zprávy klientem.  
  
## <a name="common-windows-authentication-problems"></a>Běžné problémy s ověřováním systému Windows  
 Tato část popisuje některé běžné problémy s ověřováním systému Windows a možné nápravy.  
  
### <a name="kerberos-protocol"></a>Protokol Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Problémy hlavního názvu služby (SPN) nebo UPN s protokolem Kerberos  
 Při použití ověřování systému Windows a protokolem SSPI se používá nebo vyjednává protokol Kerberos, adresa URL, kterou koncový bod klienta používá, musí obsahovat plně kvalifikovaný název domény hostitele služby v adrese URL služby. Předpokládá se, že účet, pod kterým je služba spuštěná, má přístup k klíči hlavního názvu (SPN) služby (SPN), který se vytvoří při přidání počítače do domény služby Active Directory, která se nejčastěji provádí spuštěním služby pod Účet síťové služby. Pokud služba nemá přístup k klíči hlavního názvu služby, je nutné, abyste zadali správný název SPN nebo hlavní název uživatele (UPN) účtu, pod kterým je služba spuštěná v identitě koncového bodu klienta. Další informace o tom, jak WCF funguje se službou SPN a hlavním názvem uživatele (UPN), najdete v tématu [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 V rámci scénářů vyrovnávání zatížení, jako jsou webové nebo webové zahrady, se v běžné praxi definují jedinečný účet pro každou aplikaci, přiřadíte k tomuto účtu hlavní název služby (SPN) a zajistěte, aby všechny služby aplikace běžely v tomto účtu.  
  
 K získání hlavního názvu služby (SPN) pro účet vaší služby musíte být správcem domény služby Active Directory. Další informace najdete v tématu o [technickém dodatku Kerberos pro Windows](https://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Protokol Kerberos Direct vyžaduje, aby služba běžela pod účtem počítače domény.  
 K `ClientCredentialType` tomu dochází, je-li vlastnost `Windows` nastavena na <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> hodnotu a vlastnost je `false`nastavena na hodnotu, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Pokud chcete tento problém vyřešit, spusťte službu pomocí účtu počítače v doméně, jako je třeba síťová služba, na počítači připojeném k doméně.  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegování vyžaduje vyjednávání přihlašovacích údajů  
 Chcete-li použít ověřovací protokol Kerberos s delegováním, je nutné implementovat protokol Kerberos s vyjednáváním přihlašovacích údajů (někdy se jim říká "Multi-nohy" nebo "multi-step" Kerberos). Pokud implementujete ověřování protokolu Kerberos bez vyjednávání přihlašovacích údajů (někdy se nazývá "jednorázové" nebo "jednorázové" Kerberos), vyvolá se výjimka.  
  
 K implementaci protokolu Kerberos s vyjednáváním přihlašovacích údajů proveďte následující kroky:  
  
1. Implementujte delegování <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> nastavením na <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2. Vyžadovat vyjednávání SSPI:  
  
    1. Používáte-li standardní vazby, nastavte `NegotiateServiceCredential` vlastnost na `true`hodnotu.  
  
    2. Pokud používáte vlastní vazby, nastavte `AuthenticationMode` atribut `Security` elementu na `SspiNegotiated`.  
  
3. Vyžaduje, aby vyjednávání SSPI používalo protokol Kerberos, a to tak, že nepovolí použití NTLM:  
  
    1. Udělejte to v kódu s následujícím příkazem:`ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2. Nebo to můžete provést v konfiguračním souboru nastavením `allowNtlm` atributu na. `false` Tento atribut je součástí [ \<> Windows](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Protokol NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Vyjednání SSP se vrátí do protokolu NTLM, ale protokol NTLM je zakázán.  
 Vlastnost je nastavena na `false`, což způsobí, že Windows Communication Foundation (WCF) vyvolá výjimku, pokud je použit protokol NTLM. <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Všimněte si, že nastavení této `false` vlastnosti na nemusí bránit v posílání přihlašovacích údajů NTLM přes tento kabel.  
  
 Následující příklad ukazuje, jak zakázat použití funkce Fallback na NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Přihlášení k protokolu NTLM se nezdařilo  
 Pověření klienta nejsou ve službě platná. Ověřte, že uživatelské jméno a heslo jsou správně nastaveny a odpovídají účtu, který je známý pro počítač, na kterém je služba spuštěná. Protokol NTLM používá zadaná pověření pro přihlášení k počítači služby. I když jsou přihlašovací údaje platné v počítači, kde je spuštěný klient nástroje, přihlášení se nezdaří, pokud nejsou přihlašovací údaje v počítači služby platné.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Dojde k anonymnímu přihlášení NTLM, ale anonymní přihlášení jsou ve výchozím nastavení zakázaná.  
 Při vytváření klienta <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> je vlastnost nastavena na <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, jak je znázorněno v následujícím příkladu, ale ve výchozím nastavení Server nepovoluje anonymní přihlašování. K tomu dochází, protože výchozí hodnota <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> vlastnosti <xref:System.ServiceModel.Security.WindowsServiceCredential> třídy je `false`.  
  
 Následující kód klienta se pokusí povolit anonymní přihlašování (Všimněte si, že výchozí vlastnost je `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Následující kód služby změní výchozí, aby bylo možné povolit anonymní přihlášení ze serveru.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Další informace o zosobnění najdete v tématu [delegování a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Další možností je, že klient je spuštěn jako služba systému Windows, a to pomocí integrovaného systému účtů.  
  
### <a name="other-problems"></a>Jiné problémy  
  
#### <a name="client-credentials-are-not-set-correctly"></a>Přihlašovací údaje klienta nejsou nastavené správně.  
 Ověřování systému Windows používá <xref:System.ServiceModel.Security.WindowsClientCredential> instanci vrácenou <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastností <xref:System.ServiceModel.ClientBase%601> třídy, nikoli <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Následující příklad ukazuje nesprávný příklad.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 V následujícím příkladu je uveden správný příklad.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>Rozhraní SSPI není k dispozici.  
 Následující operační systémy nepodporují ověřování systému Windows, pokud se používají jako server: [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] edice Media Center Edition a [!INCLUDE[wv](../../../../includes/wv-md.md)]Home Edition.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Vývoj a nasazení s různými identitami  
 Pokud vyvíjíte aplikaci na jednom počítači a nasadíte ji na jiný počítač a použijete k ověřování na každém počítači různé typy účtů, může docházet k různým chování. Předpokládejme například, že vyvíjíte aplikaci na počítači se systémem Windows XP pro pomocí `SSPI Negotiated` režimu ověřování. Použijete-li k ověřování pomocí místní uživatelský účet, bude použit protokol NTLM. Po dokončení vývoje aplikace službu nasadíte na počítač s Windows serverem 2003, na kterém běží pod účtem domény. V tomto okamžiku klient nebude moci ověřit službu, protože bude používat protokol Kerberos a řadič domény.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
