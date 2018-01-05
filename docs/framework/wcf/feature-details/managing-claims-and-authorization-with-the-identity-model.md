---
title: "Správa deklarací a autorizace s modelem identity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- WCF security
- claims [WCF], managing with the Identity Model
- claims [WCF]
- authorization [WCF], managing with the Identity Model
ms.assetid: 099defbb-5d35-434e-9336-1a49b9ec7663
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db0a304a908e906b635672eed1a84f0277284ad7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Správa deklarací a autorizace s modelem identity
Autorizace je proces zjišťování entit, které mají oprávnění změnit, zobrazení nebo jinak přístup k prostředkům počítače. Například v obchodu, pouze správci mohou mít přístup k soubory své zaměstnance. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]podporuje dva mechanismy pro provádění zpracování autorizace. První mechanismus vám umožňuje řídit autorizaci s použitím stávající společné jazykové konstrukty runtime (CLR). Druhá je model na základě deklarace označuje jako *modelu Identity*. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]pomocí modelu Identity vytvoří deklarace identity ze příchozí zprávy; Třídy modelu identity lze rozšířit pro podporu nových typů deklarací identity pro schémata autorizace. Toto téma obsahuje přehled hlavní koncepty programování modelu Identity funkce, jakož i seznam nejdůležitější tříd, které používá funkci.  
  
## <a name="identity-model-scenarios"></a>Scénáře modelu identity  
 Následující scénáře představují použití modelu Identity.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Scénář 1: Podpora identitu, Role a deklarace skupiny  
 Uživatelé posílat zprávy k webové službě. Požadavky řízení přístupu webové služby pomocí identity, role nebo skupiny. Odesílatel zprávy je namapována na sadu role nebo skupiny. Role nebo skupiny informace slouží k provádění kontrol přístupu.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Scénář 2: Podpora deklarací identity formátováním  
 Uživatelé posílat zprávy k webové službě. Požadavky řízení přístupu webové služby vyžadují model širší než identit, role nebo skupiny. Webová služba určuje, zda daný uživatel má přístup k určitému prostředku chráněné pomocí bohaté modelu na základě deklarace. Jeden uživatel může být například moct číst konkrétní informace, jako jsou informace o mzda, které jiní uživatelé nemají přístup k.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Scénář 3: Mapování různorodých deklarace identity  
 Uživatel odešle zprávu do webové služby. Uživatel může zadat své přihlašovací údaje do několika různými způsoby: certifikát X.509, název token uživatele nebo token protokolu Kerberos. Webová služba je nutné provést kontroly řízení přístupu stejným způsobem, bez ohledu na typ přihlašovacích údajů uživatele. Pokud další pověření typy jsou podporovány v čase, by se měl systém vyvíjet odpovídajícím způsobem.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Scénář 4: Určení přístup k více prostředkům  
 Webová služba se pokusí získat přístup k více prostředkům. Služba Určuje, které chráněným prostředkům daného uživatele tak, že porovnáte deklarace identity přidružené k uživateli s deklaracemi identity má přístup k požadované pro přístup k prostředku.  
  
