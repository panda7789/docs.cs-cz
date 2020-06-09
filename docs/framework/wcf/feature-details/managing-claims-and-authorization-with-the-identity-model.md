---
title: Správa deklarací a autorizace s modelem identity
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- WCF security
- claims [WCF], managing with the Identity Model
- claims [WCF]
- authorization [WCF], managing with the Identity Model
ms.assetid: 099defbb-5d35-434e-9336-1a49b9ec7663
ms.openlocfilehash: f9138102435aab07e5c1771ce5dba85bacbcac99
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586348"
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Správa deklarací a autorizace s modelem identity
Autorizace je proces určení, které entity mají oprávnění ke změně, zobrazení nebo jinému přístupu k prostředku počítače. Například v podniku můžou mít přístup jenom správci k souborům svých zaměstnanců. Windows Communication Foundation (WCF) podporuje dva mechanismy pro provádění zpracování autorizace. První mechanismus umožňuje řídit autorizaci pomocí stávajících konstrukcí modulu CLR (Common Language Runtime). Druhý je model založený na deklaracích, který se označuje jako *model identity*. WCF používá model identity k vytváření deklarací z příchozích zpráv; Třídy modelu identity se dají rozšířit tak, aby podporovaly nové typy deklarací pro vlastní autorizační schémata. Toto téma představuje přehled hlavních konceptů programování funkce modelu identity a také seznam nejdůležitějších tříd, které tato funkce používá.  
  
## <a name="identity-model-scenarios"></a>Scénáře modelu identity  
 Následující scénáře reprezentují použití modelu identity.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Scénář 1: Podpora deklarací identity, rolí a skupin  
 Uživatelé odesílají zprávy na webovou službu. Požadavky na řízení přístupu webové služby používají identitu, role nebo skupiny. Odesílatel zprávy je namapován na sadu rolí nebo skupin. Role nebo informace o skupině se používají k provádění kontrol přístupu.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Scénář 2: podpora bohatých deklarací identity  
 Uživatelé odesílají zprávy na webovou službu. Požadavky na řízení přístupu webové služby vyžadují širší model než identita, role nebo skupiny. Webová služba Určuje, jestli má daný uživatel přístup k určitému chráněnému prostředku pomocí rozsáhlého modelu založeného na deklaracích. Jeden uživatel může například číst určité informace, například informace o mzdě, ke kterým nemají přístup jiní uživatelé.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Scénář 3: mapování různorodých deklarací identity  
 Uživatel pošle zprávu webové službě. Uživatel může zadat své přihlašovací údaje několika různými způsoby: certifikát X. 509, token uživatelského jména nebo token protokolu Kerberos. Webová služba je nutná k provádění kontrol řízení přístupu stejným způsobem bez ohledu na typ přihlašovacích údajů uživatele. Pokud se v průběhu času podporují další typy přihlašovacích údajů, měl by se systém podle toho rozvinout.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Scénář 4: určení přístupu k více prostředkům  
 Webová služba se pokusí o přístup k více prostředkům. Služba určuje, ke kterým chráněným prostředkům má daný uživatel přístup, porovnáním deklarací identity přidružených k uživateli a deklarací identity potřebných pro přístup k prostředku.  
  
