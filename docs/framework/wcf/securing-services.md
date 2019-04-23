---
title: Zabezpečení služeb
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
ms.openlocfilehash: 65d4f2858c2be4c2a6872f96ef3739bb16253d74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157667"
---
# <a name="securing-services"></a>Zabezpečení služeb
Zabezpečení služby Windows Communication Foundation (WCF) se skládá ze dvou primárních požadavků: přenos zabezpečení a autorizace. (Třetí požadavek auditování událostí zabezpečení, je popsaná v [auditování](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) Stručně řečeno přenos zabezpečení zahrnuje ověření (ověření identity klienta a služby), důvěrnosti (šifrování zpráv) a integritu (digitální podpis umožňuje zjistit případnou manipulaci). Autorizace je řízení přístupu k prostředkům, například povolení pouze uživatelé s oprávněním ke čtení souboru. Pomocí funkce služby WCF, dva primární požadavky se snadno implementují.  
  
 S výjimkou produktů <xref:System.ServiceModel.BasicHttpBinding> třídy (nebo [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) v elementu konfigurace), ve výchozím nastavení pro všechny předdefinovaných vazeb je povoleno zabezpečení přenosu. Témata v této části se týkají dva základní scénáře: implementace přenos zabezpečení a autorizace pro služby intranetu hostované v Internetové informační služby (IIS) a implementaci zabezpečení přenosu a autorizace ve službě hostované ve službě IIS.  
  
> [!NOTE]
>  Windows XP Home nepodporuje ověřování Windows. Proto byste neměli spouštět služby v daném systému.  
  
## <a name="security-basics"></a>Základy zabezpečení  
 Zabezpečení spoléhá na *pověření*. Přihlašovací údaj prokáže, že entita je, kdo se vydává. ( *Entity* může být uživatel, proces softwaru, společnost nebo cokoli, co je možné autorizovat.) Například klient služby zadává *deklarace identity* z *identity*, a přihlašovací údaje, které tuto žádost nějakým způsobem prokáže vaše oprávnění. V rámci typického scénáře dojde k výměnou přihlašovacích údajů. Služba nejdřív vytvoří deklaraci identity a prokáže vaše oprávnění ke klientovi s přihlašovacími údaji. Naopak klient vytvoří deklaraci identity a uvede přihlašovacích údajů ke službě. Pokud obě strany vztahu důvěryhodnosti druhé strany přihlašovací údaje o *zabezpečené kontextu* lze navázat, v které všechny zprávy se vyměňují v důvěrnost a všechny zprávy přihlášení k ochraně jejich integritu. Poté, co služba vytvoří identitu klienta, může pak odpovídat deklarace identity v přihlašovacích údajích k *role* nebo *členství* ve skupině. V obou případech použití role nebo skupiny, ke kterému patří klient, služba *autorizuje* klienta vykonávat omezenou sadu operací na základě role nebo skupiny oprávnění.  
  
## <a name="windows-security-mechanisms"></a>Mechanismy zabezpečení Windows  
 Pokud klient i počítač služby jsou v doméně Windows, který vyžaduje pro přihlášení k síti, přihlašovací údaje zajišťují infrastrukturu Windows. V takovém případě přihlašovací údaje jsou vytvořeny při přihlášení uživatele počítače k síti. Každého uživatele a každý počítač v síti musí být ověření jako patřící do sady důvěryhodných uživatelů a počítačů. V systému Windows, každý takový uživatel a počítač se také označuje jako *objektu zabezpečení*.  
  
 V doméně Windows se opírá *Kerberos* řadiči, řadič Kerberos používá schéma podle udělování lístků pro každý objekt zabezpečení. Lístky uděluje kontroleru důvěřuje jiné předpisech lístek v systému. Vždy, když se pokusí entity provádět některé operace nebo přístupu *prostředků* (například soubor nebo adresář v počítači), je zkontrolován-the-ticket, jeho platnost, a pokud předá, objekt zabezpečení povolen jiného lístek pro operaci. Tato metoda přidělování lístků je mnohem efektivnější než pokusu o ověření objektu zabezpečení pro každou operaci.  
  
 Mechanismus starší, méně zabezpečené, používá v doménách Windows je NT LAN Manager (NTLM). V případech, kdy nejde použít protokol Kerberos (obvykle mimo domény Windows, například v pracovní skupině) NTLM může sloužit jako alternativu. NTLM je také k dispozici možnost zabezpečení pro službu IIS.  
  
 V systému Windows autorizace funguje tak, že přiřazení jednotlivých počítačů a uživatelů na sadu rolí a skupin. Například musí být každý počítač s Windows nastavení a řídí osoba (nebo skupiny uživatelů) v roli *správce*. Jiné role, je *uživatele*, který má mnohem více omezenou sadu oprávnění. Kromě roli jsou uživatelům přiřadit skupinám. Skupiny umožňuje více uživatelům provádět ve stejné roli. V praxi proto se počítače s Windows je spravována prostřednictvím přiřazování uživatelů do skupin. Například několika uživatelům je možné přiřadit ke skupině uživatelů, počítače a mnohem víc omezenou sadu uživatelů je možné přiřadit ke skupině správců. Na místním počítači může správce také vytvářet nové skupiny a přiřadit ke skupině Další uživatelé (nebo i jiné skupiny).  
  
 Na počítači se systémem Windows je možné chránit všechny složky v adresáři. To znamená můžete vybrat složku a určovat, kdo může přistupovat k souborům, a jestli můžete zkopírovat soubor nebo (v případě nejvíce privilegovaných) změnit soubor, odstranění souboru nebo přidejte soubory do složky. To se označuje jako řízení přístupu a mechanismus pro něj se označuje jako seznam řízení přístupu (ACL). Při vytváření seznamu ACL, můžete přiřadit přístupová oprávnění pro všechny skupiny nebo skupiny, stejně jako jednotlivé členy domény.  
  
 Infrastruktura WCF je navržen pro použití tyto mechanismy zabezpečení Windows. Proto pokud vytváříte službu, která je nasazena na intranetu a jejichž klienti jsou omezeny na členy domény Windows, zabezpečení je snadno implementovat. Pouze platní uživatelé můžou přihlásit k doméně. Po přihlášení uživatele, umožňuje kontroleru Kerberos každý uživatel k navázání zabezpečené kontexty pomocí libovolného počítače nebo aplikace. Na místním počítači můžete snadno vytvořit skupiny a při ochraně určitých složek, tyto skupiny je možné přiřadit přístupová oprávnění v počítači.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implementace zabezpečení Windows na intranetu služby  
 Pro zabezpečení aplikace, na kterém běží výhradně v doméně Windows, můžete použít výchozí nastavení zabezpečení buď <xref:System.ServiceModel.WSHttpBinding> nebo <xref:System.ServiceModel.NetTcpBinding> vazby. Ve výchozím nastavení všem uživatelům ve stejné doméně Windows mají přístup ke službám WCF. Tito uživatelé mají přihlášení k síti, že jsou důvěryhodná. Zprávy mezi službou a klienta jsou šifrované utajení a zaregistrovali integrity. Další informace o tom, jak vytvořit službu, která používá zabezpečení Windows, naleznete v tématu [jak: Zabezpečení služby pomocí pověření Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autorizace pomocí třídy PrincipalPermissionAttribute  
 Pokud potřebujete omezit přístup k prostředkům v počítači, nejjednodušší způsob je použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> třídy. Tento atribut umožňuje omezit volání operací služby tak náročné, které bude uživatel v zadané skupině Windows nebo role, nebo na konkrétního uživatele. Další informace najdete v tématu [jak: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Zosobnění  
 Zosobnění je jiný mechanismus, který můžete použít k řízení přístupu k prostředkům. Ve výchozím nastavení poběží služby hostované službou IIS v části identita účtu ASPNET. Účtu ASPNET přístupná pouze na prostředky, pro které má oprávnění. Nicméně je možné nastavit seznam ACL pro složku vyloučit ASPNET účet služby, ale povolit některé jiné identity pro přístup do složky. Pak dotaz se změní na tom, jak povolit uživatelům přístup ke složce, pokud k tomu nemá povolené účtu ASPNET. Odpověď je použití zosobnění, kterým služba může používat přihlašovací údaje klienta pro přístup k určitému prostředku. Dalším příkladem je při přístupu k databázi serveru SQL Server, ke kterým pouze určití uživatelé mají oprávnění. Další informace o použití zosobnění naleznete v tématu [jak: Zosobnění klienta ve službě](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) a [delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Zabezpečení na Internetu  
 Zabezpečení na Internetu se skládá ze stejné požadavky na zabezpečení v intranetu. Služba potřebuje prezentovat svoje přihlašovací údaje k prokázání své pravosti a klienti se musí k prokázání své identity ve službě. Jakmile prokazuje identity klienta služby můžete řídit vyjadřuje rozsah přístupu k prostředkům má klient. Ale protože heterogenní potřebujeme Internetu přihlašovací údaje se liší od používaných v doméně Windows. Že Kerberos kontroler obsluhuje ověřování uživatelů v doméně s lístky pro přihlašovací údaje na Internetu, služeb a klientů závisí na některou z několika různými způsoby prezentovat přihlašovací údaje. Cílem tohoto tématu, ale prezentovat běžným přístupem, která umožňuje vytvoření služby WCF, který je přístupný na Internetu.  
  
### <a name="using-iis-and-aspnet"></a>Pomocí služby IIS a ASP.NET  
 Požadavky na zabezpečení Internetu a mechanismy k řešení těchto problémů, nejsou nové. Služba IIS je webový server společnosti Microsoft pro Internet a obsahuje mnoho funkcí zabezpečení, které řeší tyto problémy. Kromě toho [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] má bezpečnostní funkce, které můžete použít služby WCF. Abyste mohli využívat tyto funkce zabezpečení, hostování služby WCF ve službě IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Pomocí členství technologie ASP.NET a zprostředkovatele rolí  
 Technologie ASP.NET obsahuje zprostředkovatele členství a rolí. Zprostředkovatel je databáze párů jméno/heslo uživatele za účelem ověřování totožnosti volajícím, které také umožňuje určit jednotliví volající přístupová oprávnění. S použitím technologie WCF můžete snadno použít existující členství a poskytovatel rolí prostřednictvím konfigurace. Ukázková aplikace, který ukazuje to, najdete v článku [členství a poskytovatel rolí](../../../docs/framework/wcf/samples/membership-and-role-provider.md) vzorku.  
  
### <a name="credentials-used-by-iis"></a>Přihlašovací údaje používaný službou IIS  
 Na rozdíl od domény Windows se opírá o kontroleru pomocí protokolu Kerberos je Internetu prostředí bez jedním řadičem pro správu milionům uživatelů přihlásit kdykoli. Místo toho přihlašovací údaje na Internetu jsou nejčastěji ve formě certifikátů X.509 (označované také jako (Secure Sockets Layer), nebo, pomocí certifikátů SSL). Tyto certifikáty jsou obvykle vystavené *certifikační autority*, což může být společnost třetích stran, která se zaručuje za pravosti certifikát a osoby se vystavil. Pokud chcete zpřístupnit službu na Internetu, musíte také zadat důvěryhodný certifikát k ověření vaší služby.  
  
 Dotaz v tomto okamžiku dojde, jak můžete získat tento certifikát? Jedním z přístupů je použít třetích stran certifikační autority, jako je například Authenticode nebo VeriSign, až budete připraveni k nasazení služby a zakupte certifikát pro vaši službu. Nicméně pokud jsou ve fázi vývoje s použitím technologie WCF a není ještě připraven k potvrzení nákupu certifikát, nástroje a techniky pro vytváření certifikátů X.509, který můžete simulovat produkční nasazení. Další informace najdete v tématu [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Režimy zabezpečení  
 Programování zabezpečení WCF zahrnuje několik důležitých rozhodnutí body. Jednou z nejvíce základní je volba *režim zabezpečení*. Jsou dva režimy významný bezpečnostní *režim přenosu* a *režim zprávy*.  
  
 Je třetí režimu, který kombinuje sémantiku oba hlavní režimy *přenosu s režimem pověření zprávy*.  
  
 Režim zabezpečení určuje, jak jsou zabezpečené zprávy, a každou volbu má své výhody a nevýhody, jak je popsáno níže. Další informace o nastavení režimu zabezpečení rozhraní najdete v tématu [jak: Nastavení režimu zabezpečení rozhraní](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Režim přenosu  
 Existuje několik vrstev mezi sítě a aplikace. Jedním z nich je *přenosu* vrstvy *,* která spravuje přenos zpráv mezi koncovými body. Pro tento účel k dispozici je jenom nutné pochopit, WCF, používá několik protokolů přenosu, z nichž každá může zabezpečený přenos zpráv. (Další informace o přenosech najdete v tématu [přenosy](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Běžně používané protokol je HTTP; Další je TCP. Každá z těchto protokolů můžete svázat konkrétní přenos mechanismus (nebo mechanismy) zprávy protokolu. Například protokolu HTTP je zabezpečená pomocí protokolu SSL přes protokol HTTP, často se zkracuje jako "HTTPS". Při výběru režimu přepravy pro zabezpečení jsou proto rozhodnete použít mechanismus, určený protokol. Například, pokud jste vybrali <xref:System.ServiceModel.WSHttpBinding> třídy a nastavit jeho režim zabezpečení přenosu, vybíráte SSL přes HTTPS (HTTP) jako mechanismus zabezpečení. Výhodou režim přenosu je, že je efektivnější než režim zprávy zabezpečení je integrovaná se poměrně nízké úrovni. Při použití režimu přenosu, podle specifikace pro přenos musí implementovat mechanismus zabezpečení, a proto zprávy můžete tok bezpečně pouze z typu point-to-point prostřednictvím přenosu.  
  
#### <a name="message-mode"></a>Režim zprávy  
 Režim zprávy naproti tomu poskytuje zabezpečení včetně údajů o zabezpečení v rámci každé zprávy. Použití XML a SOAP záhlaví zabezpečení, přihlašovací údaje a další data potřebné k zajištění, že jsou součástí každé zprávy integritu a důvěrnost zprávy. Každá zpráva obsahuje data zabezpečení, takže je výsledkem linka na výkon, protože každá zpráva musí být zpracovány samostatně. (V režimu přenosu, jakmile je zabezpečené přenosové vrstvy, všechny zprávy tok volně.) Zabezpečení zpráv má však výhodou přes zabezpečení přenosu: je flexibilnější. To znamená nejsou určuje požadavky na zabezpečení přenosu. Jakýkoli typ pověření klienta můžete použít k zabezpečení zprávy. (V režimu přenosu, přenosový protokol Určuje typ pověření klienta, které můžete použít.)  
  
#### <a name="transport-with-message-credentials"></a>Přenos s přihlašovacími údaji zprávy  
 Třetí režimu kombinuje to nejlepší z zabezpečení přenosu a zprávy. V tomto režimu se zabezpečení přenosu slouží k zajištění efektivní důvěrnost a integrita všechny zprávy. Všechny zprávy ve stejnou dobu, zahrnuje jeho přihlašovacích údajů data, která umožňuje zpráva, která má být ověřen. S ověřováním může být také implementováno autorizace. Zkontrolovat pracovník ostrahy odesílatele, přístup k prostředkům může být povolen (nebo odepřen) podle identity uživatele.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Určení typu pověření klienta a hodnoty přihlašovacích údajů  
 Po výběru režim zabezpečení, můžete také k určení typu pověření klienta. Typ přihlašovacích údajů klienta Určuje, jaký typ může klient musí používat své autentizaci k serveru.  
  
 Některé scénáře vyžadují typu pověření klienta, ale. Použití protokolu SSL přes HTTPS (HTTP), služba se ověří na klienta. Jako součást tohoto ověřování služby certifikát odeslán do klienta v procesu nazývaného *vyjednávání*. Přenos zabezpečené protokolem SSL zajišťuje, aby byly všechny zprávy důvěrné.  
  
 Pokud vytváříte službu, která vyžaduje ověření klienta, podle vašeho výběru typu pověření klienta závisí na přenos a vybrán režim. Například použití přenosového protokolu HTTP a výběru režimu přepravy poskytuje několik možností, jako je například Basic, Digest a další. (Další informace o těchto typů přihlašovacích údajů naleznete v tématu [Princip ověřování HTTP](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 Při vytváření služby v doméně Windows, které budou k dispozici pouze pro jiné uživatele v síti, je nejjednodušší použití typu pověření klienta Windows. Však budete také muset poskytovat služby pomocí certifikátu. To je ukázáno v [jak: Zadání hodnot přihlašovacích údajů klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Hodnot přihlašovacích údajů  
 A *přihlašovacích údajů hodnotu* je skutečná služba používá přihlašovacích údajů. Po zadání typu přihlašovacích údajů, můžete také nakonfigurovat samotné přihlašovací údaje služby. Pokud jste vybrali Windows (a služba se spustí v doméně Windows), nelze zadat hodnotu skutečné přihlašovací údaje.  
  
## <a name="identity"></a>Identita  
 Ve službě WCF termín *identity* má různé významy k serveru a klienta. Stručně řečeno při spuštění služby, identitu, která se přiřadí kontextu zabezpečení po ověření. Chcete-li zobrazit skutečnou identitu, zkontrolujte <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> vlastnosti <xref:System.ServiceModel.ServiceSecurityContext> třídy. Další informace najdete v tématu [jak: Prozkoumání kontextu zabezpečení](../../../docs/framework/wcf/how-to-examine-the-security-context.md).  
  
 Naproti tomu na klientovi, identita se používá k ověření služby. V době návrhu, můžete nastavit určitého vývojáře klienta [ \<identity >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element hodnotou získanou ze služby. V době běhu klient zkontroluje hodnotu prvku na skutečnou identitu služby. Pokud kontrola selže, klient ukončí komunikace. Hodnota může být hlavní název uživatele (UPN), pokud je služba spuštěna pod identitou konkrétní uživatele nebo hlavní název služby (SPN), pokud je služba spuštěna pod účtem počítače. Další informace najdete v tématu [identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). Přihlašovací údaje, které mohou být také certifikát nebo pole na certifikát, který identifikuje tento certifikát.  
  
## <a name="protection-levels"></a>Úrovně ochrany  
 `ProtectionLevel` Vlastnost probíhá na několika třídy atributů (jako <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> třídy). Úroveň ochrany je hodnota, která určuje, zda zprávy (nebo částí zprávy), které podporují službu jsou podepsané, podepsaný a zašifrovaný nebo odeslán bez informace o podpisy nebo šifrování. Další informace o vlastnosti najdete v tématu [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md)a programovací příklady najdete v tématu [jak: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md). Další informace o navrhování kontrakt služby s `ProtectionLevel` v kontextu, najdete v článku [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Princip úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)
- [Delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md)
- [Zabezpečení](../../../docs/framework/wcf/feature-details/security.md)
- [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Postupy: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [Postupy: Nastavení režimu zabezpečení](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
- [Postupy: Určení typu pověření klienta](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
- [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Postupy: Zosobnění klienta ve službě](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Postupy: Prozkoumání kontextu zabezpečení](../../../docs/framework/wcf/how-to-examine-the-security-context.md)
