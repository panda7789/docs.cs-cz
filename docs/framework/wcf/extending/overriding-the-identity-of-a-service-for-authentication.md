---
title: Přepsání identity služby kvůli ověřování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 6fbdd7f09c7ae15368972afbce896c5ecb39ccbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Přepsání identity služby kvůli ověřování
Obvykle nemáte nastavit identitu u služby, protože výběr typu pověření klienta Určuje typ identity vystavené v metadatech služby. Například následující kód konfigurace používá [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu a nastaví `clientCredentialType` atribut systému Windows.  
  
  
  
 Následující fragment webové služby popis Language (WSDL) ukazuje identity pro koncový bod předtím definovaný. V tomto příkladu je služba spuštěna jako služba s vlastním hostováním v rámci určitého uživatelského účtu (username@contoso.com), a proto identity hlavní název (UPN) uživatele obsahuje název účtu. Hlavní název uživatele je také známé jako přihlašovací jméno uživatele v doméně systému Windows.  
  
  
  
 Ukázkovou aplikaci, která demonstruje nastavení identity, najdete v části [ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md). Další informace o identitě služby najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Ověřování protokolem Kerberos a Identity  
 Ve výchozím nastavení, pokud služba je nakonfigurovaný na použití pověření systému Windows [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementu, který obsahuje [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) nebo [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element se generuje ve schématu WSDL. Pokud je služba spuštěna pod `LocalSystem`, `LocalService`, nebo `NetworkService` účtu, služby (SPN) pro hlavní název je generována ve výchozím nastavení ve formě `host/` \< *hostname*> protože Tyto účty s přístupem k datům SPN počítače. Pokud služba běží pod jiným účtem, Windows Communication Foundation (WCF) generuje UPN ve formě \< *uživatelské jméno*>@<*domainName* `>` . K tomu dochází, protože ověřování pomocí protokolu Kerberos vyžaduje, aby (UPN) nebo hlavní název služby je nutné zadat klienta k ověřování.  
  
 Můžete taky nástroje Setspn.exe zaregistrovat další SPN se účtu služby v doméně. Potom můžete vytvořit hlavní název služby jako identitu služby. Si můžete stáhnout nástroj [nástroj Windows 2000 Resource Kit: Setspn.exe](http://go.microsoft.com/fwlink/?LinkId=91752). Další informace o tomto nástroji naleznete v tématu [přehled nástroje Setspn](http://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, služby uživatelský účet musí mít přístup k hlavní název služby, která je zaregistrovaná u domény služby Active Directory. Můžete provést těmito způsoby:  
  
-   Použití účtu NetworkService nebo LocalSystem ke spouštění služby. Protože tyto účty mít přístup k počítači hlavní název služby, který je vytvořen, když je počítač připojen k doméně služby Active Directory [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automaticky vygeneruje správné element SPN uvnitř koncový bod služby v metadatech služby (WSDL).  
  
-   Použijte libovolný účet domény služby Active Directory ke spuštění služby. V takovém případě vytvořte název SPN pro účet domény, což lze provést pomocí nástroje Setspn.exe nástroj. Jakmile vytvoříte název SPN pro účet služby, konfigurace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] publikovat tento hlavní název služby klientům služby prostřednictvím jeho metadata (WSDL). To se provádí nastavením identitu koncového bodu pro zveřejněné koncový bod, buď prostřednictvím konfiguračního souboru aplikace nebo kódu.  
  
 Další informace o SPN, protokol Kerberos a služby Active Directory, naleznete v části [Kerberos technické Supplement pro Windows](http://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Pokud hlavní název služby nebo UPN rovná prázdný řetězec  
 Pokud nastavíte hlavní název služby nebo UPN rovna prázdný řetězec, situace, počet různých věcí v závislosti na úrovni a ověřování režim zabezpečení používá:  
  
-   Pokud používáte zabezpečení na úrovni přenosu, je zvolen ověřování LanMan NT (NTLM).  
  
-   Pokud používáte úroveň zabezpečení zpráv, může selhat ověřování, v závislosti na režim ověřování:  
  
-   Pokud používáte `spnego` režimu a `AllowNtlm` je atribut nastaven na `false`, ověřování selže.  
  
-   Pokud používáte `spnego` režimu a `AllowNtlm` je atribut nastaven na `true`, ověření nezdaří, pokud hlavní název uživatele je prázdný, ale bude úspěšné, pokud hlavní název je prázdný.  
  
-   Pokud používáte přímo pomocí protokolu Kerberos (také označované jako "jednorázové"), ověření se nezdaří.  
  
### <a name="using-the-identity-element-in-configuration"></a>Pomocí \<identity > Element v konfiguraci  
 Pokud změníte typ pověření klienta vazba dříve zobrazí certifikát`,` pak generovaného WSDL obsahuje Base64 serializovat certifikátů X.509 pro hodnotu identity, jak je znázorněno v následujícím kódu. Toto je výchozí nastavení pro všechny typy pověření klienta než Windows.  
  
  
  
 Můžete změnit hodnotu výchozí identitu služby nebo změňte typ identity pomocí <`identity`> element v konfiguraci nebo nastavení identity v kódu. Následující kód konfigurace nastaví identitu domain name system (DNS) s hodnotou `contoso.com`.  
  
  
  
### <a name="setting-identity-programmatically"></a>Nastavení Identity prostřednictvím kódu programu  
 Služby není nutné explicitně zadat svou identitu, protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automaticky určuje ho. Ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vám umožní určit identity na koncový bod, pokud je to nutné. Následující kód přidá nový koncový bod služby s konkrétní identity DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření vlastního ověřovatele identity klientů](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
