---
title: Zabezpečení služeb
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
ms.openlocfilehash: b2ee61d6bad457918f1bd5006dfd7eaa27e46caa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964173"
---
# <a name="securing-services"></a>Zabezpečení služeb
Zabezpečení služby Windows Communication Foundation (WCF) se skládá ze dvou hlavních požadavků: přenos zabezpečení a autorizace. (Třetí požadavek na auditování událostí zabezpečení je popsaný v tématu [auditování](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) V krátkém případě přenos zabezpečení zahrnuje ověřování (ověřování identity služby i klienta), důvěrnost (šifrování zpráv) a integritu (digitální podepisování pro detekci manipulace). Autorizace je řízení přístupu k prostředkům, například umožnění čtení souboru pouze privilegovaným uživatelům. Pomocí funkcí služby WCF jsou tyto dva primární požadavky snadno implementovány.  
  
 S výjimkou <xref:System.ServiceModel.BasicHttpBinding> třídy ( [ \<nebo prvku basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) v konfiguraci) je zabezpečení přenosu povoleno ve výchozím nastavení pro všechny předdefinované vazby. Témata v této části se týkají dvou základních scénářů: implementace přenosu zabezpečení a autorizace na intranetové službě hostované na Internetová informační služba (IIS) a implementace zabezpečení a autorizace přenosu v rámci služby hostované službou IIS.  
  
> [!NOTE]
> Systém Windows XP Home nepodporuje ověřování systému Windows. Proto byste neměli v tomto systému spouštět službu.  
  
## <a name="security-basics"></a>Základy zabezpečení  
 Zabezpečení spoléhá na *přihlašovací údaje*. Přihlašovací údaj prokáže, že entita je na ni deklarace identity. ( *Entita* může být osoba, softwarový proces, společnost nebo cokoli, co může být autorizováno.) Například klient služby provede deklaraci *identity*a přihlašovací údaje tuto deklaraci identity prokáže. V typickém scénáři dojde k výměně přihlašovacích údajů. Nejprve služba vytvoří deklaraci identity a prokáže klientovi s přihlašovacími údaji. Naopak klient provede deklaraci identity a prezentuje přihlašovací údaje službě. Pokud obě strany důvěřují ostatním přihlašovacím údajům, může se zřídit *zabezpečený kontext* , ve kterém se všechny zprávy vyměňují v důvěrnosti, a všechny zprávy jsou podepsané k ochraně své integrity. Poté, co služba vytvoří identitu klienta, může následně přiřadit deklarace identity v přihlašovacích údajích k *roli* nebo *členství* ve skupině. V obou případech pomocí role nebo skupiny, ke které klient patří, autorizuje služba klienta, aby provedl omezené sady operací na základě oprávnění role nebo skupiny.  
  
## <a name="windows-security-mechanisms"></a>Mechanismy zabezpečení systému Windows  
 Pokud klient a počítač služby jsou v doméně systému Windows, která vyžaduje, aby se k síti přihlásili, přihlašovací údaje poskytuje infrastruktura systému Windows. V takovém případě se přihlašovací údaje vytvoří, když se uživatel počítače přihlásí k síti. Každý uživatel a každý počítač v síti musí být ověřen jako patřící k důvěryhodné sadě uživatelů a počítačů. V systému Windows se každý takový uživatel a počítač označuje také jako *objekt zabezpečení*.  
  
 V doméně systému Windows řízené řadičem *protokolu Kerberos* používá řadič Kerberos schéma založené na udělení lístků každému objektu zabezpečení. Lístky, které kontroler uděluje, jsou pro ostatní udělení lístků v systému důvěryhodné. Pokaždé, když se entita pokusí provést určitou operaci nebo získat přístup k *prostředku* (například k souboru nebo adresáři v počítači), je vyhodnocena platnost lístku a v případě, že je předán, je objektu zabezpečení udělen jiný lístek pro tuto operaci. Tato metoda udělování lístků je efektivnější než alternativa při pokusu o ověření objektu zabezpečení pro každou operaci.  
  
 Starší a méně zabezpečený mechanismus, který se používá v doménách Windows, je NT LAN Manager (NTLM). V případech, kdy nelze použít protokol Kerberos (obvykle mimo doménu systému Windows, například v pracovní skupině), lze protokol NTLM použít jako alternativu. Protokol NTLM je také k dispozici jako možnost zabezpečení služby IIS.  
  
 V systému Windows autorizace funguje tak, že přiřazuje každému počítači a uživateli sadu rolí a skupin. Například každý počítač se systémem Windows musí být nastaven a kontrolován uživatelem (nebo skupinou lidí) v roli *správce*. Jinou rolí je *uživatel*, který má mnohem více omezené sady oprávnění. Kromě role jsou uživatelé přiřazeni do skupin. Skupina umožňuje více uživatelům provádět stejnou roli. V praxi je proto počítač se systémem Windows spravován pomocí přiřazování uživatelů do skupin. Například několik uživatelů může být přiřazeno skupině uživatelů počítače a mnohem více omezených skupin uživatelů je možné přiřadit skupině správců. V místním počítači může správce také vytvořit nové skupiny a přiřadit jiným uživatelům (nebo i jiným skupinám) skupinu.  
  
 V počítači se systémem Windows je možné chránit všechny složky v adresáři. To znamená, že můžete vybrat složku a ovládací prvek, který bude mít přístup k souborům, a určit, jestli se může soubor kopírovat, nebo (v případě nejprivilegovaného případu) změnit soubor, odstranit soubor nebo přidat soubory do složky. Tento postup se označuje jako řízení přístupu a mechanismus pro něj je známý jako seznam řízení přístupu (ACL). Při vytváření seznamu ACL můžete přiřadit přístupová oprávnění k libovolné skupině nebo skupinám i jednotlivým členům domény.  
  
 Infrastruktura WCF je navržená tak, aby používala tyto mechanismy zabezpečení systému Windows. Proto pokud vytváříte službu, která je nasazena v intranetu a jejíž klienti jsou omezeni na členy domény systému Windows, zabezpečení je snadno implementováno. K doméně se můžou přihlásit jenom platní uživatelé. Po přihlášení uživatelů řadič protokolu Kerberos umožní každému uživateli vytvořit zabezpečené kontexty s jakýmkoli jiným počítačem nebo aplikací. V místním počítači lze snadno vytvořit skupiny a při ochraně určitých složek je možné tyto skupiny použít k přiřazení přístupových oprávnění k počítači.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implementace zabezpečení Windows na intranetové služby  
 K zabezpečení aplikace, která běží výhradně v doméně systému Windows, můžete použít výchozí nastavení <xref:System.ServiceModel.WSHttpBinding> zabezpečení <xref:System.ServiceModel.NetTcpBinding> nebo vazby. Ve výchozím nastavení má kdokoli na stejné doméně Windows přístup ke službám WCF. Vzhledem k tomu, že se tito uživatelé přihlásili k síti, jsou důvěryhodné. Zprávy mezi službou a klientem jsou zašifrované pro zajištění důvěrnosti a podepsání pro integritu. Další informace o tom, jak vytvořit službu, která používá zabezpečení systému Windows, [naleznete v tématu How to: Zabezpečte službu pomocí pověření](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)systému Windows.  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autorizace pomocí třídy PrincipalPermissionAttribute  
 Pokud potřebujete omezit přístup k prostředkům v počítači, nejjednodušší způsob je použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> třídy. Tento atribut umožňuje omezit vyvolání operací služby tím, že je potřeba, aby uživatel byl v zadané skupině nebo roli systému Windows nebo aby byl konkrétní uživatel. Další informace najdete v tématu [jak: Omezte přístup pomocí třídy](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)PrincipalPermissionAttribute.  
  
### <a name="impersonation"></a>Zosobnění  
 Zosobnění je jiný mechanismus, který můžete použít k řízení přístupu k prostředkům. Ve výchozím nastavení bude služba hostovaná službou IIS běžet pod identitou účtu ASPNET. Účet ASPNET má přístup pouze k prostředkům, ke kterým má oprávnění. Je ale možné nastavit seznam ACL pro složku, aby vyloučí účet služby ASPNET, ale povolil určitým jiným identitám přístup ke složce. Otázka pak povede k tomu, aby měli uživatelé přístup ke složce, pokud není to účet ASPNET povolený. Odpovědí je použití zosobnění, kdy může služba používat přihlašovací údaje klienta pro přístup k určitému prostředku. Dalším příkladem je přístup k databázi SQL Server, ke které mají oprávnění pouze někteří uživatelé. Další informace o použití zosobnění naleznete v tématu [How to: Zosobnit klienta na službě](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) a [delegování a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Zabezpečení na internetu  
 Zabezpečení Internetu se skládá ze stejných požadavků jako zabezpečení na intranetu. Služba potřebuje přihlašovací údaje k prokázání jejího pravosti a klienti musí prokázat svoji identitu službě. Po prověření identity klienta může služba řídit, kolik přístupu má klient k prostředkům. V důsledku heterogenní povahy Internetu se však uvedená pověření liší od těch, které se použily v doméně systému Windows. Vzhledem k tomu, že kontroler protokolu Kerberos zpracovává ověřování uživatelů v doméně pomocí lístků pro přihlašovací údaje, na internetu se služby a klienti spoléhají na některý z několika různých způsobů, jak přihlašovací údaje prezentovat. Cílem tohoto tématu je však poskytnout společný přístup, který umožňuje vytvořit službu WCF, která je přístupná na internetu.  
  
### <a name="using-iis-and-aspnet"></a>Používání služby IIS a ASP.NET  
 Požadavky na zabezpečení Internetu a mechanismy, jak tyto problémy vyřešit, nejsou nové. Služba IIS je webový server společnosti Microsoft pro Internet a má mnoho funkcí zabezpečení, které řeší tyto problémy. Kromě toho ASP.NET zahrnuje funkce zabezpečení, které mohou služby WCF používat. Chcete-li využít tyto funkce zabezpečení, je nutné hostovat službu WCF ve službě IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Používání ASP.NET členství a zprostředkovatelů rolí  
 ASP.NET zahrnuje členství a poskytovatele rolí. Poskytovatel je databáze párů uživatelského jména a hesla pro ověřování volajících, která také umožňují určit přístupová oprávnění každého volajícího. Pomocí WCF můžete snadno použít stávajícího členství a poskytovatele rolí prostřednictvím konfigurace. Ukázkovou aplikaci, která to demonstruje, najdete v ukázce pro [členství a poskytovatele rolí](../../../docs/framework/wcf/samples/membership-and-role-provider.md) .  
  
### <a name="credentials-used-by-iis"></a>Přihlašovací údaje používané službou IIS  
 Na rozdíl od domény Windows zajištěné řadičem protokolu Kerberos je Internet prostředím bez jediného kontroleru pro správu milionů uživatelů přihlašování kdykoli. Místo toho jsou přihlašovací údaje na internetu nejčastěji ve formě certifikátů X. 509 (označovaných také jako SSL (Secure Sockets Layer) nebo SSL, certifikáty). Tyto certifikáty jsou obvykle vydávány *certifikační autoritou*, což může být společnost třetí strany, která ručí za certifikát pravosti certifikátu a osobu, pro kterou byla vydána. K vystavení služby na internetu musíte také k ověření vaší služby uvést takový důvěryhodný certifikát.  
  
 K otázce dojde v tomto okamžiku, jak získáte takový certifikát? Jedním z přístupů k certifikační autoritě třetí strany, jako je Authenticode nebo VeriSign, až budete připraveni nasadit službu a koupit certifikát pro vaši službu. Pokud jste však ve fázi vývoje v rámci služby WCF a ještě nejste připraveni k nákupu certifikátu, nástroje a techniky existují pro vytváření certifikátů X. 509, které můžete použít k simulaci produkčního nasazení. Další informace najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Režimy zabezpečení  
 Programování zabezpečení WCF zahrnuje několik kritických rozhodovacích bodů. Jedním z nejzákladnější je výběr *režimu zabezpečení*. Dva hlavní režimy zabezpečení jsou *Transportní režim* a *režim zpráv*.  
  
 Třetí režim, který kombinuje sémantiku hlavních režimů, je *přenos s režimem přihlašovacích údajů zprávy*.  
  
 Režim zabezpečení určuje, jak jsou zprávy zabezpečeny, a každá z možností má výhody a nevýhody, jak je vysvětleno níže. Další informace o nastavení režimu zabezpečení naleznete v tématu [How to: Nastavte režim](../../../docs/framework/wcf/how-to-set-the-security-mode.md)zabezpečení.  
  
#### <a name="transport-mode"></a>Režim přenosu  
 Mezi sítí a aplikací je několik vrstev. Jedním z nich je *přenosová* vrstva *,* která spravuje přenos zpráv mezi koncovými body. Pro účely současného účelu je potřeba, abyste pochopili, že WCF používá několik přenosových protokolů, z nichž každá může zabezpečit přenos zpráv. (Další informace o přenosech najdete v tématu [přenosy](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Běžně používaný protokol je HTTP; Další je TCP. Každý z těchto protokolů může zabezpečit přenos zpráv mechanismem (nebo mechanismy), které jsou specifické pro daný protokol. Například protokol HTTP je zabezpečený pomocí protokolu SSL přes protokol HTTP, obvykle se zkracuje jako HTTPS. Proto když vyberete transportní režim pro zabezpečení, rozhodli jste se použít mechanismus vydaný protokolem. Pokud například vyberete <xref:System.ServiceModel.WSHttpBinding> třídu a nastavíte její režim zabezpečení na transport, vybíráte jako bezpečnostní mechanismus protokol SSL (https) prostřednictvím protokolu HTTP (https). Výhodou transportního režimu je, že je efektivnější než režim zprávy, protože zabezpečení je integrované na relativně nízké úrovni. Při použití transportního režimu musí být mechanismus zabezpečení implementovaný podle specifikace pro přenos, takže zprávy mohou být zabezpečeny pouze z Point-to-Point přes přenos.  
  
#### <a name="message-mode"></a>Režim zprávy  
 Naproti tomu režim zpráv poskytuje zabezpečení tím, že zahrnuje data zabezpečení jako součást každé zprávy. Pomocí hlaviček zabezpečení XML a SOAP jsou do každé zprávy zahrnuty přihlašovací údaje a další data potřebná k zajištění integrity a důvěrnosti zprávy. Každá zpráva obsahuje data zabezpečení, takže má za následek záruku na výkon, protože každá zpráva musí být zpracována individuálně. (V transportním režimu platí, že jakmile je přenosová vrstva zabezpečená, všechny zprávy budou mít volný tok.) Zabezpečení zpráv má ale jednu výhodu oproti zabezpečení přenosu: je flexibilnější. To znamená, že požadavky na zabezpečení nejsou určeny pro přenos. K zabezpečení zprávy můžete použít libovolný typ přihlašovacích údajů klienta. (V přenosovém režimu určuje transportní protokol typ přihlašovacích údajů klienta, které můžete použít.)  
  
#### <a name="transport-with-message-credentials"></a>Přenos s přihlašovacími údaji zprávy  
 Třetí režim kombinuje nejlepší přenos i zabezpečení zpráv. V tomto režimu se zabezpečení přenosu používá k efektivnímu zajištění důvěrnosti a integrity každé zprávy. Každá zpráva zároveň obsahuje data přihlašovacích údajů, která umožňují ověření zprávy. Pomocí ověřování lze také implementovat autorizaci. Při ověřování odesílatele je možné přístup k prostředkům udělit (nebo odepřít) podle identity odesilatele.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Zadání typu přihlašovacích údajů klienta a hodnoty přihlašovacích údajů  
 Po výběru režimu zabezpečení můžete zadat také typ přihlašovacích údajů klienta. Typ přihlašovacích údajů klienta Určuje typ, který klient musí použít k ověření na serveru.  
  
 Ne všechny scénáře vyžadují typ přihlašovacích údajů klienta, ale. Pomocí protokolu SSL přes protokol HTTP (HTTPS) se služba sama ověřuje pro klienta. V rámci tohoto ověřování se certifikát služby pošle klientovi v procesu s názvem *vyjednávání*. Přenos zabezpečený protokolem SSL zajišťuje důvěrnost všech zpráv.  
  
 Pokud vytváříte službu, která vyžaduje ověření klienta, volba typu pověření klienta závisí na vybraném přenosu a režimu. Například použití přenosu HTTP a výběr režimu přenosu nabízí několik možností, jako jsou například Basic, Digest a další. (Další informace o těchto typech přihlašovacích údajů najdete v tématu [Principy ověřování http](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 Pokud vytváříte službu v doméně systému Windows, která bude k dispozici pouze pro jiné uživatele sítě, nejjednodušší je použít typ přihlašovacích údajů klienta systému Windows. Je ale možné, že budete muset zadat službu s certifikátem. To je znázorněno [v tématu Postupy: Zadejte hodnoty](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)přihlašovacích údajů klienta.  
  
#### <a name="credential-values"></a>Hodnoty přihlašovacích údajů  
 *Hodnota přihlašovacích údajů* je skutečné pověření, které služba používá. Po zadání typu přihlašovacích údajů možná budete muset službu nakonfigurovat se skutečnými přihlašovacími údaji. Pokud jste vybrali Windows (a služba se spustí v doméně Windows), nezadáte skutečnou hodnotu přihlašovacích údajů.  
  
## <a name="identity"></a>Identita  
 V rámci WCF má pojem *identity* různé významy pro server a klienta. V krátké době se při spuštění služby k kontextu zabezpečení po ověření přiřadí identita. Chcete-li zobrazit skutečnou identitu, zkontrolujte <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> <xref:System.ServiceModel.ServiceSecurityContext> a třídy. Další informace najdete v tématu [jak: Projděte si kontext](../../../docs/framework/wcf/how-to-examine-the-security-context.md)zabezpečení.  
  
 Naproti tomu na straně klienta identity slouží k ověření služby. V době návrhu může vývojář klienta nastavit [ \<identitu >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementu na hodnotu získanou ze služby. V době běhu klient kontroluje hodnotu elementu oproti skutečné identitě služby. Pokud se ověření nepovede, klient tuto komunikaci ukončí. Hodnota může být hlavní název uživatele (UPN), pokud služba běží v rámci identity konkrétního uživatele nebo hlavního názvu služby (SPN), pokud se služba spouští pod účtem počítače. Další informace najdete v tématu [Identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). Přihlašovací údaje můžou být taky certifikát nebo pole, které se našlo v certifikátu, který identifikuje certifikát.  
  
## <a name="protection-levels"></a>Úrovně ochrany  
 Vlastnost `ProtectionLevel` se vyskytuje u několika tříd atributů (jako jsou <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> třídy a). Úroveň ochrany je hodnota, která určuje, zda jsou zprávy (nebo části zpráv), které podporují službu, podepsané, podepsané a šifrované nebo odesílané bez signatur nebo šifrování. Další informace o této vlastnosti naleznete v tématu [Principy úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)a pro programování příkladů najdete v tématu [How to: Nastavte vlastnost](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)ProtectionLevel. Další informace o návrhu kontraktu služby s `ProtectionLevel` kontextem najdete v tématu [Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).  
  
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
- [Postupy: Zabezpečení služby pomocí pověření systému Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [Postupy: Nastavení režimu zabezpečení](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
- [Postupy: Zadejte typ přihlašovacích údajů klienta.](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
- [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Postupy: Zosobnění klienta ve službě](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Postupy: Projděte si kontext zabezpečení.](../../../docs/framework/wcf/how-to-examine-the-security-context.md)
