---
title: Správa relací WIF
ms.date: 03/30/2017
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
author: BrucePerlerMS
ms.openlocfilehash: 141eda509530cab1120d519c3cbc94693ef1cc51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946226"
---
# <a name="wif-session-management"></a>Správa relací WIF
Když se klient poprvé pokusí o přístup k chráněnému prostředku, který je hostovaný předávající stranou, klient se musí nejdřív ověřit ve službě tokenů zabezpečení (STS), která je pro předávající stranu důvěryhodná. Služba STS pak vydá token zabezpečení pro klienta. Klient prezentuje tento token předávající straně, což pak udělí klientovi přístup k chráněnému prostředku. Nechcete však, aby se klient musel znovu ověřit u služby STS pro každý požadavek, zejména proto, že nemusí být ani ve stejném počítači nebo ve stejné doméně jako předávající strana. Rozhraní Windows Identity Foundation (WIF) má klienta a předávající stranu místo toho, aby navázala relaci, ve které klient používá token zabezpečení relace ke svému ověření vůči předávající straně pro všechny požadavky po prvním požadavku. Předávající strana může použít token zabezpečení relace, který je uložený v souboru cookie pro rekonstrukci klienta <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>.  
  
 Služba STS definuje, jaké ověřování musí klient poskytnout. Klient ale může mít několik přihlašovacích údajů, se kterými se může sám ověřit ve službě STS. Může mít například token z Windows Live, uživatelské jméno a heslo, certifikát a SmartKey. V takovém případě STS udělí klientovi několik identit, přičemž každou identitu odpovídá jedné z přihlašovacích údajů, které klient prezentuje. Předávající strana může použít jednu nebo více těchto identit, když se rozhodne, jakou úroveň přístupu má klient udělit.  
  
 Slouží k rekonstrukci <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>klienta, který obsahuje všechny identity klienta v <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>nástroji. <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=nameWithType> Každý <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> v kolekci obsahuje tokeny Bootstrap, které jsou přidruženy k této identitě.  
  
 Pokud je vydaný nový token relace s ID relace původního tokenu relace, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=nameWithType> neaktualizuje token relace v mezipaměti tokenů. Vždy byste měli vytvořit instanci tokenu relace s jedinečným ID relace.  
  
> [!NOTE]
> Session. SecurityTokenHandler. ReadToken vyvolá <xref:System.Xml.XmlException> výjimku, pokud obdrží neplatný vstup, například pokud je soubor cookie obsahující token relace poškozený. Doporučujeme zachytit tuto výjimku a zajistit chování specifické pro aplikaci.  
  
 Pokud chráněná webová stránka obsahuje spoustu prostředků (například malých grafických objektů), které jsou také v chráněné doméně, musí se klient znovu ověřit pro předávající stranu, aby si stáhl každý z těchto prostředků. Použití tokenu ověřování relace zabraňuje nutnosti ověřovat službu STS pro každý požadavek, ale stále znamená, že se posílá mnoho souborů cookie. Je možné nastavit webovou stránku tak, aby se důležitá data a prostředky ukládaly v chráněné doméně, zatímco drobné položky jsou uloženy v nechráněné doméně a propojeny s z hlavní webové stránky. Také nastavte cestu k souboru cookie tak, aby odkazovala pouze na chráněnou doménu.  
  
 Aby bylo možné pracovat v režimu referenčního režimu, společnost Microsoft doporučuje <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> poskytnout obslužnou rutinu pro událost v souboru **Global.asax.cs** a nastavit vlastnost **IsReferenceMode** tokenu předaného ve <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> vlastnosti. Tyto aktualizace zajistí, že token relace funguje v referenčním režimu pro každý požadavek a upřednostňuje se pouze nastavením <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> vlastnosti v modulu ověřování relace.  
  
## <a name="extensibility"></a>Rozšiřitelnost  
 Mechanismus správy relace můžete roztáhnout. Jedním z důvodů je zvýšit výkon. Můžete například vytvořit vlastní obslužnou rutinu souborů cookie, která transformuje nebo optimalizuje token zabezpečení relace mezi stavem v paměti a tím, co přejde do souboru cookie. Chcete-li to provést, můžete nakonfigurovat <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=nameWithType> vlastnost <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=nameWithType> pro použití vlastní obslužné rutiny souborů cookie, která je odvozena z <xref:System.IdentityModel.Services.CookieHandler?displayProperty=nameWithType>. <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=nameWithType>je výchozí obslužná rutina souborů cookie, protože soubory cookie překračují povolenou velikost protokolu HTTP (Hypertext Transfer Protocol); Pokud místo toho použijete vlastní obslužnou rutinu souborů cookie, je nutné implementovat bloky dat.  
  
 Další informace najdete v tématu [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) Sample. V této ukázce se zobrazuje mezipaměť připravená pro farmu (na rozdíl od tokenreplycache), abyste mohli používat relace podle referenčních informací namísto výměny velkých souborů cookie. Tato ukázka také demonstruje snazší způsob zabezpečení souborů cookie ve farmě. Mezipaměť relace je založená na technologii WCF. V souvislosti se zabezpečením relací ukazuje ukázka novou funkci v WIF 4,5 transformace souborů cookie založené na MachineKey, kterou lze aktivovat pouhým vložením příslušného fragmentu do souboru Web. config. Samotný vzorek není "Farma", ale ukazuje, co potřebujete k tomu, abyste mohli farmu aplikací připravit.
