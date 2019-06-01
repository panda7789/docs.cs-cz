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
ms.openlocfilehash: aa256fe95013494488ff52258186763fab7a85c9
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456655"
---
# <a name="code-access-security"></a>Zabezpečení přístupu kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Dnešní vysoce propojenými počítačových systémů jsou často vystaveni kódu, který pochází z různých, může být neznámé zdroje. Kód můžete připojit k e-mailu, obsažených v dokumentech nebo stáhnout z Internetu. Bohužel mnoha uživateli počítače mají zkušenosti s účinky škodlivý mobilního kódu, včetně virů a červů, které mohou poškodit nebo zničit dat a náklady na čas a peníze.  
  
 Nejběžnější mechanismy zabezpečení předejte práva uživatelů podle jejich přihlašovacích údajů (obvykle heslo) a omezit prostředky (často adresářů a souborů), které má uživatel přístup. Ale tento postup selže několik problémů: uživatelé získat kód z mnoha zdrojů, z nichž některé můžou nespolehlivé; kód může obsahovat chyby nebo chyby, které umožňují zneužití škodlivým kódem; a kód někdy provádí věcí, které uživatel neví, že se že bude provádět. V důsledku toho počítačových systémů může být poškozen a soukromým datům může uniknout při spuštění škodlivého nebo plný chyb softwaru opatrní a důvěryhodní uživatelé. Většina mechanismů pro zabezpečení operačního systému vyžadují, musí být plně důvěryhodná každou část kódu, aby bylo možné spustit, s výjimkou skriptů na webové stránce. Proto se stále potřeba široce příslušné bezpečnostní mechanismus, který umožňuje kód pocházející z jednoho počítače systému na provedení s ochranou v jiném systému, i v případě, že neexistuje žádný vztah důvěry mezi systémy.  
  
 Rozhraní .NET Framework poskytuje mechanismus zabezpečení volá zabezpečení přístupu kódu k ochraně počítačové systémy před škodlivým mobilní kód umožňující kódu z neznámých zdrojů ke spuštění s ochranou a pomáhá zabránit důvěryhodného kódu z úmyslně ani náhodně tím bylo narušeno zabezpečení. Zabezpečení přístupu kódu umožňuje kódu důvěryhodné na různých úrovních, v závislosti na tom, odkud pochází kód a o dalších aspektech identity kódu. Zabezpečení přístupu kódu vynucuje také různé úrovně důvěryhodnosti na kód, který minimalizuje množství kódu, který musí být plně důvěryhodné, aby bylo možné spustit. Pomocí zabezpečení přístupu kódu může snížit pravděpodobnost, že váš kód bude zneužity škodlivých aktivit nebo Chyba vyplněný kód. Může snížit vaše odpovědnosti, protože můžete určit sadu operací, které váš kód by měl povoleno provádět. Zabezpečení přístupu kódu může také pomoct minimalizovat škody, které můžou být výsledkem ohrožení zabezpečení v kódu.  
  
