---
title: "Kód transparentní pro zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 996da59640281c8584774fa9e66b42619753afb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="security-transparent-code"></a>Kód transparentní pro zabezpečení
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Zabezpečení zahrnuje tři vzájemně komunikující části: sandboxing, oprávnění a vynucení. Sandboxing odkazuje na způsob vytváření izolované domény, kde některé kód považován za plně důvěryhodný a jiný kód je omezen na oprávnění v udělené sadě pro izolovaný prostor. Aplikační kód, který běží v rámci sady grant izolovaného prostoru se považuje za transparentní; To znamená ho nemůže provádět žádné operace, které můžou ovlivnit zabezpečení. Udělení nastavení pro izolovaný prostor je dáno důkaz (<xref:System.Security.Policy.Evidence> třídy). Důkaz identifikuje, jaké konkrétní oprávnění jsou vyžadována izolovaných prostorů a jaké druhy izolovaných prostorů nelze vytvořit. Vynucení odkazuje na umožnění transparentní kód provést pouze v rámci jeho udělené sady.  
  
> [!IMPORTANT]
>  Zásady zabezpečení je klíčovým prvkem v předchozích verzích rozhraní .NET Framework. Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zásady zabezpečení je zastaralý. Odstranění zásady zabezpečení je oddělené od transparentnosti zabezpečení. Informace o dopadech této změny naleznete v tématu [kompatibilitou zásad zabezpečení přístupu kódu a migrace](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md).  
  
 Toto téma popisuje model transparentnosti podrobněji. Obsahuje následující oddíly:  
  
