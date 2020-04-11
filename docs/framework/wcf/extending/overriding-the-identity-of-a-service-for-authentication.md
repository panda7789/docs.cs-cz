---
title: Přepsání identity služby kvůli ověřování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: e7273c1e140e52eb37a30b6cabeb9e9a83a6fa2d
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121562"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>Přepsat identitu služby pro ověřování

Obvykle není třeba nastavit identitu ve službě, protože výběr typu pověření klienta určuje typ identity vystavené v metadatech služby. Například následující konfigurační kód používá element [ \<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) a nastaví `clientCredentialType` atribut na systém Windows.  

 Následující fragment jazyka popisu webových služeb (WSDL) zobrazuje identitu dříve definovaného koncového bodu. V tomto příkladu je služba spuštěna jako služba s vlastnímusername@contoso.comhostitelem pod určitým uživatelským účtem ( ), a proto identita hlavního uživatelského jména (UPN) obsahuje název účtu. Hlavní název uživatele je také známý jako přihlašovací jméno uživatele v doméně systému Windows.  

 Ukázková aplikace, která demonstruje nastavení identity, naleznete v [tématu Ukázka identity služby](../samples/service-identity-sample.md). Další informace o identitě služby naleznete v [tématu Identita a ověřování služby](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Ověřování a identita protokolu Kerberos  
 Ve výchozím nastavení je při konfiguraci [ \<služby](../../configure-apps/file-schema/wcf/identity.md) pro použití pověření systému Windows generován v prvku WSDL prvek>identity, který obsahuje [ \<>userPrincipalName>](../../configure-apps/file-schema/wcf/userprincipalname.md) nebo [ \<servicePrincipalName>.](../../configure-apps/file-schema/wcf/serviceprincipalname.md) Pokud `LocalSystem`je služba spuštěna `LocalService`pod `NetworkService` názvem , nebo účet, hlavní název služby (SPN) je generován ve výchozím nastavení ve formě `host/` \< *názvu hostname*> protože tyto účty mají přístup k datům hlavního názvu služby počítače. Pokud je služba spuštěna pod jiným účtem, Windows Communication Foundation \<(WCF) generuje hlavní název uživatele ve formě *username*>@<*domainName*`>`. K tomu dochází, protože ověřování protokolem Kerberos vyžaduje, aby byl klientovi dodán hlavní název uživatele nebo název SPN k ověření služby.  
  
 Pomocí nástroje [Setspn](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10)?redirectedfrom=MSDN) můžete také zaregistrovat další hlavní název služby s účtem služby v doméně. Potom můžete použít hlavní číslo spn jako identitu služby. Další informace o nástroji naleznete v tématu [Setspn Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).  
  
> [!NOTE]
> Chcete-li používat typ pověření systému Windows bez vyjednávání, musí mít uživatelský účet služby přístup k názvu SPN registrovanému v doméně služby Active Directory. To lze provést následujícími způsoby:  
  
- Ke spuštění služby použijte účet NetworkService nebo LocalSystem. Vzhledem k tomu, že tyto účty mají přístup k názvu spn počítače, který je vytvořen, když se počítač připojí k doméně služby Active Directory, WCF automaticky generuje správný prvek SPN uvnitř koncového bodu služby v metadatech služby (WSDL).  
  
- Ke spuštění služby použijte libovolný účet domény služby Active Directory. V takovém případě vytvořte hlavní název služby pro tento účet domény, což můžete provést pomocí nástroje Setspn.exe. Po vytvoření hlavního název služby pro účet služby nakonfigurujte WCF publikovat tento hlavní název služby klientům služby prostřednictvím metadat (WSDL). To se provádí nastavením identity koncového bodu pro exponovaný koncový bod, a to buď prostřednictvím konfiguračního souboru aplikace nebo kódu.  
  
 Další informace o názvech SPN, protokolu Kerberos a službě Active Directory naleznete v [technickém doplňku protokolu Kerberos pro systém Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Když se spn nebo UPN rovná prázdnému řetězci  
 Pokud nastavíte hlavní číslo nebo hlavní zdroj onn na prázdné řetězce, dojde k řadě různých věcí v závislosti na úrovni zabezpečení a režimu ověřování, který se používá:  
  
- Pokud používáte zabezpečení na úrovni přenosu, je vybráno ověřování NT LanMan (NTLM).  
  
- Pokud používáte zabezpečení na úrovni zprávy, ověřování může selhat v závislosti na režimu ověřování:  
  
- Pokud používáte `spnego` režim `AllowNtlm` a atribut `false`je nastaven na , ověřování se nezdaří.  
  
- Pokud používáte `spnego` režim `AllowNtlm` a atribut `true`je nastaven na , ověřování se nezdaří, pokud je hlavní název sítě prázdný, ale úspěšné, pokud je hlavní název služby prázdný.  
  
- Pokud používáte protokol Kerberos direct (označovaný také jako "one-shot"), ověřování se nezdaří.  
  
### <a name="using-the-identity-element-in-configuration"></a>Použití \<prvku> identity v konfiguraci  
 Pokud změníte typ pověření klienta ve`,` vazbě dříve zobrazené certifikátu, pak vygenerovaný WSDL obsahuje certifikát Base64 serializovaný X.509 pro hodnotu identity, jak je znázorněno v následujícím kódu. Toto je výchozí nastavení pro všechny typy pověření klienta než Windows.  

 Můžete změnit hodnotu výchozí identity služby nebo změnit typ identity `identity` pomocí <> prvek v konfiguraci nebo nastavením identity v kódu. Následující konfigurační kód nastaví identitu dns `contoso.com`systému názvů domén s hodnotou .  

### <a name="setting-identity-programmatically"></a>Programové nastavení identity  
 Vaše služba nemusí explicitně zadat identitu, protože WCF ji automaticky určuje. WCF však umožňuje zadat identitu na koncový bod, v případě potřeby. Následující kód přidá nový koncový bod služby s určitou identitou DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření vlastního ověřovatele identity klientů](how-to-create-a-custom-client-identity-verifier.md)
- [Identita a ověřování služby](../feature-details/service-identity-and-authentication.md)