## <a name="identity-model-terms"></a>Výrazy modelu identity  
 Následující seznam popisuje klíčové pojmy, které se používají k popisu konceptů modelu identity.  
  
 Zásady autorizace  
 Sada pravidel pro mapování sady vstupních deklarací na sadu výstupních deklarací identity. Vyhodnocením zásad autorizace se načtou sady deklarací, které se přidají do kontextu vyhodnocení, a následně i kontext autorizace.  
  
 Autorizační kontext  
 Sada deklarací identity a nula nebo více vlastností. Výsledek vyhodnocení jedné nebo více autorizačních zásad.  
  
 Deklarovat  
 Kombinace typu deklarace identity, práva a hodnoty.  
  
 Sada deklarací identity  
 Sada deklarací vydaných konkrétním vystavitelem.  
  
 Typ deklarace identity  
 Druh deklarace identity. Deklarace identity definované rozhraním API modelu identity jsou vlastnosti <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> třídy. Příklady typů deklarací poskytovaných systémem jsou,,,,,, <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.System%2A> ,, <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A> a <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A> <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A> .  
  
 Kontext vyhodnocení  
 Kontext, ve kterém jsou vyhodnoceny zásady autorizace. Obsahuje vlastnosti a sady deklarací. Se bude základem autorizačního kontextu po dokončení vyhodnocení.  
  
 Deklarace identity  
 Deklarace identity, jejíž právo je identity.  
  
 Vystavitel  
 Sada deklarací, která obsahuje alespoň jednu deklaraci identity a je považována za vydanou jinou sadu deklarací.  
  
 Vlastnosti  
 Sada informací přidružených k kontextu vyhodnocení nebo autorizačnímu kontextu.  
  
 Chráněný prostředek  
 Něco v systému, které se dá použít, nebo jinak manipulovat, pokud jsou určité požadavky nejdřív splněné.  
  
 Vpravo  
 Schopnost nad prostředkem. Práva definovaná rozhraním API modelu identity jsou vlastnosti <xref:System.IdentityModel.Claims.Rights> třídy. Příkladem oprávnění poskytovaných systémem jsou <xref:System.IdentityModel.Claims.Rights.Identity%2A> a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> .  
  
 Hodnota  
 Něco, co je požadováno právo.  
  
## <a name="claims"></a>Deklarace identity  
 Model identity je systém založený na deklaracích. Deklarace identity popisují možnosti spojené s některými entitami v systému, často uživatel tohoto systému. Sadu deklarací přidružených k dané entitě lze představit jako klíč. Konkrétní deklarace definují tvar tohoto klíče, podobně jako fyzický klíč, který se používá k otevření zámku v dvířek. K získání přístupu k prostředkům se používají deklarace identity. Přístup k danému chráněnému prostředku je určený porovnáním deklarací identity potřebných pro přístup k tomuto prostředku s deklaracemi přidruženými k entitě, která se pokouší o přístup.  
  
 Deklarace je výrazem práva s ohledem na konkrétní hodnotu. Právo může být něco podobného jako "čtení", "Write" nebo "Execute". Hodnota může být databáze, soubor, poštovní schránka nebo vlastnost. Deklarace identity mají také typ deklarace identity. Kombinace typu deklarace identity a práva poskytuje mechanismus pro určení schopností v souvislosti s hodnotou. Například deklarace identity typu "File", s pravou "číst" nad hodnotou "biografie. doc", označuje, že entita, ke které je tato deklarace identity přidružena, má přístup pro čtení do souboru biografie. doc. Deklarace identity typu "Name" s pravou "PossessProperty" nad hodnotou "Martin" označuje, že entita, ke které je tato deklarace identity přidružena, má vlastnost Name s hodnotou "Martin".  
  
 I když jsou v rámci modelu identity definované různé typy deklarací identity a práva, je systém rozšiřitelný a umožňuje různým systémům sestavovat na infrastruktuře infrastruktury modelu identity, aby bylo možné definovat další typy deklarací identity a oprávnění podle potřeby.  
  
### <a name="identity-claims"></a>Deklarace identity  
 Jedním z nich je právo identity. Deklarace identity, které mají tuto pravou, vytvoří příkaz o identitě entity. Například deklarace identity typu "hlavní název uživatele" (UPN) s hodnotou " someone@example.com " a právem identity označuje konkrétní identitu v konkrétní doméně.  
  
#### <a name="system-identity-claim"></a>Deklarace identity systému  
 Model identity definuje jednu deklaraci identity: System. Deklarace identity systému indikuje, že entita je aktuální aplikace nebo systém.  
  
