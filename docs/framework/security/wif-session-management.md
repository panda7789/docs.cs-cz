---
title: WIF relace správy
ms.date: 03/30/2017
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f97406ccf826bfa5b7c3ed87bdb58478b272a216
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399108"
---
# <a name="wif-session-management"></a>WIF relace správy
Když klient se poprvé pokusí o přístup k chráněnému prostředku, který je hostován předávající strana, klient musí je nejdřív ověřit samotné služby tokenů zabezpečení (STS), která je důvěryhodná předávající stranou. Služba tokenů zabezpečení pak vydá token zabezpečení do klienta. Klient uvede tento token pro předávající stranu, která pak uděluje klientský přístup k chráněnému prostředku. Ale nechcete, aby klient tak, aby měl znovu provést ověření na službu STS pro každý požadavek zvlášť, protože i nemusí být ve stejném počítači nebo ve stejné doméně jako předávající strany. Místo toho Windows Identity Foundation (WIF) má klienta a vytvořit relaci, ve které klient použije token zabezpečení relace k vlastnímu ověření předávající stranu pro všechny požadavky po prvním požadavku předávající strany. Předávající strana můžete použít tento token zabezpečení relace, který je uložený v souboru cookie, k rekonstrukci klienta <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>.  
  
 Služba tokenů zabezpečení definuje ověření klient musí poskytnout. Klient však může mít několik přihlašovací údaje, s nimiž se může ověřit sám na službu STS. Například může mít tokenu z Windows Live, uživatelské jméno a heslo, certifikát a smartkey. V takovém případě služba tokenů zabezpečení uděluje klienta několik identit s každou identitu odpovídající přihlašovací údaje, které představuje klienta. Předávající strana můžete použít jeden nebo více těchto identit, když rozhoduje, jakou úroveň přístupu k udělení klienta.  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=nameWithType> Se používá k rekonstrukci klienta <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, který obsahuje všechny identity klienta v <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>. Každý <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> v kolekci obsahuje bootstrap tokeny, které jsou spojeny s danou identitu.  
  
 Pokud se objeví token novou relaci s ID relace původní token relace <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=nameWithType> neaktualizuje token relace v mezipaměti v tokenu. Měli vždycky vytvořit instanci token relace s ID jedinečný relace.  
  
> [!NOTE]
>  Vyvolá Session.SecurityTokenHandler.ReadToken <xref:System.Xml.XmlException> výjimka, pokud obdrží neplatný vstup; například, pokud je poškozený soubor cookie, který obsahuje token relace. Doporučujeme, abyste tuto výjimku zachytit a zadejte specifické pro aplikaci chování.  
  
 Pokud chráněný webová stránka obsahuje velké množství prostředků (například malé grafické), které jsou i v chráněnou doménu, klient musí znovu ověří předávající strany ke stažení, každý z těchto prostředků. Použití ověřovací token relace nevyžaduje nutnost ověření služby tokenů zabezpečení pro každý požadavek, ale stále znamená, že mnoho soubory cookie jsou odesílány přes. Můžete chtít nastavit webové stránky tak, že důležitá data a prostředky jsou uloženy v chráněnou doménu při menší položky jsou uložené v doméně nechráněné a odkazované z hlavní webové stránky. Také nastavte cestu k souboru cookie, chcete-li pouze chráněnou doménu.  
  
 K provozu v režimu odkaz, Microsoft doporučuje poskytuje obslužnou rutinu pro <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> událost v **global.asax.cs** souborů a nastavení **IsReferenceMode** předaná vlastnost na tokenu <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> vlastnost. Tyto aktualizace zajišťují, že token relace pracuje v režimu odkaz pro každý požadavek a je podporuje přes nastavení jenom <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> vlastnost modul relace ověřování.  
  
## <a name="extensibility"></a>Rozšiřitelnost  
 Můžete rozšířit mechanismus správy relace. Jedním z důvodů může být zlepšit výkon. Můžete například vytvořit vlastní soubor cookie obslužnou rutinu, která transformuje nebo optimalizuje token zabezpečení relace mezi jeho stav v paměti a co do souboru cookie. Chcete-li to provést, můžete nakonfigurovat <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=nameWithType> vlastnost <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=nameWithType> použít vlastní soubor cookie obslužnou rutinu, která je odvozena z <xref:System.IdentityModel.Services.CookieHandler?displayProperty=nameWithType>. <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=nameWithType> je výchozí popisovač souboru cookie, protože soubory cookie překročil povolenou velikost pro protokol HTTP (Hypertext Transfer); Pokud chcete místo toho použít vlastní soubor cookie obslužnou rutinu, je nutné implementovat rozdělování.  
  
 Další informace najdete v tématu [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) ukázka. Tento příklad ukazuje mezipaměti připravené relace farmy (na rozdíl od tokenreplycache) tak, že používáte relací odkazem místo výměna big soubory cookie. Tento příklad také znázorňuje jednodušší způsob zabezpečení soubory cookie ve farmě. Mezipaměť relace je založený na WCF. S ohledem na relaci, zabezpečení ukázka představuje novou funkci ve verzi WIF 4.5 transformačního souboru cookie podle MachineKey, což může být aktivovaný jednoduše vložením odpovídající fragment kódu v souboru web.config. Ukázka samotné není "pronájem", ale ukazuje, co je potřeba pro vytvoření aplikace připravené pro farmy.