## <a name="identity-model-terms"></a>Podmínky modelu identity  
 V následujícím seznamu definuje klíčových termínů používaných k popisu koncepty modelu Identity.  
  
 Zásady autorizace  
 Sada pravidel pro mapování sadu deklarací identity vstupní sadu deklarací identity výstup. Vyhodnocování výsledků zásad autorizace v deklarace identity se přidává do kontextu vyhodnocení a následně autorizační kontext sady.  
  
 Autorizační kontext  
 Sada sad deklarací identity a nula nebo více vlastností. Výsledek vyhodnocení jedné nebo více zásad autorizace.  
  
 Deklarace  
 Kombinace typ deklarace identity, práva a hodnotu.  
  
 Sady deklarací.  
 Sadu deklarací identity vystavený konkrétní vystavitele.  
  
 Typ deklarace identity  
 Typ deklarace identity. Vlastnosti jsou deklarace identity definované rozhraní API modelu Identity <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> třídy. Příklady typů deklarací identity poskytované systémem <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.System%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A>, a <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A>.  
  
 kontext vyhodnocení  
 Kontext, ve kterém je vyhodnocena zásad autorizace. Obsahuje sady vlastností a deklarace identity. Po dokončení testování se změní na základě kontextu autorizace.  
  
 Deklarace identity  
 Deklarace identity, jehož práva je identita.  
  
 Vystavitel  
 Sada deklarací identity, která obsahuje alespoň jedna deklarace identity a považuje se vystavily jiné sady deklarací.  
  
 Vlastnosti  
 Sada informace spojené s kontext vyhodnocení nebo autorizační kontext.  
  
 Chráněného prostředku  
 V systému, který lze použít pouze, něco přístupné, nebo jinak s nimi manipulovat, pokud nejprve splnění určitých požadavků.  
  
 Vpravo  
 Funkce na prostředku. Práva definované rozhraní API modelu Identity jsou vlastnosti <xref:System.IdentityModel.Claims.Rights> třídy. Příklady poskytované systémem rights <xref:System.IdentityModel.Claims.Rights.Identity%2A> a <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
 Hodnota  
 Něco, za které je požadováno doprava.  
  
## <a name="claims"></a>Deklarace identity  
 Modelem Identity je systém založené na deklaracích identity. Deklarace identity popisují možnosti související s některé entity v systému, často uživatel tohoto systému. Obsahuje sadu deklarací spojené s danou entitu můžete představit jako klíč. Konkrétních deklarací identit definovat obrazec tomuto klíči, podobně jako fyzický klíč použitý k otevření zámek v dveří. Deklarace identity se používají k získání přístupu k prostředkům. Přístup k danému chráněného prostředku je určen podle porovnávání deklarací identity potřebné pro přístup k prostředku s deklaracemi identity přidružené k přístup při pokusu entity.  
  
 Deklarace identity je výraz práva s ohledem na konkrétní hodnotu. Právo může být něco jako "Číst", "Zápisu" nebo "Spustit". Hodnota může být databáze, soubor, poštovní schránku nebo vlastnost. Deklarace identity také mít typ deklarace identity. Kombinace typ deklarace identity a pravé poskytuje mechanismus pro zadání možnosti s ohledem na hodnotu. Deklarace typu "Soubor" vpravo "čtení" přes hodnotu "Biography.doc", například označuje, že entita, ke které taková deklarace identity je přidružena má přístup pro čtení do souboru Biography.doc. Deklarace identity typu "Název", s vpravo "PossessProperty" nad hodnotou "Martin" označuje, zda má entit, ke které taková deklarace identity přidružena vlastnost Name s hodnotou "Martin".  
  
 I když se různé typy deklarací identity a práva jsou definované jako součást modelu Identity, systém je rozšiřitelný, což různých systémů, vytváření modelu Identity infrastruktuře, můžete definovat další typy a práv podle potřeby.  
  
### <a name="identity-claims"></a>Deklarace identity  
 Jedno konkrétní právo je identity. Deklarace identity, které měl tato práva proveďte příkaz o identitě entity. Například deklarace identity typu "hlavní název uživatele" (UPN) s hodnotou "someone@example.com" a napravo od Identity označuje konkrétní identity v konkrétní doméně.  
  
#### <a name="system-identity-claim"></a>Deklarace Identity systému  
 Modelem Identity definuje jednu deklaraci identity: systému. Deklarace identity systému označuje, že je entita aktuální aplikace nebo systému.  
  