### <a name="sets-of-claims"></a>Sady deklarací identity  
 Model deklarací identity, které představují identitu, je důležitý, protože deklarace identity jsou vždy vydávány určitou entitou v systému, a to i v případě, že je tato entita nakonec konceptem "samy". Deklarace jsou seskupené dohromady jako sada a každá sada má vystavitele. Vystavitel je pouze sada deklarací identity. Taková rekurzivní relace musí nakonec končit a každá sada deklarací může být svým vlastním vystavitelem.  
  
 Následující obrázek ukazuje příklad tří sad deklarací identity, u nichž jedna sada deklarací má jako vystavitele jinou sadu deklarací identity, která zase má jako vystaviteli nastavenou deklaraci identity systému. Sady deklarací identity proto tvoří hierarchii, která může být libovolně hluboká.  
  
 ![Sady deklarací v rámci hierarchie.](./media/managing-claims-and-authorization-with-the-identity-model/claims-sets-hierarchy.gif)  
  
 Několik sad deklarací může mít stejnou vydávající sadu deklarací, jak je znázorněno na následujícím obrázku:
  
 ![Několik sad deklarací se stejnou vydanou sadou deklarací identity.](./media/managing-claims-and-authorization-with-the-identity-model/multiple-claim-sets-same-issuing-claim-set.gif)  
  
 S výjimkou sady deklarací, která je svým vlastním vystavitelem, model identity neposkytuje žádnou podporu pro sady deklarací pro vytvoření smyčky. Proto se situace, kdy sada deklarací identity vystavuje sadou deklarací B, která je vystavená pomocí sady deklarací identity A, může nikdy nastat. Model identity navíc neposkytuje žádnou podporu pro sady deklarací identity, aby měl více vystavitelů. Pokud dva nebo více vystavitelů musí vystavovat danou sadu deklarací identity, musíte použít více sad deklarací identity, z nichž každá obsahuje stejné deklarace identity, ale mají různé vystavitele.  
  
### <a name="the-origin-of-claims"></a>Původ deklarací identity  
 Deklarace identity můžou pocházet z nejrůznějších zdrojů. Jedním z běžných zdrojů deklarací je pověření prezentované uživatelem, například jako součást zprávy odeslané webové službě. Systém tyto deklarace identity ověří a stane se součástí sady deklarací přidružených k uživateli. Mezi další systémové součásti můžou být taky zdroje deklarací identity, včetně, ale ne omezeného operačního systému, síťového zásobníku, běhového prostředí nebo aplikace. Kromě toho mohou být vzdálené služby také zdrojem deklarací identity.  
  
### <a name="authorization-policies"></a>Zásady autorizace  
 V modelu identity se deklarace identity generují jako součást procesu vyhodnocení zásad autorizace. Zásada autorizace prověřuje (případně prázdnou) sadu stávajících deklarací identity a může se rozhodnout přidat další deklarace identity na základě již přítomných deklarací identity a dalších informací, které jsou k dispozici. To poskytuje základ mapování mezi deklaracemi. Přítomnost nebo neexistence deklarací identity v systému ovlivňuje chování zásad autorizace s ohledem na to, jestli přidá další deklarace identity.  
  
 Například zásada autorizace má přístup k databázi, která obsahuje položky DatumNarození různých entit pomocí systému. Zásada autorizace používá tyto informace k přidání deklarace identity "Over18" do kontextu. Všimněte si, že tato deklarace identity Over18 nezveřejňuje žádné informace o jiné entitě, než je fakt, že je víc než 18 let věku. Všimněte si, že výklad deklarace identity Over18 závisí na porozumění sémantikě dané deklarace identity. Zásady autorizace, které přidaly deklaraci identity, rozumí těmto sémantikám na určité úrovni. Kód, který následně prověřuje deklarace identity, které jsou výsledkem vyhodnocení zásad, jsou také informovány o těchto sémantikách.  
  
 Tyto zásady autorizace můžou vyžadovat, aby se vyhodnotily víckrát, protože jako další zásady autorizace přidávají deklarace identity. Tyto zásady autorizace můžou ještě přidat další deklarace identity. Model identity je navržený tak, aby pokračoval v vyhodnocení, dokud žádné další deklarace nepřidá do kontextu žádné z platných autorizačních zásad. Toto Průběžné vyhodnocování autorizačních zásad brání nutnosti vyhodnotit určité pořadí vyhodnocování v souvislosti se zásadami autorizace; můžou být vyhodnoceny v libovolném pořadí. Pokud například zásada X přidá deklaraci identity Z jenom v případě, že zásada A přidala deklaraci B, pak se při prvním vyhodnocení X nepřidá deklarace identity Z. Následně se vyhodnotí a přidá deklaraci B. X, potom se vyhodnotí podruhé a tentokrát přidá deklaraci identity Z.  
  
 Daný systém může mít v platnosti mnoho autorizačních zásad.  
  