-   [Účel modelu transparentnosti](#purpose)  
  
-   [Určení úroveň průhlednosti](#level)  
  
-   [Vynucení transparentnosti](#enforcement)  
  
<a name="purpose"></a>   
## <a name="purpose-of-the-transparency-model"></a>Účel modelu transparentnosti  
 Průhlednost je mechanismus vynucení, který odděluje kód, který spouští jako součást aplikace z kódu, který běží v rámci infrastruktury. Průhlednost nakreslí bariéry mezi kód, který může provádět privilegované akce (kritický kód), jako například volání nativního kódu a kód, který nemůže (transparentní kód). Kód transparentní pro můžete spuštěním příkazů v rámci hranice sadu oprávnění, které funguje, ale nelze provést, jsou odvozeny od nebo obsahovat kód kritický pro.  
  
 Primární cílem vynucení transparentnosti je poskytnout jednoduchý a efektivní mechanismus pro izolaci různých skupin kódu založený na oprávnění. V rámci modelu sandboxing, jsou tyto skupiny oprávnění buď plně důvěryhodné (to znamená, nejsou omezeny) nebo částečně důvěryhodné (který je omezeno na sadou oprávnění udělenou k izolovanému prostoru).  
  
> [!IMPORTANT]
>  Model transparentnosti přesahuje zabezpečení přístupu kódu. Průhlednost je vyžadována kompilátorem za běhu a zůstává v platnosti bez ohledu na to grant sadu pro sestavení, včetně úplný vztah důvěryhodnosti.  
  
 Průhlednost byla zavedena v rozhraní .NET Framework verze 2.0 pro zjednodušení modelu zabezpečení a usnadňují psaní a nasazení zabezpečených knihoven a aplikací. Kód transparentní pro se také používá Microsoft Silverlight, zjednodušit vývoj částečně důvěryhodné aplikace.  
  
> [!NOTE]
>  Při vývoji částečně důvěryhodné aplikace, budete muset znát požadavky na oprávnění pro cílového hostitele. Můžete vyvíjet aplikace, která používá prostředky, které nejsou povoleny některé hostitele. Tato aplikace bude kompilovat bez chyby, ale selže, když je načten do hostovaného prostředí. Pokud jste si vytvořili aplikaci pomocí sady Visual Studio, můžete povolit ladění v částečné důvěryhodnosti nebo s omezenými oprávněními nastavit z vývojového prostředí. Další informace najdete v tématu [postupy: ladění aplikace ClickOnce s omezenými oprávněními](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). Tato funkce Vypočítat oprávnění zadaný pro aplikace ClickOnce je také k dispozici pro všechny částečně důvěryhodné aplikace.  
  
 [Zpět na začátek](#top)  
  
<a name="level"></a>   
## <a name="specifying-the-transparency-level"></a>Určení úroveň průhlednosti  
 Úroveň sestavení <xref:System.Security.SecurityRulesAttribute> atribut explicitně vybere <xref:System.Security.SecurityRuleSet> pravidla, která bude sestavení dodržovat. Pravidla jsou uspořádány podle číselné úrovně systému, kde vyšší úrovně znamenají náročnější vynucení pravidla zabezpečení.  
  
 Úrovně jsou následující:  
  
-   Úroveň 2 (<xref:System.Security.SecurityRuleSet.Level2>) – [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] průhlednost pravidla.  
  
-   Úroveň 1 (<xref:System.Security.SecurityRuleSet.Level1>) – pravidla transparentnosti rozhraní .NET Framework 2.0.  
  
 Hlavní rozdíl mezi dvěma průhlednost úrovně je, že úroveň 1 nevynucuje průhlednost pravidla pro volání z mimo sestavení a je určena pouze pro kompatibilitu.  
  
> [!IMPORTANT]
>  Musíte zadat průhlednost úrovně 1 pouze pro kompatibilitu; To znamená, zadejte úroveň 1 pouze pro kód, který byla vyvinuta v rozhraní .NET Framework 3.5 nebo starším, který používá <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut, nebo nepoužívá model průhlednost. Průhlednost úrovně 1 můžete například použijte pro sestavení rozhraní .NET Framework 2.0, které umožňují volání z částečně důvěryhodné volající (APTCA). Pro kód, který je vyvinutý pro [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vždy použijte průhlednost úrovně 2.  
  
### <a name="level-2-transparency"></a>Průhlednost úrovně 2  
 Průhlednost úrovně 2 byla zavedena v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Tři zásady tohoto modelu jsou transparentní kód, bezpečné a kritické pro zabezpečení kód a kód kritický pro zabezpečení.  
  
-   Transparentní kód, bez ohledu na oprávnění udělená (včetně úplný vztah důvěryhodnosti), můžete volat jenom jiné transparentní kód nebo kód bezpečné a kritické pro zabezpečení. Pokud je částečně důvěryhodný kód, může provádět jenom akce, které jsou povoleny sadě oprávnění domény. Kód transparentní nelze provést následující akce:  
  
    -   Provést <xref:System.Security.CodeAccessPermission.Assert%2A> operace nebo zvýšení oprávnění.  
  
    -   Obsahovat nebezpečný nebo neověřitelný kód.  
  
    -   Kód kritický pro volejte přímo.  
  
    -   Nativní kód nebo kód, který se má volat <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atribut.  
  
    -   Volání člena, který je chráněn <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Typy kritické dědí.  
  
     Kromě toho transparentní metody nelze přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.  
  
-   Bezpečné a kritické pro zabezpečení kód je plně důvěryhodný, ale je volatelné transparentní kód. Zpřístupňuje omezenou oblast povrchu kódu plné důvěryhodnosti. Dojde k ověření správnosti a zabezpečení v kritickém kódu.  
  
-   Kód kritický pro zabezpečení můžete volat žádný kód a je plně důvěryhodný, ale ji nelze volat kód transparentní.  
  
### <a name="level-1-transparency"></a>Průhlednost úrovně 1  
 Model průhlednost úrovně 1 byla zavedena v rozhraní .NET Framework verze 2.0 a umožňuje vývojářům ke snížení objemu kódu, který je předmětem zabezpečení auditu. I když průhlednost úrovně 1 byla veřejně dostupné ve verzi 2.0, byla primárně používána pouze v rámci společnosti Microsoft pro účely auditování zabezpečení. Vývojáři dokážou deklarovat typy, které prostřednictvím poznámky, mohou provést členové – zvýšení úrovní oprávnění zabezpečení a další důvěryhodné akce (kritický pro zabezpečení) a který nelze (transparentní pro zabezpečení). Kód, který je identifikován jako transparentní nevyžaduje vysoký stupeň auditování zabezpečení. Průhlednost úrovně 1 stavy vynucení transparentnosti je omezený na v rámci sestavení. Jinými slovy všechny veřejné typy nebo členy, které jsou označeny jako kritické pro zabezpečení jsou kritické pro zabezpečení pouze v rámci sestavení. Pokud chcete vynutit zabezpečení pro tyto typy a členy, když jsou volány z mimo sestavení, musíte použít požadavky propojení pro úplný vztah důvěryhodnosti. Pokud ho použít nechcete, veřejně viditelné typy kritické pro zabezpečení a členové jsou zpracovány jako bezpečné a kritické pro zabezpečení a mohou být volány částečně důvěryhodným kódem mimo sestavení.  
  
 Model průhlednost úrovně 1 má následující omezení:  
  
-   Typy kritické pro zabezpečení a členy, kteří jsou veřejné jsou přístupné z kód transparentní pro zabezpečení.  
  
-   Poznámky transparentnosti se vynucují jenom v rámci sestavení.  
  
-   Typy kritické pro zabezpečení a členy musí používat požadavky propojení vynutit zabezpečení pro volání z mimo sestavení.  
  
-   Pravidla dědičnosti nejsou vynucená.  
  
-   Potenciálně existuje pro transparentní kód udělat škodlivé akce při spuštění v režimu plné důvěryhodnosti.  
  
 [Zpět na začátek](#top)  
  
<a name="enforcement"></a>   
## <a name="transparency-enforcement"></a>Vynucení transparentnosti  
 Pravidla transparentnosti nejsou vynucená, dokud se počítá průhlednost. V ten moment se <xref:System.InvalidOperationException> je vyvolána, pokud je pravidlo transparentnosti porušeno. Čas, který se počítá průhlednost závisí na několika faktorech a nelze ji předpovědět. Se počítá jako pozdní. V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], dříve, než v rozhraní .NET Framework 2.0 dojde k výpočtu transparentnosti úrovně sestavení. Pouze záruku je, že výpočtu transparentnosti dojde na době, kdy je to nezbytné. Toto je podobná jak kompilátoru za běhu (JIT) můžete změnit bod při kompilaci metoda a zjištění všechny chyby v této metodě. Výpočet průhlednost je neviditelná, pokud kód nemá žádné chyby průhlednost.  
  
## <a name="see-also"></a>Viz také  
 [Kód transparentní pro zabezpečení, úroveň 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
