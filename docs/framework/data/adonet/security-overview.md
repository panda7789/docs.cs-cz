---
title: Přehled zabezpečení
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 8a036a40d2b1728f39037018c3672551b8b67bd9
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545026"
---
# <a name="security-overview"></a>Přehled zabezpečení

Zabezpečení aplikace je nepřetržitý proces. Nikdy nebudete mít k dispozici žádný bod, ve kterém může vývojář zaručit, že aplikace je bezpečná před všemi útoky, protože není možné předpovědět, jaké druhy budoucích útoků přináší nové technologie. Naopak, protože nikdo dosud nezjistil (nebo publikoval) nedostatky zabezpečení v systému, neznamená, že žádný neexistuje nebo může existovat. Musíte naplánovat zabezpečení v rámci fáze návrhu projektu a také naplánovat způsob, jakým se bude udržovat zabezpečení po celou dobu životnosti aplikace.

## <a name="design-for-security"></a>Návrh pro zabezpečení
 Jedním z největších problémů při vývoji zabezpečených aplikací je, že zabezpečení je často dodatečně, což je implementace po dokončení kódu projektu. Nevytváření zabezpečení v aplikaci v počátku vede k nezabezpečeným aplikacím, protože k tomu, že je aplikace zabezpečená, je dána málo myšlená.

 Poslední minutová implementace zabezpečení vede k většímu počtu chyb, jako je softwarová přerušení v rámci nových omezení nebo musí být přepsána, aby vyhovovala neočekávaným funkcím. Každý řádek revidovaného kódu obsahuje možnost zavedení nové chyby. Z tohoto důvodu byste měli zvážit zabezpečení v rané fázi vývoje, aby bylo možné pokračovat v sestavách společně s vývojem nových funkcí.

### <a name="threat-modeling"></a>Modelování hrozeb
 Proti útokům nelze chránit systém, pokud nerozumíte všem potenciálním útokům, které jsou vystaveny. K určení pravděpodobnosti a důsledky narušení zabezpečení ve vaší aplikaci ADO.NET je potřeba proces hodnocení bezpečnostních hrozeb označovaných jako *modelování hrozeb*.

 Modelování hrozeb se skládá ze tří kroků vysoké úrovně: princip zobrazení nežádoucí osoba, characterizing zabezpečení systému a určení hrozeb.

 Modelování hrozeb je iterativním přístupem k vyhodnocování ohrožení zabezpečení ve vaší aplikaci, aby bylo možné najít ty, které jsou nejbezpečnější, protože zpřístupňují nejvíc citlivých dat. Jakmile zjistíte ohrožení zabezpečení, zařadíte je v pořadí podle závažnosti a vytvoříte sadu protiopatření pro účely čítače hrozeb.

Další informace naleznete v následujících zdrojích:

|Prostředek|Popis|
|--------------|-----------------|
|Web [modelování hrozeb](https://www.microsoft.com/securityengineering/sdl/threatmodeling) na portálu Security Engineering|Prostředky na této stránce vám pomůžou pochopit proces modelování hrozeb a vytvářet modely hrozeb, které můžete použít k zabezpečení vlastních aplikací.|

## <a name="the-principle-of-least-privilege"></a>Princip nejnižších oprávnění
 Při navrhování, sestavování a nasazování aplikace musíte předpokládat, že vaše aplikace bude napadena. Tyto útoky často pocházejí ze škodlivého kódu, který se spouští s oprávněními uživatele, který spouští kód. Jiné můžou pocházet s dobře úmyslným kódem, který zneužije útočník. Při plánování zabezpečení vždy se předpokládá, že dojde k nejhoršímu scénáři.

 Jedním z čítačů měření, které můžete využít, je pokus o navýšení co největšího množství zdí, pokud je to možné, a to spuštěním s nejnižšími oprávněními. Princip nejnižších oprávnění znamená, že kterékoli dané oprávnění by mělo být uděleno na nejnižší množství kódu, který je nezbytný pro nejkratší dobu potřebnou k provedení úlohy.

 Osvědčeným postupem při vytváření zabezpečených aplikací je začínat bez oprávnění a pak přidat nejužší oprávnění pro konkrétní úkol, který se provádí. Naopak počínaje všemi oprávněními a jejich odepření vede k nezabezpečeným aplikacím, které se obtížně testují a udržují, protože bezpečnostní otvory můžou existovat neúmyslnému udělení více oprávnění, než je potřeba.

Další informace o zabezpečení aplikací najdete v následujících zdrojích informací:

|Prostředek|Popis|
|--------------|-----------------|
|[Zabezpečování aplikací](/visualstudio/ide/securing-applications)|Obsahuje odkazy na obecná témata zabezpečení. Obsahuje také odkazy na témata týkající se zabezpečení distribuovaných aplikací, webových aplikací, mobilních aplikací a aplikací klasické pracovní plochy.|

## <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)

Zabezpečení přístupu kódu (CAS) je mechanismus, který pomáhá omezit přístup kódu k chráněným prostředkům a operacím. V .NET Framework CAS provádí následující funkce:

- Definuje oprávnění a sady oprávnění, které reprezentují právo na přístup k různým systémovým prostředkům.

- Umožňuje správcům konfigurovat zásady zabezpečení přidružením sad oprávnění ke skupinám kódu (skupin kódu).

- Umožňuje kódu požádat o oprávnění, která vyžaduje, aby bylo možné spustit, a také oprávnění, která by byla užitečná, a určuje, která oprávnění kód nesmí mít nikdy.

- Uděluje oprávnění pro každé načtené sestavení na základě oprávnění, která požaduje kód, a operací povolených zásadami zabezpečení.

- Umožňuje kódu požadovat, aby jeho volající měl určitá oprávnění.

- Umožňuje, aby kód vyvolal, že jeho volající mají digitální podpis, což umožňuje pouze volajícím z konkrétní organizace nebo webu volat chráněný kód.

- Vynutila omezení kódu za běhu tím, že porovná udělená oprávnění každého volajícího v zásobníku volání k oprávněním, která volající musí mít.

Chcete-li minimalizovat množství škod, ke kterým může dojít v případě úspěšného útoku, vyberte kontext zabezpečení pro váš kód, který uděluje přístup pouze k prostředkům, které potřebuje k tomu, aby bylo možné svou práci provést a žádné další.

Další informace naleznete v následujících zdrojích:

|Prostředek|Popis|
|--------------|-----------------|
|[Zabezpečení přístupu ke kódu a ADO.NET](code-access-security.md)|Popisuje interakce mezi zabezpečením přístupu kódu, zabezpečením založeným na rolích a částečně důvěryhodnými prostředími z perspektivy aplikace ADO.NET.|
|[Zabezpečení přístupu kódu](../../misc/code-access-security.md)|Obsahuje odkazy na další témata popisující certifikační autority v .NET Framework.|

## <a name="database-security"></a>Zabezpečení databáze

Princip nejnižší úrovně oprávnění platí také pro váš zdroj dat. Mezi obecné pokyny k zabezpečení databáze patří:

- Vytvořte účty s nejnižšími možnými oprávněními.

- Nepovolujte uživatelům přístup k účtům správců jenom k tomu, aby mohli pracovat s kódem.

- Nevracet do klientských aplikací chybové zprávy na straně serveru.

- Ověřte všechny vstupy jak na klientovi, tak na serveru.

- Použijte parametrizované příkazy a vyhněte se dynamickým příkazům SQL.

- Povolte auditování zabezpečení a protokolování databáze, kterou používáte, abyste byli upozorňováni na případné porušení zabezpečení.

Další informace naleznete v následujících zdrojích:

|Prostředek|Popis|
|--------------|-----------------|
|[SQL Server – zabezpečení](./sql/sql-server-security.md)|Poskytuje přehled o zabezpečení SQL Server s využitím scénářů aplikací, které poskytují pokyny k vytváření zabezpečených aplikací ADO.NET, které cílí na SQL Server.|
|[Doporučení pro strategie přístupu k datům](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Poskytuje doporučení pro přístup k datům a provádění databázových operací.|

## <a name="security-policy-and-administration"></a>Zásady zabezpečení a Správa

Nepatřičná Správa zásad zabezpečení přístupu kódu (CAS) může potenciálně vytvářet slabá místa zabezpečení. Po nasazení aplikace by se měly používat techniky pro monitorování zabezpečení a rizika vyhodnocená jako nové hrozby.

Další informace naleznete v následujících zdrojích:

|Prostředek|Popis|
|--------------|-----------------|
|[Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))|Poskytuje informace o vytváření a správě zásad zabezpečení.|
|[Osvědčené postupy pro zásady zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))|Obsahuje odkazy, které popisují, jak spravovat zásady zabezpečení.|

## <a name="see-also"></a>Viz také:

- [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)
- [Zabezpečení v .NET](../../../standard/security/index.md)
- [SQL Server – zabezpečení](./sql/sql-server-security.md)
- [Přehled ADO.NET](ado-net-overview.md)