### <a name="a-key-making-machine"></a>Počítač pro vytváření klíčů  
 Vyhodnocení skupiny přidružených zásad autorizace je například použití počítače, který vytváří klíče. Vyhodnotí se tyto zásady autorizace a vygenerují se sady deklarací, které vytvářejí tvar klíče. Až se tvar klíče dokončí, dá se použít k pokusu o otevření některých zámků. Tvar klíče je uložen v "autorizačním kontextu", který je vytvořen správcem autorizací.  
  
### <a name="authorization-context"></a>Autorizační kontext  
 Správce autorizací vyhodnotí různé zásady autorizace, jak je popsáno, a výsledkem je autorizační kontext (sada deklarací identity a některé přidružené vlastnosti). Kontext autorizace se dá prozkoumat, abyste zjistili, jaké deklarace identity jsou v daném kontextu, vztahy mezi těmito různými deklaracemi (například vydávající sada deklarací identity) a nakonec je porovnejte s některými požadavky, které musí splňovat při přístupu k prostředku.  
  
### <a name="locks"></a>Zámky  
 Pokud je kontextem autorizace (sada deklarací identity) klíč, požadavky, které musí být splněné pro udělení přístupu k určitému chráněnému prostředku, představují zámek, který musí klíč splňovat. Model identity neformalizovat způsob, jakým jsou tyto požadavky vyjádřené, ale v důsledku povahy systému založeného na deklaraci identity, zahrnuje porovnání deklarací identity v kontextu autorizace s určitou sadou požadovaných deklarací.  
  