### <a name="sets-of-claims"></a>Sady deklarací identity  
 Model deklarace identity, které reprezentuje identitu je důležité, protože deklarace identity jsou vždy vydané některé entity v systému, i když je dané entity nakonec některé konceptu "vlastní". Deklarace identity jsou seskupeny dohromady jako sada a má každá sada vystavitele. Vystavitele je právě sadu deklarací identity. Nakonec musí končit rekurzivní relaci a všechny deklarace identity, že nastavení může být vlastní vystavitele.  
  
 Následující obrázek znázorňuje příklad tři sady deklarací, kde má jedna sada deklarací identity, jako jeho vydavatel jinou sadu deklarací identity, která naopak má systém sady jako vystavitele deklarací identity. Proto sady deklarací identity tvoří hierarchii, která může být nahodile hloubkové.  
  
 ![Správa deklarací a autorizace](../../../../docs/framework/wcf/feature-details/media/claimshierarchy.gif "claimshierarchy")  
  
 Několik sad deklarací identity může mít stejné vydávající deklarace sady, jak je znázorněno na následujícím obrázku.  
  
 ![Správa deklarací a autorizace](../../../../docs/framework/wcf/feature-details/media/multiplesetsofclaims.gif "multiplesetsofclaims")  
  
 S výjimkou sady deklarací, který je jeho vlastní vystavitele modelem Identity neposkytuje žádné podporu pro sady deklarací identity a vytvořit smyčku. Proto mohou nikdy nastat situace, kdy vydání sady deklarací identity A sadou deklarací identity B, který je sám vystavený sady deklarací identity A. Navíc modelem Identity neposkytuje žádné podporu pro sady deklarací identity tak, aby měl více vystavitelů. Pokud dva nebo více vystavitelů musí vystavit danou sadu deklarací identity, pak musíte použít několik sad deklarací identity, každý obsahující stejné deklarace identity, ale s jinou vystavitelů.  
  
### <a name="the-origin-of-claims"></a>Původ deklarace identity  
 Deklarace identity mohou pocházet z různých zdrojů. Jeden společný zdroj deklarací identity je přihlašovací údaje předkládaných uživatelem, například jako součást zprávy odeslané do webové služby. Systém ověří taková deklarace identity a se stávají součástí sadu deklarací identity přidružené k uživateli. Zdroje deklarací identity, včetně operačního systému, síťových protokolů, běhové prostředí nebo aplikace mohou být také dalších komponent systému. Vzdálené kromě toho může být zdrojem deklarací identity.  
  
### <a name="authorization-policies"></a>Zásady autorizace  
 V modelu Identity deklarace identity jsou generovány jako součást procesu hodnocení zásad autorizace. Zásad autorizace prozkoumá (pravděpodobně prázdná) sadu existující deklarací identity a rozhodnout, přidejte další deklarace identity založené na deklaracích identity, které jsou již existuje a další informace k dispozici. To poskytuje základ pro mapování mezi deklarací identity. Existenci nebo neexistenci těchto deklarací identity v systému vliv chování zásad autorizace s ohledem na tom, jestli ho přidá další deklarace identity.  
  
 Například má zásady autorizace pro přístup k databázi, která zahrnuje birthdates různých entit pomocí systému. Zásady autorizace používá tyto informace k přidání deklaraci identity "Over18" do kontextu. Všimněte si, že tuto deklaraci Over18 nesmí vyzradit žádné informace o entita, než na skutečnost, že je více než 18 let. Všimněte si, že výklad deklarace identity, Over18, závisí na pochopení Sémantika této deklarace identity. Zásady autorizace, který přidán deklarace rozumí těchto sémantiku na určité úrovni. Kód, který je následně prozkoumá deklarace identity, které jsou výsledkem vyhodnocení zásad také být informováni o těchto sémantiku.  
  
 Zásady daného autorizace může vyžadovat vícekrát ho možné vyhodnotit, protože, jako ostatní zásady autorizace přidání deklarací identity, zásad autorizace může přidat ještě více deklarací identity. Modelu identity je určena pro pokračovat vyhodnocení, dokud žádné další deklarace identity se nepřidají do kontextu podle těchto zásad autorizace v platnost. Toto trvalé hodnocení zásady autorizace zabrání požadavku k vynucení pořadí žádné konkrétní vyhodnocení s ohledem na zásady autorizace; může být vyhodnocen v libovolném pořadí. Například pokud zásady X deklarace identity Z přidá pouze, pokud zásady A přidala B deklarace identity, pak pokud nejprve vyhodnotí X ho původně nepřidá Z deklarací identity. A následně je vyhodnocena a přidá X B. deklarace identity je následně vyhodnocovaná ještě jednou a tentokrát přidá Z deklarací identity.  
  
 Daný systém může mít mnoho zásady autorizace v platnost.  
  
