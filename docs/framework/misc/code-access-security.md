---
title: Zabezpečení přístupu kódu
description: Seznamte se s mechanismem zabezpečení přístupu kódu v rozhraní .NET, který pomáhá chránit počítačové systémy před škodlivým mobilním kódem.
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
ms.openlocfilehash: 6fa7983d0355a9e11728f8dbd0f4e06bbb0f8e5b
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281638"
---
# <a name="code-access-security"></a>Zabezpečení přístupu kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Dnešní vysoce připojené počítačové systémy se často zveřejňují pro kód pocházející z různých, případně neznámých zdrojů. Kód může být připojen k e-mailu, obsažený v dokumentech nebo stažen prostřednictvím Internetu. Mnoho uživatelů počítačů bohužel sami účinky škodlivého mobilního kódu, včetně virů a červů, což může poškodit nebo zničit data a náklady a peníze.  
  
 Nejběžnější mechanismy zabezpečení poskytují uživatelům práva na základě přihlašovacích přihlašovacích údajů (obvykle hesla) a omezují prostředky (často se jedná o adresáře a soubory), ke kterým má uživatel povolený přístup. Tento přístup ale nedokáže vyřešit několik problémů: uživatelé získávají kód z mnoha zdrojů, z nichž některé můžou být nespolehlivé; kód může obsahovat chyby nebo chyby zabezpečení, které umožňují jeho zneužití škodlivým kódem. a kód někdy provede něco, co uživatel neví, že to bude dělat. V důsledku toho může dojít k poškození počítačových systémů a k úniku soukromých dat v případě, že obezřetní a věrohodní Uživatelé spouštějí škodlivý nebo chybově vypsaný software. Většina mechanismů zabezpečení operačních systémů vyžaduje, aby každá část kódu musela být plně důvěryhodná, aby ji bylo možné spustit, s výjimkou skriptů na webové stránce. Proto je stále potřeba mít široce použitelný mechanismus zabezpečení, který umožňuje, aby kód pocházející z jednoho počítačového systému běžel s ochranou v jiném systému, a to i v případě, že mezi systémy neexistují žádné vztahy důvěryhodnosti.  
  
 .NET Framework poskytuje mechanismus zabezpečení, který se nazývá zabezpečení přístupu kódu k ochraně počítačových systémů před škodlivým kódem, aby bylo možné spustit kód z neznámých původních zdrojů s ochranou, a zajistit, aby byl důvěryhodný kód v úmyslu nebo omylem ohrozit zabezpečení. Zabezpečení přístupu kódu umožňuje, aby kód byl důvěryhodný pro různé stupně v závislosti na tom, kde kód pochází, a na dalších aspektech identity kódu. Zabezpečení přístupu kódu taky vynutilo proměnlivé úrovně důvěry na kódu, což minimalizuje množství kódu, který musí být plně důvěryhodný, aby bylo možné spustit. Použití zabezpečení přístupu kódu může snížit pravděpodobnost, že váš kód bude omylem použit škodlivým kódem nebo kódem vyplněným chybou. Může snížit vaši zodpovědnost, protože můžete zadat sadu operací, které by měl váš kód provádět. Zabezpečení přístupu kódu také může přispět k minimalizaci škod, které mohou být výsledkem chyb zabezpečení ve vašem kódu.  
  
