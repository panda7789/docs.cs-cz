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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e01d3ecf3367baed6673a66015918337105eecb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="code-access-security"></a>Zabezpečení přístupu kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Dnešní vysoce připojených počítačových systémů jsou často viditelné na kód, pochází z různých, případně neznámých zdrojů. Kód můžete připojit k e-mailu, obsažených v dokumentech nebo stažen z Internetu. Bohužel mnoho uživatelů počítačů má zkušenosti důsledky škodlivý mobilní kód, včetně virů a červů, které může dojít k poškození nebo zničení dat a náklady na čas a peníze.  
  
 Nejběžnější mechanismy zabezpečení udělit práva k uživatelů podle jejich přihlašovacích údajů (obvykle heslo) a omezit prostředky (často adresářů a souborů), které má uživatel přístup. Však tento postup selže řešit potíže se několik: uživatelé získat kód z mnoha zdrojů, některé z nich může nespolehlivé; kód může obsahovat chyby nebo chyby, které umožňují zneužití škodlivý kód; a kód někdy provádí věci, které uživatel nebude vědět, že je provádí. V důsledku toho může dojít k porušení počítačových systémů a osobní data můžou uniknout při opatrní a důvěryhodní uživatelé spuštění škodlivého nebo plný chyb softwaru. Většina mechanismy zabezpečení operačního systému vyžadovat, že každá část kódu, musí být zcela důvěryhodné aby bylo možné spustit, s výjimkou skriptů na webové stránce. Proto je zde stále zapotřebí široce použít bezpečnostní mechanismus, který umožňuje kód pocházející z jednoho počítače systému spuštění s ochranou v jiném systému, i když není žádný vztah důvěryhodnosti mezi systémy.  
  
 Rozhraní .NET Framework poskytuje mechanismus zabezpečení nazvaný zabezpečení přístupu kódu k ochraně počítačových systémů ze škodlivý kód mobilní, aby kód z neznámého původu pro spuštění s ochranou a pomáhá zabránit důvěryhodný kód z záměrně nebo neúmyslně ohrožení zabezpečení. Zabezpečení přístupu kódu umožňuje kódu být důvěryhodný na různých úrovních, v závislosti na tom, odkud pochází kód a na dalších aspektů identity kódu. Zabezpečení přístupu kódu taky vynutí různých úrovní důvěryhodnosti na kód, který minimalizuje množství kód, který musí být plně důvěryhodná, aby bylo možné spustit. Pomocí zabezpečení přístupu kódu může snížit pravděpodobnost, že váš kód bude došlo ke zneužití kódem škodlivý nebo plný chyb. Může snížit vaše odpovědnosti, protože můžete určit sadu operací, které váš kód by měl bude moct provádět. Zabezpečení přístupu kódu také může pomoci minimalizovat škody, které může být důsledkem chyby zabezpečení v kódu.  
  
