---
title: Přepsání identity služby kvůli ověřování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: d1c0cc487d8deea7045ee9653d1eae9b73ec864f
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938020"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Přepsání identity služby kvůli ověřování
Obvykle není nutné nastavovat identitu na službě, protože výběr typu přihlašovacích údajů klienta Určuje typ identity, která je vystavena v metadatech služby. Například následující konfigurační kód používá [> prvek\<WSHttpBinding](../../configure-apps/file-schema/wcf/wshttpbinding.md) a nastaví atribut `clientCredentialType` na Windows.  

 Následující fragment kódu jazyka WSDL (Web Services Description Language) zobrazuje identitu dříve definovaného koncového bodu. V tomto příkladu je služba spuštěná jako Samoobslužná služba v rámci konkrétního uživatelského účtu (username@contoso.com), a proto Identita hlavního názvu uživatele (UPN) obsahuje název účtu. Hlavní název uživatele (UPN) je také označován jako přihlašovací jméno uživatele v doméně systému Windows.  

 Ukázkovou aplikaci, která demonstruje nastavení identity, najdete v tématu [Ukázka identity služby](../samples/service-identity-sample.md). Další informace o identitě služby najdete v tématu [identita služby a ověřování](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Ověřování a identita protokolu Kerberos  
 Ve výchozím nastavení platí, že pokud je služba nakonfigurována pro použití pověření systému Windows, [\<prvek identity >](../../configure-apps/file-schema/wcf/identity.md) , který obsahuje [\<userPrincipalName >](../../configure-apps/file-schema/wcf/userprincipalname.md) nebo [\<prvek servicePrincipalName >](../../configure-apps/file-schema/wcf/serviceprincipalname.md) element je vygenerován v jazyce WSDL. Pokud je služba spuštěna pod účtem `LocalSystem`, `LocalService`nebo `NetworkService`, hlavní název služby (SPN) je ve výchozím nastavení generován ve formě `host/`\<*název hostitele*> protože tyto účty mají přístup k datům hlavního názvu počítače. Pokud je služba spuštěná pod jiným účtem, Windows Communication Foundation (WCF) vygeneruje hlavní název uživatele (UPN) ve formátu \<*username*>@<*DomainName*`>`. K tomu dochází, protože ověřování protokolem Kerberos vyžaduje, aby klient zadal hlavní název uživatele (UPN) nebo hlavní název služby, aby mohl ověřit službu.  
  
 Pomocí nástroje Setspn. exe můžete také zaregistrovat další hlavní název služby (SPN) s účtem služby v doméně. Pak můžete jako identitu služby použít hlavní název služby (SPN). Pokud si chcete nástroj stáhnout, přečtěte si téma [Nástroj Windows 2000 Resource Kit: Setspn. exe](https://go.microsoft.com/fwlink/?LinkId=91752). Další informace o tomto nástroji najdete v tématu [Přehled nástroje Setspn](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).  
  
> [!NOTE]
> Chcete-li použít typ přihlašovacích údajů systému Windows bez vyjednávání, musí mít uživatelský účet služby přístup k hlavnímu názvu služby (SPN), který je zaregistrován v doméně služby Active Directory. Můžete to udělat následujícími způsoby:  
  
- Ke spuštění služby použijte účet NetworkService nebo LocalSystem. Vzhledem k tomu, že tyto účty mají přístup k hlavnímu názvu služby počítače, který se vytvoří, když se počítač připojí k doméně služby Active Directory, služba WCF automaticky vygeneruje správný element SPN v rámci koncového bodu služby v metadatech služby (WSDL).  
  
- Ke spuštění služby použijte libovolný účet domény služby Active Directory. V takovém případě vytvořte hlavní název služby (SPN) pro účet domény, který můžete provést pomocí nástroje Setspn. exe Utility. Po vytvoření hlavního názvu služby (SPN) pro účet služby nakonfigurujte WCF pro publikování tohoto hlavního názvu služby do klientů služby prostřednictvím metadat (WSDL). To se provádí nastavením identity koncového bodu pro vystavený koncový bod, a to buď prostřednictvím konfiguračního souboru aplikace, nebo kódu.  
  
 Další informace o SPN, protokolu Kerberos a službě Active Directory najdete v tématu [Kerberos Technical dodatk pro Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Pokud hlavní název služby (SPN) nebo hlavní název uživatele se rovná prázdnému řetězci  
 Pokud nastavíte hlavní název služby (SPN) nebo hlavní název uživatele (UPN) na hodnotu prázdný řetězec, dojde v závislosti na úrovni zabezpečení a používaném režimu ověřování k různým účelům.  
  
- Pokud používáte zabezpečení na úrovni přenosu, zvolí se ověřování NT LanMan (NTLM).  
  
- Pokud používáte zabezpečení na úrovni zpráv, ověřování může selhat v závislosti na režimu ověřování:  
  
- Pokud používáte režim `spnego` a atribut `AllowNtlm` je nastaven na `false`, ověřování se nezdaří.  
  
- Pokud používáte režim `spnego` a atribut `AllowNtlm` je nastaven na `true`, ověřování selže, pokud je hlavní název uživatele prázdný, ale úspěch je prázdný, pokud je hlavní název služby prázdný.  
  
- Pokud používáte protokol Kerberos Direct (označovaný také jako "jeden snímek"), ověření se nepovede.  
  
### <a name="using-the-identity-element-in-configuration"></a>Použití prvku \<> identity v konfiguraci  
 Pokud změníte typ přihlašovacích údajů klienta ve vazbě, která byla dříve zobrazena na certifikát`,` pak vygenerovaný prvek WSDL obsahuje serializovaný certifikát X. 509 pro hodnotu identity, jak je znázorněno v následujícím kódu. Toto je výchozí nastavení pro všechny typy přihlašovacích údajů klienta jiné než Windows.  

 Můžete změnit hodnotu výchozí identity služby nebo změnit typ identity pomocí elementu <`identity`> v konfiguraci nebo nastavením identity v kódu. Následující konfigurační kód nastaví identitu DNS (Domain Name System) s hodnotou `contoso.com`.  

### <a name="setting-identity-programmatically"></a>Nastavování identity prostřednictvím kódu programu  
 Vaše služba nemusí explicitně určovat identitu, protože ji WCF automaticky určí. Služba WCF ale umožňuje v případě potřeby zadat identitu pro koncový bod. Následující kód přidá nový koncový bod služby s konkrétní identitou DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření vlastního ověřovatele identity klientů](how-to-create-a-custom-client-identity-verifier.md)
- [Identita a ověřování služby](../feature-details/service-identity-and-authentication.md)
