---
title: Zabezpečení přístupu kódu
ms.date: 03/30/2017
helpviewer_keywords:
- named permission sets, code access security
- call stacks
- malicious code
- stack walk
- security [.NET Framework], code access security
- permissions [.NET Framework], code access security
- trusted code
- mobile code security
- unmanaged code, code access security
- granting permissions, code access security
- user authentication, code access security
- code access security
ms.assetid: 859af632-c80d-4736-8d6f-1e01b09ce127
ms.openlocfilehash: 7b4f4c1c3f768e5e7c0bb8f6c0e3c6444faf7d0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181187"
---
# <a name="code-access-security"></a>Zabezpečení přístupu kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Dnešní vysoce propojené počítačové systémy jsou často vystaveny kódu pocházejícímu z různých, možná neznámých zdrojů. Kód lze připojit k e-mailu, obsažené v dokumentech nebo stáhnout přes Internet. Bohužel, mnoho uživatelů počítačů zažili z první ruky účinky škodlivého mobilního kódu, včetně virů a červů, které mohou poškodit nebo zničit data a náklady na čas a peníze.  
  
 Nejběžnější mechanismy zabezpečení poskytují práva uživatelům na základě jejich přihlašovacích pověření (obvykle heslo) a omezují prostředky (často adresáře a soubory), ke kterým má uživatel povolen přístup. Tento přístup však neřeší několik problémů: uživatelé získají kód z mnoha zdrojů, z nichž některé mohou být nespolehlivé; kód může obsahovat chyby nebo chyby zabezpečení, které umožňují jeho zneužití škodlivým kódem; a kód někdy dělá věci, které uživatel neví, že bude dělat. V důsledku toho mohou být počítačové systémy poškozeny a soukromá data mohou být nezrazena, pokud opatrní a důvěryhodní uživatelé spustí škodlivý software nebo software naplněný chybami. Většina mechanismů zabezpečení operačního systému vyžaduje, aby každá část kódu byla zcela důvěryhodná, aby bylo možné spustit, s výjimkou skriptů na webové stránce. Proto je stále potřeba široce použitelný bezpečnostní mechanismus, který umožňuje kód pocházející z jednoho počítačového systému spustit s ochranou v jiném systému, i když neexistuje žádný vztah důvěryhodnosti mezi systémy.  
  
 Rozhraní .NET Framework poskytuje mechanismus zabezpečení nazývaný zabezpečení přístupu kódu, který pomáhá chránit počítačové systémy před škodlivým mobilním kódem, povolit spuštění kódu z neznámého původu s ochranou a zabránění úmyslnému nebo náhodnému použití důvěryhodného kódu ohrožení bezpečnosti. Zabezpečení přístupu kódu umožňuje kód důvěryhodný v různé míře v závislosti na tom, odkud kód pochází a na dalších aspektech identity kódu. Zabezpečení přístupu kódu také vynucuje různé úrovně důvěryhodnosti kódu, což minimalizuje množství kódu, který musí být plně důvěryhodný, aby bylo možné spustit. Použití zabezpečení přístupu kódu může snížit pravděpodobnost, že váš kód bude zneužit škodlivým kódem nebo kódem naplněným chybou. Může snížit vaši odpovědnost, protože můžete určit sadu operací, které by měl být váš kód povolen k provedení. Zabezpečení přístupu kódu může také pomoci minimalizovat škody, které mohou vyplývat z chyb zabezpečení ve vašem kódu.  
  
