---
title: Kód transparentní pro zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc39e4ee47041e70060465a7e220ae1d861d9053
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510114"
---
# <a name="security-transparent-code"></a>Kód transparentní pro zabezpečení
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Zabezpečení zahrnuje tři vzájemně komunikující části: izolaci prostoru, oprávnění a prosazování. Sandboxing odkazuje na praxi vytváření izolovaných domén, kde nějaký kód považován za plně důvěryhodný a jiný kód je omezen oprávněními v sadě oprávnění pro izolovaný prostor. Kód aplikace, který běží v rámci udělené sady izolovaného prostoru je považován za transparentní; To znamená že nemůže provádět žádné operace, které můžou ovlivnit zabezpečení. Udělená sada pro izolovaný prostor je určena legitimací (<xref:System.Security.Policy.Evidence> třídy). Legitimace identifikuje, jaká konkrétní oprávnění jsou vyžadována izolovanými prostory a jaké druhy izolovaných prostorů mohou být vytvořeny. Vynucení odkazuje na umožnění transparentnímu kódu vykonávat pouze v rámci jeho udělené sady.  
  
> [!IMPORTANT]
>  Zásady zabezpečení byly klíčovým elementem v předchozích verzích rozhraní .NET Framework. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zásady zabezpečení je zastaralé. Odstranění zásad zabezpečení je oddělené od transparentnosti zabezpečení. Informace o účincích této změny najdete v tématu [kompatibilitou zásad zabezpečení přístupu kódu a migrace](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md).  
  
 Toto téma popisuje model transparentnosti podrobněji. Obsahuje následující oddíly:  
  