### <a name="a-recap"></a>Rekapitulace  
 Model identity je založený na konceptu deklarací identity. Deklarace identity jsou seskupeny do sad a agregovány v autorizačním kontextu. Autorizační kontext obsahuje sadu deklarací identity a je výsledkem vyhodnocení jedné nebo více zásad autorizace přidružených k nástroji Správce autorizací. Tyto sady deklarací lze prozkoumat a zjistit, zda byly splněny požadavky na přístup. Následující obrázek znázorňuje vztahy mezi různými koncepty modelu identity.  
  
 ![Správa deklarací identity a autorizace](media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>WCF a model identity  
 WCF používá infrastrukturu modelu identity jako základ pro provádění autorizací. Ve <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> službě WCF vám třída umožňuje jako součást služby zadat zásady *autorizace* . Tyto zásady autorizace se označují jako *externí zásady autorizace*a můžou provádět zpracování deklarací identity na základě místních zásad nebo prostřednictvím interakce se vzdálenou službou. Správce autorizací reprezentovaný <xref:System.ServiceModel.ServiceAuthorizationManager> třídou vyhodnocuje externí zásady autorizace společně se zásadami autorizace, které rozpoznávají různé typy přihlašovacích údajů (tokeny), a naplní, co se nazývá *autorizační kontext* s deklaracemi, které jsou vhodné pro příchozí zprávy. Autorizační kontext je reprezentován <xref:System.IdentityModel.Policy.AuthorizationContext> třídou.  
  
## <a name="identity-model-programming"></a>Programování modelu identity  
 Následující tabulka popisuje objektový model používaný k programování rozšíření modelu identity. Tyto třídy existují v <xref:System.IdentityModel.Policy> <xref:System.IdentityModel.Claims> oborech názvů nebo.  
  
|Třída|Popis|  
|-----------|-----------------|  
|Autorizační součást|Třída modelu identity, která implementuje <xref:System.IdentityModel.Policy.IAuthorizationComponent> rozhraní.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Rozhraní, které poskytuje jednu vlastnost řetězce jen pro čtení: ID. Hodnota této vlastnosti je jedinečná pro každou instanci v systému, který implementuje toto rozhraní.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|*Autorizační komponenta* , která obsahuje sadu `ClaimSet` instancí s nulovými nebo více vlastnostmi, výsledek vyhodnocení jedné nebo více zásad autorizace.|  
|<xref:System.IdentityModel.Claims.Claim>|Kombinace typu deklarace identity, práva a hodnoty. Části pravé a hodnoty jsou omezeny typem deklarace identity.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Abstraktní základní třída. Kolekce `Claim` instancí.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Zapečetěná třída. Implementace `ClaimSet` třídy.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Abstraktní základní třída. Předává se zásadám autorizace během vyhodnocování zásad.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Rozhraní odvozené od `IAuthorizationComponent` třídy zásad autorizace a implementováno je.|  
|<xref:System.IdentityModel.Claims.Rights>|Statická třída, která obsahuje předdefinované pravé hodnoty.|  
  
 Následující třídy jsou také používány pro programování modelu identity, ale nebyly nalezeny v <xref:System.IdentityModel.Policy> <xref:System.IdentityModel.Claims> oborech názvů nebo.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Třída, která poskytuje metodu – <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> k provádění kontrol autorizace na základě deklarace identity pro každou operaci ve službě. Musíte odvozovat z třídy a přepsat metodu.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Zapečetěná třída, která poskytuje různé vlastnosti související s chováním služby, která se vztahuje k autorizaci.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Třída, která poskytuje kontext zabezpečení, včetně kontextu autorizace, pro operaci aktuálně spuštěné (nebo ke spuštění). Instance této třídy je součástí <xref:System.ServiceModel.OperationContext> .|  
  
### <a name="significant-members"></a>Významnou členy  
 Následující členové se běžně používají k vytváření nových typů deklarací.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Odvozené třídy implementují tuto metodu, aby před spuštěním operací ve službě prováděla kontroly přístupu založené na deklaracích. Jakékoli a všechny informace v dodaných <xref:System.ServiceModel.OperationContext> nebo jinde se dají prozkoumat při rozhodování o kontrole přístupu. Pokud se <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> vrátí `true` , pak se udělí přístup a operace se může spustit. Pokud se `CheckAccessCore` vrátí `false` , přístup se odepře a operace se nespustí. Příklad najdete v tématu [Postup: Vytvoření vlastního Správce autorizací pro službu](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Vrátí <xref:System.ServiceModel.ServiceAuthorizationManager> pro službu. <xref:System.ServiceModel.ServiceAuthorizationManager>Zodpovídá za provádění autorizačních rozhodnutí.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Kolekce vlastních zásad autorizace zadaných pro službu. Tyto zásady se vyhodnocují Kromě těchto zásad přidružených k přihlašovacím údajům v příchozích zprávách.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Policy.EvaluationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationComponent>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims>
- <xref:System.IdentityModel.Policy>
- <xref:System.IdentityModel.Tokens>
- <xref:System.IdentityModel.Selectors>
- [Deklarace a tokeny](claims-and-tokens.md)
- [Deklarace identity a odepření přístupu k prostředkům](claims-and-denying-access-to-resources.md)
- [Vytvoření deklarace identity a hodnoty prostředků](claim-creation-and-resource-values.md)
- [Postupy: Vytvoření vlastní deklarace identity](../extending/how-to-create-a-custom-claim.md)
- [Postupy: Porovnávání deklarací](../extending/how-to-compare-claims.md)
- [Postupy: Vytvoření vlastních zásad autorizace](../extending/how-to-create-a-custom-authorization-policy.md)
- [Postupy: Vytvoření vlastního správce autorizace pro službu](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Přehled zabezpečení](security-overview.md)
- [Autorizace](authorization-in-wcf.md)
