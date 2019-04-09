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
ms.openlocfilehash: 568fb1c2a18cfde5b15b844754f4356af0a576a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155087"
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Správa deklarací a autorizace s modelem identity
Autorizace je proces určování entit, které mají oprávnění změnit, zobrazit nebo jinak přístupu k prostředkům počítače. Například ve firmě, pouze správci mohou bude moct získat přístup k souborům svým zaměstnancům. Windows Communication Foundation (WCF) podporuje dva mechanismy pro provádění zpracování autorizace. První mechanismus umožňuje řídit autorizaci s použitím existujícího běžné konstrukce jazyka runtime (CLR). Druhý je známý jako model založené na deklaracích *modelem Identity*. WCF používá Model identit k vytvoření deklarace identity z příchozí zprávy. Třídy modelu identity je možné rozšířit na podporu nových typů deklarací identity pro vlastní autorizace schémata. Toto téma obsahuje přehled hlavní koncepty programování funkce modelu identit, jakož i seznam vašich nejdůležitějších tříd, které používá funkci.  
  
## <a name="identity-model-scenarios"></a>Scénáře modelu identit  
 Následující scénáře představují pomocí modelu identit.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Scénář 1: Podpora identit, Role a deklarace skupiny  
 Uživatelé odesílat zprávy do webové služby. Požadavky na řízení přístupu webové služby pomocí identit, role nebo skupiny. Odesílatel zprávy je namapována na sadu role nebo skupiny. Role nebo skupiny informace slouží k provádění kontroly přístupu.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Scénář 2: Podpora deklarací identity ve formátu RTF  
 Uživatelé odesílat zprávy do webové služby. Požadavky na řízení přístupu webové služby vyžadují modelu širší než identit, role nebo skupiny. Webová služba určuje, zda daný uživatel má přístup k určitému prostředku chráněné pomocí bohatých modelu založené na deklaracích. Jeden uživatel může být například moct číst konkrétní informace, například informace o mzda, který ostatní uživatelé nebudou mít přístup k.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Scénář 3: Mapování různorodých deklarací identity  
 Uživatel odešle zprávu do webové služby. Uživatel může zadat své přihlašovací údaje v několika různými způsoby: Certifikát X.509, název token uživatele nebo token protokolu Kerberos. Webová služba je nutné provést kontroly řízení přístupu stejným způsobem bez ohledu na typ přihlašovacích údajů uživatele. Pokud další pověření typy jsou podporovány v čase, by měl systém vyvíjí odpovídajícím způsobem.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Scénář 4: Určení přístup k více prostředkům  
 Webová služba se pokusí o přístup k více prostředkům. Služba Určuje určitý uživatel má přístup k porovnáním deklarací identity přidružené k uživateli se deklarace identity, která chránila prostředky vyžadované pro přístup k prostředku.  
  
## <a name="identity-model-terms"></a>Podmínky modelu identit  
 V následujícím seznamu definuje klíčové pojmy používané k popisu koncepty modelu identit.  
  
 Zásady autorizace  
 Sada pravidel pro mapování sadu vstupních deklarací identity k sadě výstupní deklarace identit. Vyhodnocení výsledků zásad autorizace v deklarace identity se přidávají do kontext vyhodnocení a následně autorizační kontext sady.  
  
 Autorizační kontext  
 Sada sad deklarací identity a nula nebo více vlastností. Výsledek vyhodnocení výrazu jedné nebo více zásad autorizace.  
  
 Deklarace  
 Kombinace typu deklarace identity, vpravo, a hodnotu.  
  
 Sada deklarací identity  
 Sadu deklarací identity vystavených konkrétní vystavitelem.  
  
 Typ deklarace identity  
 Typ deklarace identity. Vlastnosti jsou deklarace identity definované rozhraní API modelu Identity <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> třídy. Příklady typů deklarací poskytovaných systémem <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.System%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A>, a <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A>.  
  
 Kontext vyhodnocení  
 Kontext, ve kterém je vyhodnocen zásad autorizace. Obsahuje vlastnosti a deklarace identity sady. Po dokončení testování se změní na základě autorizační kontext.  
  
 Deklarace identity  
 Deklarace identity, jehož doprava je identita.  
  
 Vystavitel  
 Sada deklarací identity, který obsahuje alespoň jednu deklaraci identity a se považuje za vydali další sadu deklarací.  
  
 Vlastnosti  
 Sada informace související s kontext vyhodnocení nebo autorizační kontext.  
  
 Chráněného prostředku  
 Něco v systému, který jde použít jenom, získat přístup nebo jinak manipulovat, pokud nejprve splnění určitých požadavků.  
  
 Pravé  
 Funkce na prostředku. Definice rozhraní API modelu Identity práv jsou vlastnosti <xref:System.IdentityModel.Claims.Rights> třídy. Příklady poskytované systémem rights <xref:System.IdentityModel.Claims.Rights.Identity%2A> a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
 Value  
 Něco, nad tím, které je požadováno práva.  
  