> [!NOTE]
> Byly provedeny velké změny zabezpečení přístupu kódu v rozhraní .NET Framework 4. Nejpozoruhodnější změnou byla [transparentnost zabezpečení](security-transparent-code.md), ale existují také další významné změny, které ovlivňují zabezpečení přístupu kódu. Informace o těchto změnách naleznete v [tématu Změny zabezpečení](../security/security-changes.md).  
  
 Zabezpečení přístupu kódu se týká především kódu knihovny a částečně důvěryhodných aplikací. Vývojáři knihovny musí chránit svůj kód před neoprávněným přístupem před částečně důvěryhodnými aplikacemi. Částečně důvěryhodné aplikace jsou aplikace, které jsou načteny z externích zdrojů, jako je například Internet. Aplikace nainstalované na ploše nebo v místním intranetu jsou spuštěny v plné důvěryhodnosti. Plně důvěryhodné aplikace nejsou ovlivněny zabezpečením přístupu kódu, pokud nejsou označeny jako [transparentní pro zabezpečení](security-transparent-code.md), protože jsou plně důvěryhodné. Jediným omezením pro plně důvěryhodné aplikace je, <xref:System.Security.SecurityTransparentAttribute> že aplikace, které jsou <xref:System.Security.SecurityCriticalAttribute> označeny atributem nelze volat kód, který je označen atributem. Částečně důvěryhodné aplikace musí být spuštěny v izolovaném prostoru (například v aplikaci Internet Explorer), aby bylo možné použít zabezpečení přístupu kódu. Pokud stáhnete aplikaci z Internetu a pokusíte se ji <xref:System.NotSupportedException> spustit z plochy, zobrazí se zpráva s odkazem: "Došlo k pokusu o načtení sestavení ze síťového umístění, které by způsobilo, že sestavení bylo v předchozích verzích rozhraní .NET Framework v izolovaném prostoru. Tato verze rozhraní .NET Framework ve výchozím nastavení nepovoluje zásady CAS, takže toto zatížení může být nebezpečné." Pokud jste si jisti, že aplikace může být důvěryhodný, můžete povolit, aby byl spuštěn jako úplný vztah důvěryhodnosti pomocí [ \<loadFromRemoteSources> element](../configure-apps/file-schema/runtime/loadfromremotesources-element.md). Informace o spuštění aplikace v izolovaném prostoru naleznete v tématu [Postup: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Veškerý spravovaný kód, který cílí na běžný jazyk runtime obdrží výhody zabezpečení přístupu kódu, i v případě, že tento kód neprovede volání zabezpečení přístupu k jednomu kódu. Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](code-access-security-basics.md).  
  
<a name="key_functions"></a>
## <a name="key-functions-of-code-access-security"></a>Klíčové funkce zabezpečení přístupu ke kódu  
 Zabezpečení přístupu kódu pomáhá omezit přístup, který má kód k chráněným prostředkům a operacím. V rozhraní .NET Framework provádí zabezpečení přístupu kódu následující funkce:  
  
- Definuje oprávnění a sady oprávnění, které představují právo na přístup k různým systémovým prostředkům.  
  
- Umožňuje kód požadovat, aby jeho volající mají určitá oprávnění.  
  
- Umožňuje kódu požadovat, aby jeho volající měli digitální podpis, což umožňuje volání chráněného kódu pouze volajícím z určité organizace nebo webu.  
  
- Vynucuje omezení kódu za běhu porovnáním udělených oprávnění každého volajícího v zásobníku volání s oprávněními, která musí mít volající.  
  
<a name="walking_the_call_stack"></a>
## <a name="walking-the-call-stack"></a>Chůze volání Zásobník  
 Chcete-li zjistit, zda je kód oprávněn k přístupu k prostředku nebo k provedení operace, systém zabezpečení za běhu prochází zásobníkvolání a porovnává udělená oprávnění každého volajícího s požadovaným oprávněním. Pokud některý volající v zásobníku volání nemá požadované oprávnění, je vyvolána výjimka zabezpečení a přístup je odmítnut. Procházení zásobníku je navrženo tak, aby pomohlo zabránit lákavým útokům, ve kterých méně důvěryhodný kód volá vysoce důvěryhodný kód a používá jej k provádění neoprávněných akcí. Náročné oprávnění všech volajících za běhu ovlivňuje výkon, ale je nezbytné chránit kód před lákáním útoků méně důvěryhodným kódem. Chcete-li optimalizovat výkon, můžete mít váš kód provádět méně procházení zásobníku; však musíte být jisti, že není vystavit slabé stránky zabezpečení při každém této provedete.  
  
 Následující obrázek znázorňuje procházení zásobníku, které je výsledkem, když metoda v sestavení A4 vyžaduje, aby její volající měli oprávnění P.  
  
 ![Zabezpečení přístupu kódu](media/slide-10a.gif "slide_10a")  
Procházení zásobníku zabezpečení  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Základy zabezpečení přístupu kódu](code-access-security-basics.md)|Popisuje zabezpečení přístupu kódu a jeho nejběžnější použití.|  
|[Transparentní kód pro zabezpečení, úroveň 2](security-transparent-code-level-2.md)|Popisuje model transparentnosti zabezpečení v rozhraní .NET Framework 4.|  
|[Používání knihoven z částečně důvěryhodného kódu](using-libraries-from-partially-trusted-code.md)|Popisuje, jak povolit knihovny pro použití s nespravovaným kódem a jak používat knihovny z nespravovaného kódu.|  
|[Klíčové koncepty zabezpečení](../../standard/security/key-security-concepts.md)|Obsahuje přehled mnoha klíčových termínů a konceptů používaných v systému zabezpečení rozhraní .NET Framework.|  
|[Zabezpečení na základě rolí](../../standard/security/role-based-security.md)|Popisuje, jak začlenit zabezpečení na základě rolí.|  
|[Kryptografické služby](../../standard/security/cryptographic-services.md)|Popisuje, jak do aplikací začlenit kryptografii.|