### <a name="a-key-making-machine"></a>Provádění klíč počítače  
 Vyhodnocení skupinu zásady přidružené autorizace je jako počítač, který umožňuje klíče. Zásady autorizace se každý vyhodnotit a jsou generovány sady deklarací identity, vytváření tvaru klíče. Po dokončení tvaru klíče může sloužit k pokusu o otevření některé zámky. Tvar klíče jsou uloženy v "autorizace kontextu," vytvořený serverem Správce autorizací.  
  
### <a name="authorization-context"></a>Autorizační kontext  
 Správce autorizací vyhodnotí různé zásady autorizace, jak je popsáno a výsledkem je kontextu autorizace (sada sady deklarací a některé vlastnosti). Autorizační kontext můžete prověřit, abyste zjistili, jaké deklarace identity se nacházejí v tomto kontextu vztahy mezi tyto různé deklarace identity (například vydávající sady deklarací) a nakonec je porovnán některé požadavky, musí splňovat pro přístup prostředek.  
  
### <a name="locks"></a>Zámky.  
 Pokud autorizační kontext (sadu deklarací identity) je klíč, požadavky, které je nutné splnit k udělení přístupu k určitému chráněného prostředku tvoří uzamčení, které se musí vejít klíč. Modelu identity není formalizovat, jak tyto požadavky jsou vyjádřeny ale, vzhledem k povaze systému, na základě deklarací identity představují-porovnávání deklarací identity ve autorizační kontext proti některé sady deklarací identity, vyžaduje.  
  