## <a name="claims"></a>deklarace identity  
 Model identit je systém založené na deklaracích. Deklarace identity popisují možnosti přidružené nějaké entity v systému, často uživatele systému. Sadu deklarací identity přidružené k dané entitě můžete představit jako klíč. Konkrétních deklarací identit definovat tvar tohoto klíče, podobně jako na fyzických klíč použitý k otevření zámku v dveří. Deklarace identity se používají k získání přístupu k prostředkům. Přístup k dané chráněnému prostředku se určuje podle porovnávání deklarací potřebné pro přístup k tomuto prostředku díky deklaracím identity přidružené k pokusu o přístup entity.  
  
 Deklarace identity je výraz práva s ohledem na určitou hodnotu. Právo může být něco jako "Čtení", "Write" nebo "Spustit". Hodnota může být databáze, soubor, poštovní schránku nebo vlastnost. Deklarace také mít typ deklarace identity. Kombinace typu deklarace identity a pravá poskytuje mechanismus pro určení možnosti s ohledem na hodnoty. Deklarace typu "File" vpravo "čtení" hodnotou "Biography.doc", například znamená, že entity, které takové deklarace identity je přidružené má oprávnění ke čtení souboru Biography.doc. Deklarace typu "Name", s správné "PossessProperty" hodnotou "Novák" označuje, že entity, které takové deklarace identity je přidružené má vlastnost Name s hodnotou "Novák".  
  
 I když různé typy deklarací identity a práva jsou definované jako součást modelu Identity, systém je rozšiřitelný, umožňuje různé systémy vytváření nad infrastrukturou Identity Model, chcete-li definovat typy další deklarace identity a přístupových práv podle potřeby.  
  
### <a name="identity-claims"></a>Deklarace identity  
 Jedno konkrétní právo je, že identity. Deklarace identity, které se mají tato práva provést příkaz o identitě entity. Například, deklarace identity typu "hlavní název uživatele" (UPN) s hodnotou "someone@example.com" a vpravo od Identity označuje konkrétní identity v určité doméně.  
  
#### <a name="system-identity-claim"></a>Deklarace Identity systému  
 Identity Model definuje jedna deklarace identity: Systém. Deklarace identity systému označuje, že entita je aktuální aplikace nebo systému.  
  
### <a name="sets-of-claims"></a>Sadu deklarací identity  
 Model deklarací identity, které reprezentuje identitu je důležité, protože deklarace identity jsou vždy vystavované některé entity v systému, i v případě, že dané entitě v konečném důsledku je některé pojmu "vlastní". Deklarace identity jsou seskupeny jako sada a má každá sada vystavitele. Vystavitele je právě sadu deklarací identity. Nakonec musí být ukončen rekurzivní relaci a všechny deklarace identity, že sada může být vlastní vystavitele.  
  
 Následující obrázek znázorňuje příklad tři sady deklarací identity, kde jednu sadu deklarací identity má, jako její Vystavitel jinou sadu deklarací identity, která naopak má systém sadu jako její Vystavitel deklarací. Proto sady deklarací, které tvoří hierarchii, která může být libovolné hloubky.  
  
 ![Správa deklarací identity a autorizace](../../../../docs/framework/wcf/feature-details/media/claimshierarchy.gif "claimshierarchy")  
  
 Několik sad deklarací, které mohou mít stejný vydávání deklarací identity sady, jak je znázorněno na následujícím obrázku.  
  
 ![Správa deklarací identity a autorizace](../../../../docs/framework/wcf/feature-details/media/multiplesetsofclaims.gif "multiplesetsofclaims")  
  
 S výjimkou sadu deklarací identity, která je vlastní vystavitele neposkytuje modelem Identity podporuje deklarace identity sad a vytvoří smyčku. Proto nastat situace, ve kterém sada deklarací identity A vydává sady deklarací B, která sama o sobě vydala sadu deklarací identity A, můžete nikdy. Navíc Model identit neposkytuje podporuje sady deklarací, aby více vystavitelů. Pokud dva nebo více vystavitelů musíte vydat danou sadu deklarací identity, pak je nutné použít více sad deklarací identity, každá obsahující deklarace pro stejný, ale s jinou vystavitelů.  
  
