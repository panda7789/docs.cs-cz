---
title: Přepsání identity služby kvůli ověřování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 29529115847950dcaba255b0740bc5014557244f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635724"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Přepsání identity služby kvůli ověřování
Standardně nastavit identitu ve službě, protože výběr typu pověření klienta Určuje typ identity v metadatech služby není nutné. Například následující kód konfigurace používá [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu a nastaví `clientCredentialType` atribut pro Windows.  

 Následující fragment webové služby WSDL (Description Language) ukazuje identitu pro koncový bod definovaný dříve. V tomto příkladu je služba spuštěna jako služba v místním prostředí v rámci určitého uživatelského účtu (username@contoso.com), a proto hlavní název (UPN) identity uživatele obsahuje název účtu. Hlavní název uživatele je také označovaný jako přihlašovací jméno uživatele v doméně Windows.  

 Ukázková aplikace, který ukazuje nastavení identity, najdete v části [ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md). Další informace o identitě služby najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Ověřování protokolem Kerberos a Identity  
 Ve výchozím nastavení, když služba je nakonfigurován pro použití přihlašovací údaje Windows [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element, který obsahuje [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) nebo [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) vygenerován element ve schématu WSDL. Pokud služba běží `LocalSystem`, `LocalService`, nebo `NetworkService` účtu, služby (SPN) pro hlavní název je generován výchozí ve formě `host/` \< *název hostitele*> protože Tyto účty mají přístup k datům hlavního názvu služby počítači. Pokud služba běží pod jiným účtem, generuje Windows Communication Foundation (WCF) hlavní název uživatele v podobě \< *uživatelské jméno*>@<*domainName* `>` . K tomu dochází, protože vyžaduje ověřování protokolem Kerberos, že název SPN a UPN zadat do klienta k ověřování.  
  
 Můžete také použít nástroje Setspn.exe Další SPN zaregistrovat u účtu služby v doméně. Hlavní název služby můžete pak použít jako identita služby. Stáhněte si nástroj, najdete v článku [Windows 2000 Resource Kit nástroje: Setspn.exe](https://go.microsoft.com/fwlink/?LinkId=91752). Další informace o tomto nástroji naleznete v tématu [přehled nástroje Setspn](https://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Pokud chcete použít typ přihlašovacích údajů Windows bez vyjednávání, služby uživatelský účet musí mít přístup k hlavní název služby, které je zaregistrované v doméně služby Active Directory. Můžete to udělat následujícími způsoby:  
  
- Použití účtu NetworkService nebo LocalSystem ke spouštění vaší služby. Vzhledem k tomu, že tyto účty mají přístup k počítači hlavní název služby, který je vytvořen, když je počítač připojen k doméně služby Active Directory, WCF automaticky generuje elementu řádné SPN uvnitř koncového bodu služby v služby metadat (WSDL).  
  
- Použijte libovolný účet domény služby Active Directory ke spuštění služby. V takovém případě vytvořte název SPN pro účet domény, což lze provést pomocí nástroje Setspn.exe nástroj. Jakmile vytvoříte název SPN pro účet služby, nakonfigurujte WCF k publikování této hlavní název služby klientům služby prostřednictvím jeho metadat (WSDL). To se provádí nastavením identitě koncového bodu vystavené koncového bodu, buď prostřednictvím konfiguračního souboru aplikace nebo kódu.  
  
 Další informace o SPN, protokol Kerberos a Active Directory, naleznete v tématu [Kerberos technické Supplement pro Windows](https://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Pokud hlavní název služby nebo hlavní název uživatele se rovná prázdný řetězec  
 Pokud nastavíte hlavní název služby nebo hlavní název uživatele rovna prázdný řetězec, stát, řada různých věcí v závislosti na úrovni a ověřování režimu, který používá:  
  
- Pokud používáte zabezpečení na úrovni přenosu, je vybrán LanMan NT (NTLM) authentication.  
  
- Pokud používáte zabezpečení na úrovni zpráv, ověřování se pravděpodobně nezdaří, v závislosti na režimu ověřování:  
  
- Pokud používáte `spnego` režimu a `AllowNtlm` atribut je nastaven na `false`, selhání ověřování.  
  
- Pokud používáte `spnego` režimu a `AllowNtlm` atribut je nastaven na `true`, ověření se nezdaří, pokud hlavní název uživatele je prázdná, ale bude úspěšné, pokud hlavní název služby je prázdný.  
  
- Pokud používáte Kerberos přímé (označované také jako "jednorázové"), ověření se nezdaří.  
  
### <a name="using-the-identity-element-in-configuration"></a>Použití \<identity > v elementu konfigurace  
 Pokud změníte typ přihlašovacích údajů klienta ve vazbě bylo dříve uvedeno na certifikát`,` generovaného WSDL obsahuje Base64 serializovat certifikátů X.509 pro hodnotu identity, jak je znázorněno v následujícím kódu. Toto je výchozí pro všechny typy přihlašovacích údajů klienta jiné než Windows.  

 Můžete změnit hodnotu výchozí identitu služby nebo změňte typ identity pomocí <`identity`> element v konfiguraci nebo nastavením identita v kódu. Následující kód konfigurace nastaví identitou system (DNS) název domény s hodnotou `contoso.com`.  

### <a name="setting-identity-programmatically"></a>Nastavení Identity prostřednictvím kódu programu  
 Vaše služba není nutné explicitně určit identitu, protože WCF automaticky určuje. Ale WCF umožňuje určit identitu, která v koncovém bodě, podle potřeby. Následující kód přidá nový koncový bod služby s konkrétní identitu DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření vlastního ověřovatele Identity](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