### <a name="a-recap"></a>Rekapitulace  
 Identity Model je založen kolem koncept deklarací identity. Deklarace identity jsou seskupené do sad a agregovat do autorizační kontext. Autorizační kontext obsahuje sadu deklarací identity a je výsledkem vyhodnocení jeden nebo více zásad autorizace, které jsou přidružené Správce autorizací. Tyto deklarace identity, že nastaví můžete prověřit, abyste zjistili, pokud byly splněny požadavky na přístup. Následující obrázek znázorňuje vztahy mezi tyto různé koncepty modelu Identity.  
  
 ![Správa deklarací a autorizace](../../../../docs/framework/wcf/feature-details/media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>WCF a modelu Identity  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá infrastrukturu modelu Identity jako základ pro provádění autorizace. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> třída umožňuje určit *autorizace* zásady jako součást služby. Tyto zásady autorizace se označují jako *zásady autorizace externí*, a mohou provádět zpracování deklarace identity založené na místní zásady nebo interakci s vzdálené služby. Správce autorizací, reprezentována <xref:System.ServiceModel.ServiceAuthorizationManager> třída vyhodnotí zásady autorizace externí společně s zásady autorizace, které rozpoznají různých přihlašovacích údajů typy (tokeny) a naplní, co se nazývá  *autorizační kontext* s deklaracemi identity vhodné pro příchozí zprávy. Autorizační kontext je reprezentována <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.  
  
## <a name="identity-model-programming"></a>Identity modelu programování  
 Následující tabulka popisuje model objektu použít k rozšíření modelu Identity programu. Všechny tyto třídy existovat buď <xref:System.IdentityModel.Policy> nebo <xref:System.IdentityModel.Claims> obory názvů.  
  
|Třída|Popis|  
|-----------|-----------------|  
|Součást autorizace|Třídu modelu Identity, který implementuje <xref:System.IdentityModel.Policy.IAuthorizationComponent> rozhraní.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Rozhraní, které poskytuje vlastnosti jeden řetězec jen pro čtení: ID. Hodnota této vlastnosti je jedinečný pro každou instanci v systému, které toto rozhraní implementuje.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|*Autorizace součást* obsahující sadu `ClaimSet` instance nula nebo více vlastností; výsledek vyhodnocení jedné nebo více zásad autorizace.|  
|<xref:System.IdentityModel.Claims.Claim>|Kombinace typ deklarace identity, práva a hodnotu. Typ deklarace identity jsou omezené části práva a hodnotu.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Abstraktní základní třídu. Kolekce `Claim` instance.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Zapečetěné třídy. Implementace `ClaimSet` třídy.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Abstraktní základní třídu. Byl předán zásad autorizace během hodnocení zásad.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Rozhraní odvozené z `IAuthorizationComponent` a implementované třídy zásad autorizace.|  
|<xref:System.IdentityModel.Claims.Rights>|Statická třída, která obsahuje předdefinované správné hodnoty.|  
  
 Následující třídy se používají i pro programování modelu Identity, ale nejsou k dispozici v <xref:System.IdentityModel.Policy> nebo <xref:System.IdentityModel.Claims> obory názvů.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Třídu, která poskytuje metodu – <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>– k provedení ověření na základě deklarace identity ověří jednotlivých operací ve službě. Musí být odvozen od třídy a přepsat metodu.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Zapečetěné třídu, která poskytuje různé vlastnosti související s chování služby, jak se vztahuje k autorizaci.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Třídu, která poskytuje kontext zabezpečení, včetně autorizační kontext, pro aktuálně spuštěné (nebo bude spuštěný) operaci. Instance této třídy je součástí <xref:System.ServiceModel.OperationContext>.|  
  
### <a name="significant-members"></a>Významné členy  
 Následující členy se běžně používají k vytvoření nové typy deklarací identity.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Odvozené třídy implementovat tuto metodu za účelem provádění kontrol přístupu na základě deklarace identity před spuštěním operace ve službě. Veškeré informace v zadaných <xref:System.ServiceModel.OperationContext>, nebo jinde, může být prověřen při provádění přístup, zkontrolujte rozhodnutí. Pokud <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> vrátí `true`, udělí přístup, a operaci se může spustit. Pokud `CheckAccessCore` vrátí `false`, byl odepřen přístup a nejde spustit operaci. Příklad, naleznete v části [postupy: vytvoření vlastního Správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Vrátí <xref:System.ServiceModel.ServiceAuthorizationManager> pro službu. <xref:System.ServiceModel.ServiceAuthorizationManager> Zodpovídá za při autorizačním rozhodování.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Kolekce, které vlastní autorizační zásady pro služby je zadaný. Kromě toho tyto zásady přidružené přihlašovací údaje v příchozí zprávy vyhodnocují se tyto zásady.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Policy.EvaluationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationComponent>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims>  
 <xref:System.IdentityModel.Policy>  
 <xref:System.IdentityModel.Tokens>  
 <xref:System.IdentityModel.Selectors>  
 [Deklarace identity a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [Deklarace identity a odepření přístupu k prostředkům](../../../../docs/framework/wcf/feature-details/claims-and-denying-access-to-resources.md)  
 [Vytvoření deklarace identity a hodnoty prostředků](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [Postupy: Vytvoření vlastní deklarace identity](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)  
 [Postupy: Porovnávání deklarací identity](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [Postupy: Vytvoření vlastních zásad autorizace](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-policy.md)  
 [Postupy: Vytvoření vlastního správce autorizace pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