### <a name="the-origin-of-claims"></a>Zdroje deklarací identity  
 Deklarace identity můžou pocházet z různých zdrojů. Běžné příčiny deklarace identity se přihlašovací údaje předkládaných uživatelem, například jako součást zpráva odeslaná do webové služby. Systém ověří tyto deklarace identity a stanou součástí sadu deklarací identity přidružené k uživateli. Zdroje deklarací identity, včetně operačního systému, zásobníku sítě, běhové prostředí nebo aplikace může být také dalších komponent systému. Vzdálené kromě toho může být zdrojem deklarací identity.  
  
### <a name="authorization-policies"></a>Zásady autorizace  
 V modelu Identity jako součást procesu hodnocení zásady autorizace pro generování deklarací identity. Zásad autorizace zkontroluje sada (pravděpodobně prázdná) existující deklarace identity a můžete přidat další deklarace identity založené na deklaracích identity, které jsou už k dispozici a další informace k dispozici. To poskytuje základ pro mapování mezi deklarací identity. Přítomnosti nebo nepřítomnosti deklarací identity v systému ovlivní chování zásad autorizace s ohledem na tom, jestli ho přidá další deklarace identity.  
  
 Například zásady autorizace pro má přístup k databázi, která zahrnuje birthdates různých entit pomocí systému. Zásady autorizace používá tyto informace přidat deklaraci identity "Over18" v kontextu. Všimněte si, že tato deklarace identity Over18 neposkytují žádné informace o entitě, než je skutečnost, že je za 18 let. Všimněte si, že výklad deklarace identity "Over18" závisí na principy sémantiku tuto žádost. Zásady autorizace, který přidá deklaraci identity rozumí těchto sémantiku na určité úrovni. Kód, který se následně prozkoumá deklarace identity, které jsou výsledkem vyhodnocení zásad se také informace o těchto sémantiku.  
  
 Zásady autorizace pro dané může vyžadovat více než jednou ji možné vyhodnotit, protože jako ostatní zásady autorizace přidání deklarace identity, tuto zásadu autorizace může přidat ještě více deklarací identity. Model identit slouží k vyhodnocení pokračovat, dokud nebudou přidány žádné další deklarace identity ke kontextu podle těchto zásad autorizace v platnost. Tuto trvalou hodnocení zásad autorizace zabrání požadavku k vynucení pořadí žádné konkrétní vyhodnocení s ohledem na zásady autorizace; mohou být vyhodnoceny v libovolném pořadí. Například pokud zásada X deklarace identity Z přidá pouze, pokud zásady A přidal B deklarace identity, pak pokud X je vyhodnocen jako první, je zpočátku nepřidá Z deklarací identity. A následně je vyhodnocen a přidá X B. deklarace identity se pak vyhodnocuje podruhé a tentokrát ho přidá Z deklarací identity.  
  
 Daný systém může mít mnoho zásad autorizace v platnost.  
  
### <a name="a-key-making-machine"></a>Vytváření klíč počítače  
 Vyhodnocení skupiny zásad přidružených autorizace je například počítač, který vytvoří klíče. Zásady autorizace se každý vyhodnocen a sady deklarací, které jsou generovány, vytvářejí tvar klíče. Po dokončení tvar klíč lze použít k pokusu o otevření některé zámky. Tvar klíče jsou uloženy v "kontextu autorizace,", který je vytvořil Správce autorizací.  
  
### <a name="authorization-context"></a>Autorizační kontext  
 Správce autorizací vyhodnotí různé zásady autorizace, jak je popsáno a výsledkem je objekt context autorizace (sadu sady deklarací a některé vlastnosti). Autorizační kontext se dají prozkoumat a určit, jaké deklarace identity jsou k dispozici v tomto kontextu, vztahy mezi těmito různých deklarací (například vydávající sadě deklarací), takže v konečném důsledku je porovnán některé požadavky musí splňovat pro přístup prostředek.  
  
### <a name="locks"></a>Zámky  
 Pokud objekt context autorizace (sadu deklarací identity) je klíč, požadavky, které pokud chcete udělit přístup pro konkrétní chráněný prostředek, musí být splněny tvoří zámek, který klíč se musí vejít. Model identit není formalizujte, jak jsou vyjádřeny tyto požadavky, ale, vzhledem k povaze systému, na základě deklarace identity zahrnují porovnávání deklarací identity v kontextu autorizace některé sady požadované deklarace identit.  
  
