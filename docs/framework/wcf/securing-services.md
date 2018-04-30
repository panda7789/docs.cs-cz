---
title: Zabezpečení služeb
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
caps.latest.revision: 28
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: ffc985d528bfdcdd9b62772a8a8ba61823c95e76
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="securing-services"></a>Zabezpečení služeb
Zabezpečení [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby se skládá ze dvou primární požadavky: přenos zabezpečení a autorizaci. (Třetí požadavek, auditování událostí zabezpečení, je popsaný v [auditování](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) Stručně řečeno zabezpečení přenosu zahrnuje ověření (ověření identity služby a klient), důvěrnost (šifrování zpráv) a integrita (digitální podepisování, které zjistit případnou manipulaci). Autorizace je řízení přístupu k prostředkům, například povolení jenom mohou uživatelé s oprávněním ke čtení souboru. Pomocí funkce [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], jsou požadavky na dva primární snadno implementovat.  
  
 S výjimkou produktů <xref:System.ServiceModel.BasicHttpBinding> – třída (nebo [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element v konfiguraci), ve výchozím nastavení pro všechny předdefinované vazby je povolené zabezpečení přenosu. Témata v této části se týkají dva základní scénáře: implementace zabezpečení přenosu a autorizace na intranetu službu hostované na Internetové informační služby (IIS) a implementaci zabezpečení přenosu a autorizace na službě hostované ve službě IIS.  
  
> [!NOTE]
>  Windows XP Home nepodporuje ověřování systému Windows. Proto by nemělo spuštění služby v daném systému.  
  
## <a name="security-basics"></a>Základy zabezpečení  
 Zabezpečení je závislé na *pověření*. Pověření prokáže, že entita je, kdo se vydává. ( *Entity* může být uživatel, proces softwaru, společnost nebo všechno, co lze udělit oprávnění.) Například klient služby zadává *deklarace identity* z *identity*, a přihlašovací údaje prokáže, že deklarace identity nějakým způsobem. Na Typický scénář dojde k výměně přihlašovací údaje. Služby nejprve vytvoří deklaraci identity a prokáže klientovi s pověřením. Naopak klienta provádí deklarace identity a používá přihlašovací údaje ke službě. Pokud obě strany důvěřovat jiný přihlašovací údaje, pak *zabezpečené kontextu* lze navázat, ve které všechny zprávy se vyměňují v důvěrnost, a všechny zprávy přihlášení k ochraně jejich integritu. Po službu vytvoří identitu klienta, můžete pak odpovídat deklarací identity ve přihlašovacích údajů do *role* nebo *členství* ve skupině. V obou případech pomocí roli nebo skupinu, do které patří klienta, službu *autorizuje* klienta provádět omezenou sadu operací na základě role nebo skupiny oprávnění.  
  
## <a name="windows-security-mechanisms"></a>Mechanismy zabezpečení systému Windows  
 Pokud klient a počítače služby jsou i v doméně systému Windows, který vyžaduje i pro přihlášení k síti, přihlašovací údaje jsou poskytovány infrastruktury systému Windows. V takovém případě přihlašovací údaje jsou určeny, když uživatel počítače přihlásí k síti. Každý uživatel a každý počítač v síti musí být ověřený jako náležící do sady důvěryhodných uživatelů a počítačů. V systému Windows, každý uživatel a počítač se také označuje jako *objekt zabezpečení*.  
  
 V doméně systému Windows, který je zálohovaný díky *Kerberos* řadiči řadičem protokolu Kerberos používá schéma podle udělování lístků pro každý objekt zabezpečení. Lístky uděluje řadiče jsou důvěryhodné v jiných předpisech lístek v systému. Vždy, když se pokusí provádět některé operace nebo přístup entity *prostředků* (například soubor nebo adresář na počítači), je zkontrolován the-ticket její platnosti a, pokud se předá, objekt povolen jiný lístek pro operaci. Tato metoda přidělování lístků je efektivnější než alternativní z pokusu o ověření objektu zabezpečení pro všechny operace.  
  
 Mechanismus starší, méně bezpečné použít v doménách systému Windows je NT LAN Manager (NTLM). V případech, kdy nejde použít protokolu Kerberos (obvykle mimo domény systému Windows, například v pracovní skupině) protokol NTLM slouží jako alternativu. NTLM je také k dispozici jako možnost zabezpečení pro službu IIS.  
  
 V systému Windows autorizace funguje přiřazením jednotlivých počítačů a uživatelů pro sadu rolí a skupin. Například musí být každý počítač se systémem Windows nastavit a řídí osoba (nebo skupiny uživatelů) v roli *správce*. Jiné role, je *uživatele*, který má víc omezené sadu oprávnění. Kromě role uživatele přiřazené do skupin. Skupinu umožňuje více uživatelům provádět v na stejný atribut role. V praxi tedy počítače s Windows je spravuje přiřazování uživatelů do skupiny. Například několik uživatelé se dají přiřadit ke skupině uživatelů, počítače a víc omezené sadu uživatelů lze přiřadit ke skupině správců. V místním počítači správce také vytvářet nové skupiny a přiřaďte jiní uživatelé (nebo i další skupiny) do skupiny.  
  
 V počítači se systémem Windows je možné chránit všechny složky v adresáři. To znamená můžete vybrat složku a určovat, kdo má přístup k souborům, a zda můžete zkopírovat soubor nebo (v případě nejvíce privilegovaných) změnit soubor, odstranění souboru, nebo přidat soubory do složky. To se označuje jako řízení přístupu a mechanismus pro něj se označuje jako seznam řízení přístupu (ACL). Při vytváření seznamu ACL, můžete přiřadit přístupová oprávnění pro všechny skupiny nebo skupin, stejně jako jednotlivé členy domény.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Infrastruktury umožňuje použít tyto mechanismy zabezpečení systému Windows. Proto při vytváření služby, který je nasazen na intranetu, a jehož klienti omezen na členy domény systému Windows, zabezpečení je snadno implementovat. Jenom oprávnění uživatelé můžou přihlásit k doméně. Po přihlášení uživatele, řadičem Kerberos umožňuje každého uživatele k navázání zabezpečeného kontexty s jinými počítači nebo aplikace. V místním počítači můžete snadno vytvořit skupiny, a při ochraně určitých složek, tyto skupiny můžete použít k přiřazování přístupovými oprávněními v počítači.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implementace zabezpečení systému Windows na intranetu služby  
 Chcete-li zabezpečit aplikaci spuštěnou výhradně v doméně systému Windows, můžete použít výchozí nastavení zabezpečení buď <xref:System.ServiceModel.WSHttpBinding> nebo <xref:System.ServiceModel.NetTcpBinding> vazby. Ve výchozím nastavení, kdokoli ve stejné doméně systému Windows přístup [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Protože tyto uživatelé přihlásí k síti, jsou důvěryhodné. Zprávy mezi službou a klienta jsou utajení šifrována a podepsaný integritu. Další informace o tom, jak vytvořit službu, která používá zabezpečení systému Windows najdete v tématu [postupy: zabezpečení služby s pověřeními Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autorizace pomocí třídy PrincipalPermissionAttribute  
 Pokud potřebujete omezit přístup k prostředkům v počítači, nejjednodušším způsobem je použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> třídy. Tento atribut umožňuje omezit volání náročných operací služby, které uživatel bude v zadané skupině Windows nebo role, nebo na konkrétního uživatele. Další informace najdete v tématu [postupy: omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Zosobnění  
 Zosobnění je jiný mechanismus, který můžete použít k řízení přístupu k prostředkům. Ve výchozím nastavení spustí službě hostované službou IIS s identitou účtu ASPNET. U účtu ASPNET můžete přístup pouze k prostředkům, pro které má oprávnění. Nicméně je možné nastavit seznam řízení přístupu pro složku vyloučit ASPNET účet služby, ale povolit určité identity pro přístup do složky. Otázka pak stane jak umožnit uživatelům přístup ke složce, pokud uděláte to tak není povoleno účtu ASPNET. Odpověď je použití zosobnění, které je povoleno službu používat pověření klienta pro přístup k určitému prostředku. Dalším příkladem je při přístupu k databázi systému SQL Server, ke kterému mají jenom určitým uživatelům oprávnění. Další informace o použití zosobnění najdete v tématu [postupy: zosobnění klienta ve službě](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) a [delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Zabezpečení Internetu  
 Zabezpečení na Internetu se skládá ze stejné požadavky jako zabezpečení v síti intranet. Služba potřebuje pro svoje přihlašovací údaje k prokázání své pravosti k dispozici, a klienti se musí k prokázání své identity ke službě. Jakmile je ověřené identity klienta, můžete řídit službu kolik přístup k prostředkům má klient. Kvůli heterogenní povaha Internetu, však přihlašovací údaje lišit od těch, které používá v doméně systému Windows. Zatímco zpracovává řadič protokolu Kerberos k ověřování uživatelů v doméně s lístky pro přihlašovací údaje na Internetu, služeb a klientů závisí na některý ze několik různých způsobů, jak přihlašovací údaje k dispozici. Cílem tohoto tématu, ale je k dispozici běžný postup, který umožňuje vytvářet [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] službu, která je přístupné z Internetu.  
  
### <a name="using-iis-and-aspnet"></a>Pomocí služby IIS a ASP.NET  
 Požadavky na zabezpečení Internetu, a na mechanismy k řešení těchto problémů nejsou nové. Služba IIS je webový server společnosti Microsoft pro Internet a obsahuje mnoho funkcí zabezpečení, které řeší tyto problémy; Kromě toho [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] zahrnuje funkce zabezpečení, které [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby můžou používat. Abyste mohli využívat tyto funkce zabezpečení, hostitele [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby ve službě IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Pomocí členství technologie ASP.NET a zprostředkovatelů rolí  
 Technologie ASP.NET obsahuje zprostředkovatele členství a rolí. Zprostředkovatel je databáze párů uživatelské jméno a heslo pro ověření volání, která umožňuje také zadat každou volající přístupová oprávnění. S [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], můžete snadno použít už existující členství a zprostředkovatele rolí prostřednictvím konfigurace. Ukázkové aplikace, která ukazuje na to, najdete v článku [členství a poskytovatel rolí](../../../docs/framework/wcf/samples/membership-and-role-provider.md) ukázka.  
  
### <a name="credentials-used-by-iis"></a>Přihlašovací údaje používané službou IIS  
 Na rozdíl od založenou na protokolu Kerberos řadiče domény systému Windows Internet je prostředí bez jeden řadič pro správu miliony uživatelů přihlásit kdykoli. Místo toho přihlašovací údaje na Internetu jsou nejčastěji ve formě certifikáty X.509 (také označované jako (Secure Sockets Layer) nebo SSL, certifikáty). Tyto certifikáty jsou obvykle vydává *certifikační autority*, může být jiné společnosti, která se zaručuje za pravost certifikát a uživatel je vystavený pro. Chcete-li vystavit služby v síti Internet, je nutné zadat také důvěryhodný certifikát k ověření služby.  
  
 Otázka v tomto okamžiku dojde, jak můžete získat tento certifikát? Jeden z přístupů je přejít na certifikační autority, například Authenticode nebo VeriSign, až budete připraveni k nasazení služby a zakupte certifikát pro vaši službu. Ale pokud jste ve fázi vývoje s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a není ještě připraven pro potvrzení při nákupu certifikát, nástroje a techniky existují pro vytváření certifikátů X.509, které můžete použít k simulaci produkčním nasazení. Další informace najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Režimy zabezpečení  
 Programování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] zabezpečení zahrnuje několik důležitých rozhodovací body. Jeden z Většina základních je volba *režim zabezpečení*. Jsou dva režimy hlavní zabezpečení *režim přenosu* a *režim zprávy*.  
  
 Je třetí režimu, který kombinuje sémantika oba hlavní režimy, *přenosu s režimem přihlašovací údaje zpráva*.  
  
 Režim zabezpečení určuje, jak jsou zabezpečené zprávy, a každou volbu obsahuje výhody a nevýhody, jak je popsáno níže. Další informace o nastavení režimu zabezpečení najdete v tématu [postupy: nastavení režimu zabezpečení](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Režim přenosu  
 Existuje několik vrstev mezi sítí a aplikace. Jedním z nich je *přenosu* vrstvy *,* které spravuje přenos zpráv mezi koncovými body. K dispozici účelu je jenom potřeba, abyste rozuměli tomu, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] používá několik přenosové protokoly, z nichž každý můžete zabezpečit přenos zpráv. (Další informace o přenosech najdete v tématu [přenosy](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Běžně používané protokol je HTTP; Další je TCP. Každý z těchto protokolů můžete zabezpečit přenos mechanismus (nebo mechanismy) konkrétní zprávu protokolu. Například je protokol HTTP zabezpečené pomocí protokolu SSL přes protokol HTTP, často se používá zkratka jako "Protokol HTTPS." Pokud vyberete režim přenosu pro zabezpečení, jsou proto rozhodnete použít mechanismus, jak je stanoveno protokolem. Například, pokud jste vybrali <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte režim zabezpečení na přenos, vybíráte SSL přes protokol HTTP (HTTPS) jako mechanismus zabezpečení. Výhodou režim přenosu je, že je efektivnější než režim zprávy protože zabezpečení je integrované srovnatelně nízké úrovni. Pokud používáte režim přenosu, musí být implementována mechanismus zabezpečení podle specifikace pro přenos, a proto zprávy můžete procházet bezpečně jenom z typu point-to-point prostřednictvím přenosu.  
  
#### <a name="message-mode"></a>Režim zprávy  
 Režim zprávy naopak poskytuje zabezpečení včetně zabezpečení dat v rámci každé zprávy. Pomocí XML a zabezpečení hlavičky SOAP, pověření a dalších dat potřebných k zajištění integrity a důvěrnosti zprávy, které jsou součástí každou zprávu. Všechny zprávy je i zabezpečení dat, je výsledkem projedou na výkon, protože musí být každá zpráva zpracuje jednotlivě. (V režimu přenosu po přenosové vrstvy musí být zabezpečená, všechny zprávy toku volně.) Zabezpečení zpráv má však jednou z výhod přes zabezpečení přenosu: je flexibilnější. To znamená požadavky na zabezpečení nejsou určen přenos. Jakýkoli typ pověření klienta můžete použít k zabezpečení zprávy. (V režimu přenosu přenosový protokol Určuje typ pověření klienta, který můžete použít.)  
  
#### <a name="transport-with-message-credentials"></a>Přenos s pověřením zpráv  
 Třetí režimu kombinují nejlepší zabezpečení přenosu a zprávy. V tomto režimu zabezpečení přenosu umožňuje efektivně zajistit důvěrnost a integrity každé zprávy. Současně všechny zprávy je i jeho data přihlašovacích údajů, což umožňuje zpráva, která má být ověřen. Pomocí ověřování autorizace můžete implementovat také. Tak, že odesílatele, přístup k prostředkům může být povolen (nebo odepřen) podle identity uživatele.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Určení typu pověření klienta a hodnotu přihlašovacích údajů  
 Poté, co jste vybrali režim zabezpečení, můžete také k určení typu pověření klienta. Tento typ přihlašovacích údajů klienta Určuje, jaký typ klient musí použít k vlastnímu ověření serveru.  
  
 Ne všechny scénáře vyžadují typu pověření klienta, ale. Použití protokolu SSL přes protokol HTTP (HTTPS), služba se ověří na klientovi. V rámci tohoto ověřování služby certifikát odeslán do klienta v procesu označovaného jako *vyjednávání*. Přenos zabezpečené protokolem SSL jistotu, že všechny zprávy důvěrné.  
  
 Pokud vytváříte službu, která vyžaduje ověření klienta, zvoleného typu pověření klienta závisí na přenos a vybraný režim. Například pomocí přenosového protokolu HTTP a vybrat režim přenosu k dispozici několik možností, jako je například Digest, Basic a dalších. (Další informace o těchto přihlašovacích údajů typy najdete v tématu [ověřování protokolu HTTP Principy](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 Při vytváření služby v doméně systému Windows, která bude k dispozici pouze jiným uživatelům v síti, je nejjednodušší používat typu pověření klienta systému Windows. Však může také potřebujete poskytovat služby pomocí certifikátu. To je ukázáno v [postup: Zadejte hodnot přihlašovacích údajů klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Hodnot přihlašovacích údajů  
 A *pověření hodnota* je skutečnou pověření používá služby. Po zadání typ přihlašovacích údajů, můžete také nakonfigurovat služby s aktuálními pověřeními. Pokud jste vybrali systému Windows (a služba bude spuštěna v doméně systému Windows), pak nezadáte hodnotu skutečné přihlašovacích údajů.  
  
## <a name="identity"></a>Identita  
 V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], termín *identity* má odlišný význam na server a klienta. Stručně řečeno při kterém běží služba, identity je přiřazený k kontext zabezpečení po ověření. Chcete-li zobrazit skutečné identitu, zkontrolujte <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> vlastnosti <xref:System.ServiceModel.ServiceSecurityContext> třídy. Další informace najdete v tématu [postupy: prozkoumání kontextu zabezpečení](../../../docs/framework/wcf/how-to-examine-the-security-context.md).  
  
 Na klientovi, na rozdíl od identity slouží k ověření služby. V době návrhu, můžete nastavit vývojář klienta [ \<identity >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element na hodnotu získat ze služby. V době běhu klient zkontroluje hodnota elementu proti skutečné identitu služby. Pokud kontrola selže, ukončí klient komunikace. Hodnota může být hlavní název uživatele (UPN), pokud je služba spuštěna pod identitou konkrétní uživatele nebo hlavní název služby (SPN), pokud je služba spuštěna pod účtem počítače. Další informace najdete v tématu [identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). Přihlašovací údaje mohou být také certifikát nebo pole na certifikát, který identifikuje certifikát nalezen.  
  
## <a name="protection-levels"></a>Úrovně ochrany  
 `ProtectionLevel` Vlastnost proběhne několik třídy atributů (například <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> třídy). Úroveň ochrany je hodnota, která určuje, zda zprávy (nebo části zprávy) podporující služby jsou podepsané, podepsané a šifrovaná nebo odeslán bez informace podpisy nebo šifrování. Další informace o vlastnosti najdete v tématu [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md)a programovací příklady najdete v tématu [postupy: nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md). Další informace o návrhu kontrakt služby s `ProtectionLevel` v kontextu, najdete v části [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Princip úrovně ochrany](../../../docs/framework/wcf/understanding-protection-level.md)  
 [Delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Zabezpečení](../../../docs/framework/wcf/feature-details/security.md)  
 [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Postupy: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Postupy: Zabezpečení služby pomocí přihlašovacích údajů Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [Postupy: Nastavení režimu zabezpečení](../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Postupy: Určení typu přihlašovacích údajů klienta](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)  
 [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Postupy: Zosobnění klienta ve službě](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Postupy: Prozkoumání kontextu zabezpečení](../../../docs/framework/wcf/how-to-examine-the-security-context.md)