> [!NOTE]
> V .NET Framework 4 byly provedeny významné změny zabezpečení přístupu kódu. Nejvýznamnější změnou je [transparentnost zabezpečení](security-transparent-code.md), ale existují i další významné změny, které ovlivňují zabezpečení přístupu kódu. Informace o těchto změnách najdete v tématu [změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Zabezpečení přístupu kódu primárně ovlivňuje kód knihovny a částečně důvěryhodné aplikace. Vývojáři knihovny musí chránit svůj kód před neoprávněným přístupem z částečně důvěryhodných aplikací. Částečně důvěryhodné aplikace jsou aplikace, které jsou načteny z externích zdrojů, jako je například Internet. Aplikace nainstalované na počítači nebo v místním intranetu běží v úplném vztahu důvěryhodnosti. Aplikace s plnou důvěryhodností neovlivní zabezpečení přístupu kódu, pokud nejsou označeny jako transparentní z hlediska [zabezpečení](security-transparent-code.md), protože jsou plně důvěryhodné. Jediným omezením pro plně důvěryhodné aplikace je, že aplikace, které jsou označeny <xref:System.Security.SecurityTransparentAttribute> atributem, nemohou volat kód, který je označen <xref:System.Security.SecurityCriticalAttribute> atributem. Částečně důvěryhodné aplikace musí být spuštěny v izolovaném prostoru (například v Internet Exploreru), aby bylo možné použít zabezpečení přístupu kódu. Pokud si stáhnete aplikaci z Internetu a pokusíte se ji spustit z plochy, zobrazí <xref:System.NotSupportedException> se zpráva s upozorněním: "došlo k pokusu o načtení sestavení ze síťového umístění, které by způsobilo, že sestavení bylo v předchozích verzích .NET Framework v izolovaném prostoru. Tato verze .NET Framework ve výchozím nastavení nepovoluje zásady CAS, takže toto zatížení může být nebezpečné. " Pokud jste si jisti, že aplikace může být důvěryhodná, můžete ji povolit spustit jako úplný vztah důvěryhodnosti pomocí [ \<loadFromRemoteSources> elementu](../configure-apps/file-schema/runtime/loadfromremotesources-element.md). Informace o spuštění aplikace v izolovaném prostoru (sandbox) naleznete v tématu [How to: Run částečně důvěryhodný kód v izolovaném prostoru (sandboxu)](how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Veškerý spravovaný kód, který cílí na modul CLR (Common Language Runtime), obdrží výhody zabezpečení přístupu kódu, a to i v případě, že tento kód neprovádí volání zabezpečení přístupu kódu. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](code-access-security-basics.md).  
  
<a name="key_functions"></a>
## <a name="key-functions-of-code-access-security"></a>Klíčové funkce zabezpečení přístupu kódu  
 Zabezpečení přístupu kódu pomáhá omezit přístup tohoto kódu k chráněným prostředkům a operacím. V .NET Framework zabezpečení přístupu kódu provádí následující funkce:  
  
- Definuje oprávnění a sady oprávnění, které reprezentují právo na přístup k různým systémovým prostředkům.  
  
- Umožňuje kódu požadovat, aby jeho volající měl určitá oprávnění.  
  
- Umožňuje, aby kód vyvolal, že jeho volající mají digitální podpis, což umožňuje pouze volajícím z konkrétní organizace nebo webu volat chráněný kód.  
  
- Vynutila omezení kódu za běhu tím, že porovná udělená oprávnění každého volajícího v zásobníku volání k oprávněním, která volající musí mít.  
  
<a name="walking_the_call_stack"></a>
## <a name="walking-the-call-stack"></a>Procházení zásobníku volání  
 Chcete-li určit, zda je kód autorizován pro přístup k prostředku nebo provést operaci, provede systém zabezpečení modulu runtime zásobník volání a porovná udělená oprávnění každého volající k oprávněním, která se vyžadují. Pokud nějaký volající v zásobníku volání nemá požadované oprávnění, je vyvolána výjimka zabezpečení a přístup je odmítnut. Procházení zásobníku je navrženo tak, aby pomohla zabránit útokům luring, ve kterých méně důvěryhodný kód volá vysoce důvěryhodný kód a používá ho k provádění neautorizovaných akcí. Náročná oprávnění všech volajících za běhu mají vliv na výkon, ale je nezbytné přispět k ochraně kódu před útoky luring pomocí méně důvěryhodného kódu. Pro optimalizaci výkonu může váš kód provádět méně procházení zásobníku; je ale potřeba mít jistotu, že když to uděláte, nebudete moct odhalit slabá místa zabezpečení.  
  
 Následující ilustrace znázorňuje průchod zásobníku, který je výsledkem, když metoda v sestavení A4 požaduje, aby jeho volající měl oprávnění P.  
  
 ![Zabezpečení přístupu kódu](media/slide-10a.gif "slide_10a")  
Procházení zásobníku zabezpečení  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Základy zabezpečení přístupu kódu](code-access-security-basics.md)|Popisuje zabezpečení přístupu kódu a jeho nejběžnější použití.|  
|[Transparentní kód pro zabezpečení, úroveň 2](security-transparent-code-level-2.md)|Popisuje model transparentnosti zabezpečení v .NET Framework 4.|  
|[Používání knihoven z částečně důvěryhodného kódu](using-libraries-from-partially-trusted-code.md)|Popisuje, jak povolit knihovny pro použití s nespravovaným kódem a jak používat knihovny z nespravovaného kódu.|  
|[Klíčové koncepty zabezpečení](../../standard/security/key-security-concepts.md)|Poskytuje přehled mnoha klíčových pojmů a konceptů používaných v systému .NET Framework Security.|  
|[Zabezpečení na základě rolí](../../standard/security/role-based-security.md)|Popisuje, jak začlenit zabezpečení na základě rolí.|  
|[Šifrovací služby](../../standard/security/cryptographic-services.md)|Popisuje, jak začlenit do svých aplikací kryptografii.|