> [!NOTE]
>  Důležité změny byly provedeny na zabezpečení přístupu kódu v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Byl nejdůležitější změny [transparentnosti zabezpečení](../../../docs/framework/misc/security-transparent-code.md), ale jsou taky mezi další výrazné změny, které mají vliv na zabezpečení přístupu kódu. Informace o těchto změnách najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Zabezpečení přístupu kódu má vliv na primárně knihovny kódu a částečně důvěryhodné aplikace. Knihovna vývojáři musí chránit svůj kód před neoprávněným přístupem z částečně důvěryhodné aplikace. Částečně důvěryhodné aplikace jsou aplikace, které jsou načteny z externích zdrojů, jako je Internet. Aplikace, které jsou nainstalovány v počítači nebo v místním intranetu spustit v režimu plné důvěryhodnosti. Aplikace úplného vztahu důvěryhodnosti nejsou ovlivněny zabezpečení přístupu kódu, pokud nejsou označeny jako [transparentní pro zabezpečení](../../../docs/framework/misc/security-transparent-code.md), protože jsou plně důvěryhodné. Jediným omezením pro úplného vztahu důvěryhodnosti aplikace je, že aplikace, které jsou označeny <xref:System.Security.SecurityTransparentAttribute> atribut nejde volat kód, který je označen <xref:System.Security.SecurityCriticalAttribute> atribut. Částečně důvěryhodné aplikace musí být spuštěn v izolovaném prostoru (třeba v Internet Exploreru) tak, aby se dají nastavit zabezpečení přístupu kódu. Pokud aplikaci stáhnout z Internetu a zkuste spustit z plochy, zobrazí se <xref:System.NotSupportedException> s touto zprávou: "Proběhl pokus o načtení sestavení z umístění v síti, které by způsobily sestavení do izolovaného prostoru v předchozích verzích rozhraní .NET Framework. Tato verze rozhraní .NET Framework nepovolí zásady CAS ve výchozím nastavení, takže toto načtení může být nebezpečné." Pokud jste si jistí, že aplikace může považovat za důvěryhodné, můžete povolit, aby byla spuštěna jako úplný vztah důvěryhodnosti s použitím [ \<loadFromRemoteSources > element](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Informace o spuštění aplikace v izolovaném prostoru, naleznete v tématu [jak: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Všechen spravovaný kód, který cílí, modul common language runtime získává výhody zabezpečení přístupu kódu, i v případě, že kód neprovede volání zabezpečení přístupu jednoho kódu. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Klíčové funkce zabezpečení přístupu kódu  
 Zabezpečení přístupu kódu pomáhá omezit přístup ke kódu, který má k chráněným prostředkům a operacím. Zabezpečení přístupu kódu v rozhraní .NET Framework, provádí následující funkce:  
  
- Definuje oprávnění a sady oprávnění, které představují práva pro přístup k různým prostředkům systému.  
  
- Umožňuje poptávku, že jeho volající nemá oprávnění kódu.  
  
- Umožňuje kódu na vyžádání, že jeho volající nemá digitální podpis, což umožní volat chráněné kód pouze volající z konkrétní organizace nebo webu.  
  
- Vynucuje omezení kódu v době běhu porovnáním udělená oprávnění každý volající v zásobníku volání, které volající musí mít oprávnění.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Procházení zásobníku volání  
 Pokud chcete zjistit, zda kód je oprávněn přistupovat k prostředku nebo provedení operace, vás systém zabezpečení modulu runtime zásobník volání, porovnání každého volajícího požadováné oprávnění udělená oprávnění. Pokud jakýkoli volající v zásobníku volání nemá požadované oprávnění, je vyvolána výjimka zabezpečení a přístup je zamítnut. Procházení zásobníku je určena k zabránění lákajícím útokům, ve kterém méně důvěryhodnému kódu volá vysoce důvěryhodným kódem a použije ho k provedení neoprávněným akcím. Požadování oprávnění všech volajících v době běhu má vliv na výkon, ale je nezbytné k ochraně proti útokům typu luring kódem méně důvěryhodnému kódu. Za účelem optimalizace výkonu můžete mít kód provádět méně procházení zásobníku; musí být ale, že pokaždé, když to uděláte bez odkrytí slabé stránky zabezpečení.  
  
 Následující obrázek znázorňuje procházení zásobníku, která vznikne, když na metodu v sestavení A4 se požadavky, jeho volající máte oprávnění P.  
  
 ![Zabezpečení přístupu ke kódu](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Procházení zásobníku zabezpečení  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Základy zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security-basics.md)|Popisuje zabezpečení přístupu kódu a jeho nejběžnější použití.|  
|[Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|Popisuje model transparentnosti zabezpečení v rozhraní .NET Framework 4.|  
|[Používání knihoven z částečně důvěryhodného kódu](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|Popisuje postup povolení knihovny pro použití s nespravovaným kódem a jak používat knihovny z nespravovaného kódu.|  
|[Klíčové koncepty zabezpečení](../../../docs/standard/security/key-security-concepts.md)|Poskytuje přehled mnoha klíčové pojmy a koncepty používané v systém zabezpečení rozhraní .NET Framework.|  
|[Zabezpečení na základě rolí](../../../docs/standard/security/role-based-security.md)|Popisuje, jak začlenit zabezpečení na základě rolí.|  
|[Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)|Popisuje, jak začlenit do svých aplikací kryptografie.|