-   [Účel modelu transparentnosti](#purpose)  
  
-   [Specifikování úrovně transparentnosti](#level)  
  
-   [Vynucení transparentnosti](#enforcement)  
  
<a name="purpose"></a>   
## <a name="purpose-of-the-transparency-model"></a>Účel modelu transparentnosti  
 Transparentnost je mechanismus vynucování, který odděluje kód, který spouští jako součást aplikace od kódu, který běží jako část infrastruktury. Transparentnost kreslí bariéru mezi kódem, který může dělat privilegované věci (kritický kód), jako je například volání nativního kódu a kód, který nemůže (transparentní kód). Transparentní kód můžete provádět příkazy v rámci hranice sady oprávnění, které funguje, ale nelze spustit, odvozovat nebo obsahovat kritický kód.  
  
 Primární cíl vynucování transparentnosti je poskytnout jednoduchý a účinný mechanismus pro izolaci různých skupin kódu založený na oprávnění. V rámci kontextu modelu izolace (sandbox), jsou tyto skupiny oprávnění buď plně důvěryhodné (to znamená, nejsou omezeny) nebo částečně důvěryhodné (tedy omezeny sadou oprávnění udělenou izolovanému prostoru).  
  
> [!IMPORTANT]
>  Model transparentnosti přesahuje zabezpečení přístupu kódu. Transparentnost je vynucena kompilátorem za běhu a zůstává v platnosti bez ohledu na udělenou sadu pro sestavení, včetně úplné důvěryhodnosti.  
  
 Transparentnost byla představena v rozhraní .NET Framework verze 2.0 zjednodušila model zabezpečení a usnadňují zápis a nasazovat zabezpečené knihovny a aplikace. Transparentní kód se také používá v Microsoft Silverlight pro zjednodušení vývoje částečně důvěryhodné aplikace.  
  
> [!NOTE]
>  Když vyvíjíte částečně důvěryhodnou aplikaci, budete muset znát požadavky oprávnění na vaše cílové hostitele. Můžete vyvíjet aplikace, která využívá prostředky, které nejsou povoleny některými hostiteli. Tato aplikace bude zkompilována bez chyby, ale selže, když je načten do hostovaného prostředí. Pokud jste vytvořili aplikaci pomocí sady Visual Studio, můžete povolit ladění v částečném vztahu důvěryhodnosti nebo v omezené sadě z vývojového prostředí oprávnění. Další informace najdete v tématu [jak: Ladění aplikace ClickOnce s omezenými oprávněními](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). Vlastnost Calculate Permissions poskytnutá k aplikaci ClickOnce je také k dispozici pro libovolnou částečně důvěryhodnou aplikaci.  
  
 [Zpět na začátek](#top)  
  
<a name="level"></a>   
## <a name="specifying-the-transparency-level"></a>Specifikování úrovně transparentnosti  
 Úrovni sestavení <xref:System.Security.SecurityRulesAttribute> atribut explicitně vybere <xref:System.Security.SecurityRuleSet> pravidla, která bude sestavení dodržovat. Pravidla jsou uspořádána podle číselné úrovně systému, kde vyšší úrovně znamenají těsnější prosazování pravidel zabezpečení.  
  
 Tyto úrovně jsou následující:  
  
-   Úroveň 2 (<xref:System.Security.SecurityRuleSet.Level2>) – [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pravidla transparentnosti.  
  
-   Úroveň 1 (<xref:System.Security.SecurityRuleSet.Level1>) – pravidla transparentnosti rozhraní .NET Framework 2.0.  
  
 Hlavní rozdíl mezi těmito dvěma úrovněmi transparentnosti je, že 1 úroveň nevynucuje pravidla transparentnosti pro volání pocházející mimo sestavení a je určena pouze pro kompatibilitu.  
  
> [!IMPORTANT]
>  Je třeba zadat transparentnosti úrovně 1 pouze pro kompatibilitu; To znamená, specifikovat úroveň 1 pouze pro kód, který byl vyvinut v rozhraní .NET Framework 3.5 nebo starším, který používá <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut nebo nepoužívá model transparentnosti. Například použijte transparentnosti úrovně 1 pro sestavení rozhraní .NET Framework 2.0, které umožňují volání od částečně důvěryhodných volajících (APTCA). Pro kód, který je vyvinutý pro [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vždy použijte transparentnost druhé úrovně 2.  
  
### <a name="level-2-transparency"></a>Průhlednost úrovně 2  
 Průhlednost úrovně 2 byla zavedena v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Tři zásady tohoto modelu jsou transparentní kód, bezpečný a kritický pro zabezpečení kód a kód kritický pro zabezpečení.  
  
-   Transparentní kód, bez ohledu na oprávnění, která má oprávnění (včetně úplné důvěryhodnosti), může volat pouze jiný transparentní kód nebo bezpečný a kritický pro zabezpečení kódu. Pokud je kód částečně důvěryhodný, může pouze provádět akce, které jsou povolené sadou oprávnění domény. Transparentní kód nemůže provádět následující:  
  
    -   Provést <xref:System.Security.CodeAccessPermission.Assert%2A> operace nebo zvýšení oprávnění.  
  
    -   Obsahovat nebezpečný nebo neověřitelný kód.  
  
    -   Přímo volejte kritický kód.  
  
    -   Volat nativní kód nebo kód, který má <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atribut.  
  
    -   Volat člen, který je chráněn <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Dědit z kritických typů.  
  
     Kromě toho transparentní metody nelze přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.  
  
-   Bezpečné a kritické pro zabezpečení kódu je plně důvěryhodný, ale je volatelný transparentním kódem. Zpřístupňuje omezenou oblast povrchu plně důvěryhodného kódu. Ověření správnosti a zabezpečení dojde v bezpečný a kritický kód.  
  
-   Kód kritický pro zabezpečení může volat libovolný kód a je plně důvěryhodný, ale nemůže být volán transparentním kódem.  
  
### <a name="level-1-transparency"></a>Transparentnosti úrovně 1  
 Modelu transparentnosti úrovně 1 byla zavedena v rozhraní .NET Framework verze 2.0 a umožňuje vývojářům snížit objem kódu, který podléhá auditu zabezpečení. I když transparentnosti úrovně 1 byla veřejně k dispozici ve verzi 2.0, byla primárně používána pouze v rámci společnosti Microsoft pro účely auditování zabezpečení. Prostřednictvím anotací jsou vývojáři schopni deklarovat, které typy a členy mohou zvyšovat zabezpečení a jiné důvěryhodné akce (bezpečnostně kritické) provádět a které nemohou (bezpečnostně transparentní). Kód, který je identifikován jako transparentní, nevyžaduje vysoký stupeň auditování zabezpečení. Transparentnosti úrovně 1 uvádí, že vynucení transparentnosti je omezeno v rámci sestavení. Jinými slovy jakékoliv veřejné typy nebo členy, které jsou identifikovány jako kritické pro zabezpečení jsou kritické pro zabezpečení pouze v rámci sestavení. Pokud chcete vynutit zabezpečení pro tyto typy a členy, když jsou volaní mimo sestavení, musíte použít požadavky propojení pro úplný vztah důvěryhodnosti. Pokud tak neučiníte, veřejně viditelné typy kritické pro zabezpečení a členy jsou zpracovány jako bezpečné a kritické pro zabezpečení a mohou být volány částečně důvěryhodným kódem mimo sestavení.  
  
 Modelu transparentnosti úrovně 1 má následující omezení:  
  
-   Typy kritické pro zabezpečení a členy, které jsou veřejné, jsou přístupné z kódu transparentního pro zabezpečení.  
  
-   Anotace transparentnosti jsou vynuceny pouze v rámci sestavení.  
  
-   Typy a členy kritické pro zabezpečení musí používat požadavky propojení k vynucení zabezpečení pro volání pocházející mimo sestavení.  
  
-   Pravidla dědičnosti nejsou vynucena.  
  
-   Potenciál existuje pro transparentní kód, aby prováděl škodlivé akce při spuštění v režimu plné důvěryhodnosti.  
  
 [Zpět na začátek](#top)  
  
<a name="enforcement"></a>   
## <a name="transparency-enforcement"></a>Vynucení transparentnosti  
 Pravidla transparentnosti nejsou vynucena, dokud se transparentnost nevypočítá. V tu chvíli <xref:System.InvalidOperationException> je vyvolána, pokud je pravidlo transparentnosti porušeno. Čas, který je transparentnost vypočítána, závisí na několika faktorech a nemůže být předpovězen. Je vypočten tak pozdě nejvíce. V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], dříve, než v rozhraní .NET Framework 2.0 dojde k výpočtu transparentnosti úrovně sestavení. Jediná záruka je, že výpočtu transparentnosti dojde v době, kdy je to potřeba. To se podobá jak kompilátor just-in-time (JIT) může měnit bod, když je metoda kompilována a zjištěny nějaké chyby v této metodě. Výpočet transparentnosti je neviditelný, pokud váš kód nemá nějaké chyby transparentnosti.  
  
## <a name="see-also"></a>Viz také:
- [Kód transparentní pro zabezpečení, úroveň 1](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