### <a name="a-recap"></a>Rekapitulace  
 Identity Model je založený kolem koncepce deklarací identity. Deklarace identity jsou seskupeny do sad a agregovat v kontextu autorizace. Autorizační kontext obsahuje sadu deklarací identity a je výsledek vyhodnocení výrazu nejméně jedny zásady autorizace přidružené Správce autorizací. Tyto deklarací sady můžete prověřit, abyste zjistili, pokud byly splněny požadavky na přístup. Následující obrázek znázorňuje vztahy mezi tyto různé koncepty modelu identit.  
  
 ![Správa deklarací identity a autorizace](../../../../docs/framework/wcf/feature-details/media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>WCF a modelem Identity  
 WCF používá infrastrukturu identit modelu jako základ pro autorizaci. Ve službě WCF <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> třída umožňuje určit *autorizace* zásady jako součást služby. Tyto zásady autorizace se označují jako *externí autorizační zásady*, a mohou provádět zpracování deklarace identity založené na místní zásady nebo interakci se vzdálenou službou. Správce autorizací, reprezentovaný <xref:System.ServiceModel.ServiceAuthorizationManager> třídy vyhodnotí zásady autorizace externí spolu s zásady autorizace, které rozpoznají různých přihlašovacích údajů typy (tokeny) a naplní, co je volána  *autorizační kontext* díky deklaracím identity pro příchozí zprávy. Autorizační kontext je reprezentována <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.  
  
## <a name="identity-model-programming"></a>Model programování identity  
 Následující tabulka popisuje objektový model pro rozšíření modelu identit. Všechny tyto třídy existovat v jednom <xref:System.IdentityModel.Policy> nebo <xref:System.IdentityModel.Claims> obory názvů.  
  
|Třída|Popis|  
|-----------|-----------------|  
|Komponenta autorizace|Třídu s modelem Identity, který implementuje <xref:System.IdentityModel.Policy.IAuthorizationComponent> rozhraní.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Rozhraní, která poskytuje jeden řetězec jen pro čtení vlastnosti: Id. Hodnota této vlastnosti je jedinečný pro každou instanci v systému, který implementuje toto rozhraní.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|*Autorizace součástí* , který obsahuje sadu `ClaimSet` instancí se nula nebo více vlastností, výsledek vyhodnocení výrazu jedné nebo více zásad autorizace.|  
|<xref:System.IdentityModel.Claims.Claim>|Kombinace typ deklarace identity, vpravo a hodnotu. Typ deklarace identity jsou omezeny částí doprava a hodnotu.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Abstraktní základní třídu. Kolekce `Claim` instancí.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Zapečetěná třída. Implementace `ClaimSet` třídy.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Abstraktní základní třídu. Předaný zásad autorizace během vyhodnocení zásad.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Rozhraní je odvozena z `IAuthorizationComponent` a implementované třídami zásad autorizace.|  
|<xref:System.IdentityModel.Claims.Rights>|Statická třída, která obsahuje předdefinované správné hodnoty.|  
  
 Následující třídy jsou také používány pro programovací Model identit, ale nejsou součástí <xref:System.IdentityModel.Policy> nebo <xref:System.IdentityModel.Claims> obory názvů.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Třída, která poskytuje metodu – <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>– provádět ověřování na základě deklarace identity ověří jednotlivých operací ve službě. Musíte odvodit z třídy a přepsat metodu.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Zapečetěná třída, která poskytuje různé vlastnosti související s chování služby, protože se týkají autorizace.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Třída, která poskytuje kontext zabezpečení, včetně autorizační kontext, pro aktuálně spuštěné (nebo být spuštěn) operace. Instance této třídy je součástí <xref:System.ServiceModel.OperationContext>.|  
  
### <a name="significant-members"></a>Důležité členy  
 Následující členy se běžně používají k vytvoření nových typů deklarací identity.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Odvozené třídy Implementujte tuto metodu za účelem provádění kontrol přístupu na základě deklarace identity před spuštěním operace ve službě. Všechny informace do zadané <xref:System.ServiceModel.OperationContext>, nebo jinde, se dají prozkoumat při provádění přístup, zkontrolujte rozhodnutí. Pokud <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> vrátí `true`, se udělí přístup k a operace se může spustit. Pokud `CheckAccessCore` vrátí `false`, přístup se odepře a operace se nespustí. Příklad najdete v tématu [jak: Vytvoření vlastního Správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Vrátí <xref:System.ServiceModel.ServiceAuthorizationManager> pro službu. <xref:System.ServiceModel.ServiceAuthorizationManager> Zodpovídá za při autorizačním rozhodování.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Kolekce zadaná pro službu Zásady autorizace. Tyto zásady jsou vyhodnocovány kromě tyto zásady přidružené k přihlašovacím údajům příchozí zprávy.|  
  
## <a name="see-also"></a>Viz také:

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
- [Deklarace a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Deklarace a odepření přístupu k prostředkům](../../../../docs/framework/wcf/feature-details/claims-and-denying-access-to-resources.md)
- [Vytvoření nároku a hodnoty prostředků](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Postupy: Vytvoření vlastní deklarace](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
- [Postupy: Porovnání deklarací](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [Postupy: Vytvoření vlastní zásady autorizace](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-policy.md)
- [Postupy: Vytvoření vlastního správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
