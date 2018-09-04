---
title: Správa relací WIF
ms.date: 03/30/2017
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 04c2f4bdfe2a6309fde0821db308ee2a83887323
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520549"
---
# <a name="wif-session-management"></a>Správa relací WIF
Když se klient poprvé pokusí pro přístup k chráněnému prostředku, který je hostitelem předávající stranu, klient musí je nejdřív ověřit samotné služby tokenů zabezpečení (STS), která je důvěryhodná pro předávající stranu. Služba tokenů zabezpečení pak vydá token zabezpečení do klienta. Klient představuje tento token pro předávající stranu, která udělí přístup klienta k chráněnému prostředku. Ale nechcete, aby klient bude muset znovu ověřovat, aby služba tokenů zabezpečení pro každý požadavek, zejména, protože ještě nemusí být ve stejném počítači nebo ve stejné doméně jako předávající straně. Místo toho technologie Windows Identity Foundation (WIF) má klient a předávající strana vytvořit relaci, ve které klient použije ke svému ověření ke předávající stranu pro všechny žádosti od prvního požadavku na token relace zabezpečení. Předávající straně můžete pomocí tohoto tokenu zabezpečení relace, která je uložena v souboru cookie, k rekonstrukci klienta <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>.  
  
 Služba tokenů zabezpečení definuje ověření klient musí poskytnout. Klient však pravděpodobně více přihlašovací údaje, se kterými se může ověřit sám na službu STS. Například může mít tokenu z Windows Live, uživatelské jméno a heslo, certifikátu a smartkey. V takovém případě služba tokenů zabezpečení uděluje klient několik identit, se každá identita odpovídá jedné z přihlašovacích údajů, které klient poskytne. Předávající straně můžete použít jeden nebo více těchto identit, pokud dospěje k závěru jaké úroveň přístupu k udělit této klientské.  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=nameWithType> Se používá k rekonstrukci klienta <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, která obsahuje všechny identity klienta v <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>. Každý <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> v kolekci obsahuje bootstrap tokeny, které jsou spojené s touto identitou.  
  
 Pokud vydává token novou relaci s ID relace, původní token relace <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=nameWithType> neaktualizuje tokenu relace v mezipaměť tokenu. By měl vždycky vytvoří instanci tokenu relace s ID relace jedinečný.  
  
> [!NOTE]
>  Vyvolá Session.SecurityTokenHandler.ReadToken <xref:System.Xml.XmlException> výjimku, pokud obdrží neplatný vstup; například, pokud je poškozený soubor cookie, který obsahuje token relace. Doporučujeme, abyste tuto výjimku zachytit a poskytuje chování specifické pro aplikaci.  
  
 Pokud se chráněný webová stránka obsahuje velké množství prostředků (například malé graphics), které jsou také v chráněnou doménu, klient musí znovu svému ověření ke předávající stranu pro stahování, každý z těchto prostředků. Použití ověřování tokenu relace Polly nemusíte ověřovat služby STS pro každý požadavek, ale stále znamená, že mnoho soubory cookie jsou odesílány prostřednictvím. Můžete chtít nastavit webovou stránku tak, aby důležitá data a prostředky jsou uloženy v chráněnou doménu dílčí položky jsou uložené v doméně nechráněný a odkazované z hlavní webové stránky. Nastavuje cestu k souboru cookie tak, aby odkazovaly jen chráněnou doménu.  
  
 Provozovat v režimu odkaz poskytuje obslužné rutiny pro společnost Microsoft doporučuje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> událost v **global.asax.cs** souborů a nastavení **IsReferenceMode** vlastnost na token předaný <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> vlastnost. Tyto aktualizace zajistí, že tokenu relace funguje v režimu odkaz pro každý požadavek a podporuje přes pouze nastavení <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> vlastnost na modul relace ověřování.  
  
## <a name="extensibility"></a>Rozšiřitelnost  
 Můžete rozšířit mechanismus řízení relace. Jedním z důvodů může být zvýšení výkonu. Můžete například vytvořit vlastní soubor cookie obslužnou rutinu, která transformuje nebo optimalizuje tokenu zabezpečení relace mezi jeho stav v paměti a co je potřeba k souboru cookie. Uděláte to tak, můžete nakonfigurovat <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=nameWithType> vlastnost <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=nameWithType> použít vlastní soubor cookie obslužnou rutinu, která je odvozena z <xref:System.IdentityModel.Services.CookieHandler?displayProperty=nameWithType>. <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=nameWithType> je výchozí popisovač souboru cookie, protože soubory cookie překročí povolenou velikost pro protokol HTTP (Hypertext Transfer); Pokud používáte vlastní soubor cookie obslužnou rutinu místo, musíte implementovat dělením dat do bloků.  
  
 Další informace najdete v tématu [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) vzorku. Tento příklad ukazuje mezipaměť připravená relace farmy (na rozdíl od tokenreplycache) tak, aby relace můžete použít odkaz na místo výměna velké soubory cookie. Tato ukázka předvádí, nejsnazším způsobu zabezpečení souborů cookie ve farmě. Mezipaměť relace je založená na WCF. Jde o relaci zabezpečení ukázce nová funkce technologie WIF 4.5 transformace souborů cookie podle MachineKey, což lze aktivovat jednoduchým vložením fragment kódu odpovídající v souboru web.config. Ukázka samotný není "pronájem", ale ukazuje, co potřebujete k provádění vaší aplikace připravené pro farmu.