> [!NOTE]
>  Zabezpečení přístupu kódu v byly provedeny změny hlavní [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Nejdůležitější změna byla [transparentnost zabezpečení](../../../docs/framework/misc/security-transparent-code.md), ale jsou taky jiné významné změny, které ovlivňují zabezpečení přístupu kódu. Informace o těchto změnách najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Zabezpečení přístupu kódu primárně ovlivňuje kód knihovny a částečně důvěryhodné aplikace. Vývojáři knihoven musí chránit svůj kód před neoprávněným přístupem z částečně důvěryhodné aplikace. Částečně důvěryhodné aplikace jsou aplikace, které jsou načteny z externích zdrojů, jako je Internet. Aplikace, které jsou nainstalovány v počítači nebo na místní intranet, spusťte v režimu plné důvěryhodnosti. Plně důvěryhodné aplikace nejsou ovlivněny zabezpečení přístupu kódu, pokud jsou označeny jako [transparentní pro zabezpečení](../../../docs/framework/misc/security-transparent-code.md), protože jsou plně důvěryhodné. Jediné omezení pro aplikace plné důvěryhodnosti je, že aplikace, které jsou označené <xref:System.Security.SecurityTransparentAttribute> atributu nelze volat kód, který je označený <xref:System.Security.SecurityCriticalAttribute> atribut. Částečně důvěryhodné aplikace musí být spuštěny v izolovaném prostoru (například v aplikaci Internet Explorer), takže zabezpečení přístupu kódu můžete použít. Pokud jste stáhnout aplikaci z Internetu a zkuste spustit z plochy, zobrazí se <xref:System.NotSupportedException> se zprávou: "byl učiněn pokus o načtení sestavení z umístění v síti, která by způsobila sestavení, které má být v izolovaném prostoru v předchozích verzích rozhraní .NET Framework. Tato verze rozhraní .NET Framework neumožňuje zásadu CAS ve výchozím nastavení, tak tato zatížení může být nebezpečný." Pokud jste si jistí, že aplikace mohou být důvěryhodné, můžete ji spustit jako úplný vztah důvěryhodnosti pomocí povolit [ \<loadfromremotesources – > element](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Informace o spuštění aplikace v izolovaném prostoru najdete v tématu [postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Všechny spravované kódu s cílem modul common language runtime obdrží výhody zabezpečení přístupu kódu, i v případě, že kód neprovádí zabezpečení přístupu jedné kódu volání. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Klíčové funkce zabezpečení přístupu kódu  
 Zabezpečení přístupu kódu pomáhá omezit přístup k chráněným prostředkům a operace. Zabezpečení přístupu kódu v rozhraní .NET Framework, provádí následující funkce:  
  
-   Definuje oprávnění a sady oprávnění, které představují práva pro přístup k různým prostředkům systému.  
  
-   Umožňuje kódu požadovat, aby jeho volající mít specifické oprávnění.  
  
-   Umožňuje kódu požadovat, jeho volající měl digitální podpis, což umožňuje volání chráněného kódu pouze volajícím z určité organizace nebo webu.  
  
-   Porovnání udělená oprávnění každého volajícího v zásobníku volání oprávnění, které volající musí mít vynucuje omezení kódu v době běhu.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Procházení zásobníku volání  
 K určení, zda kód je oprávněn k přístupu k prostředkům nebo k provedení operace, provede systém zabezpečení modulu runtime zásobníku volání, porovnává udělená oprávnění jednotlivých volajícího, aby požadováné. Pokud žádné volající v zásobníku volání nemá požadované oprávnění, je vyvolána výjimka zabezpečení a přístup je zamítnut. Procházení zásobníku je navržená tak, aby se zabránilo útokům typu luring, ve kterém méně důvěryhodný kód volá vysoce důvěryhodný kód a používá ho k neoprávněným akcím. Náročných oprávnění všech volajících v době běhu ovlivňuje výkon, ale je nezbytné k ochraně proti útokům typu luring kódem méně důvěryhodný kód. Za účelem optimalizace výkonu, může mít kód provést méně procházení zásobníku; musí být ale, že vždy, když to uděláte není vystavit slabá místa zabezpečení.  
  
 Následující obrázek znázorňuje procházení zásobníku, který nastane, když metoda v sestavení A4 vyžaduje, aby její volající měli oprávnění P.  
  
 ![Zabezpečení přístupu ke kódu](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Procházení zásobníku zabezpečení  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md)|Popisuje zabezpečení přístupu kódu a jeho nejčastější použití.|  
|[Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|Popisuje průhlednost model zabezpečení v nástroji [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].|  
|[Používání knihoven z částečně důvěryhodného kódu](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|Popisuje postup povolení knihovny pro použití s nespravovaným kódem a používání knihoven z nespravovaného kódu.|  
|[Klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md)|Poskytuje přehled mnoha klíčových pojmů a koncepty používané v systému zabezpečení rozhraní .NET Framework.|  
|[Zabezpečení na základě rolí](../../../docs/standard/security/role-based-security.md)|Popisuje, jak začlenit zabezpečení na základě rolí.|  
|[Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)|Popisuje, jak začlenit kryptografie do vaší aplikace.|
