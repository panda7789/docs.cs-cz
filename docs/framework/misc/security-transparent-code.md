---
title: Kód transparentní pro zabezpečení
description: Pochopení účelu transparentního modelu kódu, určení úrovně transparentnosti a vynucení transparentnosti v zabezpečení.
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
ms.openlocfilehash: a167efe12b88f796fba4abc6d60ebffe4693709a
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309843"
---
# <a name="security-transparent-code"></a>Kód transparentní pro zabezpečení

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Zabezpečení zahrnuje tři vzájemně komunikující součásti: sandboxing, oprávnění a vynucování. Sandboxing odkazuje na postupy vytváření izolovaných domén, kde určitý kód je považován za plně důvěryhodný a jiný kód je omezen na oprávnění v sadě udělení pro izolovaný prostor (sandbox). Kód aplikace, který běží v sadě udělení izolovaného prostoru (sandbox), je považován za transparentní; To znamená, že nemůže provádět žádné operace, které mohou ovlivnit zabezpečení. Sada udělení pro izolovaný prostor (sandbox) je určena legitimací ( <xref:System.Security.Policy.Evidence> třída). Legitimace určuje, jaká konkrétní oprávnění jsou požadována v izolovaném prostoru a jaké druhy izolovaných prostorů lze vytvořit. Vynucení označuje, že transparentní kód se dá provádět jenom v rámci své sady udělení.

> [!IMPORTANT]
> Zásady zabezpečení byly klíčovým prvkem v předchozích verzích .NET Framework. Počínaje .NET Framework 4 je zásada zabezpečení zastaralá. Odstranění zásad zabezpečení je nezávislé na transparentnosti zabezpečení. Informace o účincích této změny najdete v tématu [Kompatibilita a migrace zásad zabezpečení přístupu kódu](code-access-security-policy-compatibility-and-migration.md).

## <a name="purpose-of-the-transparency-model"></a>Účel modelu transparentnosti

Transparentnost je mechanismus vynucení, který odděluje kód spouštěný jako součást aplikace z kódu, který se spouští jako součást infrastruktury. Transparentnost kreslí bariéru mezi kódem, který může dělat privilegované věci (kritický kód), jako je například volání nativního kódu, a kód, který nemůže (transparentní kód). Transparentní kód může spouštět příkazy v mezích sady oprávnění, na které pracuje, ale nemůže provádět, odvozovat nebo obsahovat kritický kód.

Hlavním cílem vynucení transparentnosti je poskytnutí jednoduchého a efektivního mechanismu pro izolaci různých skupin kódu na základě oprávnění. V rámci kontextu modelu izolovaného prostoru jsou tyto skupiny oprávnění buď plně důvěryhodné (tj. bez omezení) nebo částečně důvěryhodné (tj. omezeny na sadu oprávnění udělenou izolovanému prostoru).

> [!IMPORTANT]
> Model transparentnosti transcends zabezpečení přístupu kódu. Transparentnost je vynutila kompilátorem za běhu a zůstává v platnosti bez ohledu na udělenou sadu pro sestavení, včetně úplného vztahu důvěryhodnosti.

Transparentnost byla představena ve verzi .NET Framework 2,0, která zjednodušuje model zabezpečení a usnadňuje psaní a nasazování zabezpečených knihoven a aplikací. Transparentní kód se používá také v programu Microsoft Silverlight pro zjednodušení vývoje částečně důvěryhodných aplikací.

> [!NOTE]
> Při vývoji částečně důvěryhodné aplikace musíte mít na paměti požadavky na oprávnění pro vaše cílové hostitele. Můžete vyvíjet aplikace, které používají prostředky, které nejsou povoleny některými hostiteli. Tato aplikace bude zkompilována bez chyby, ale při jejím načtení do hostovaného prostředí se nezdaří. Pokud jste aplikaci vyvinuli pomocí sady Visual Studio, můžete povolit ladění v částečném vztahu důvěryhodnosti nebo v sadě s omezeným oprávněním z vývojového prostředí. Další informace naleznete v tématu [How to: Debug a aplikace ClickOnce s omezenými oprávněními](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). Funkce Vypočti oprávnění poskytovaná pro aplikace ClickOnce je dostupná také pro všechny částečně důvěryhodné aplikace.

## <a name="specifying-the-transparency-level"></a>Určení úrovně transparentnosti

Atribut na úrovni sestavení <xref:System.Security.SecurityRulesAttribute> explicitně vybere <xref:System.Security.SecurityRuleSet> pravidla, která bude pokračovat v sestavení. Pravidla jsou uspořádaná v rámci systému číselné úrovně, kde vyšší úrovně znamenají užší vynucování pravidel zabezpečení.

Úrovně jsou následující:

- Level 2 ( <xref:System.Security.SecurityRuleSet.Level2> ) – pravidla transparentnosti .NET Framework 4.

- Úroveň 1 ( <xref:System.Security.SecurityRuleSet.Level1> ) – pravidla transparentnosti .NET Framework 2,0.

Hlavním rozdílem mezi těmito dvěma úrovněmi transparentnosti je, že úroveň 1 neuplatňuje pravidla transparentnosti pro volání mimo sestavení a je určena pouze pro zajištění kompatibility.

> [!IMPORTANT]
> Měli byste zadat transparentnost první úrovně pouze pro kompatibilitu; To znamená, že zadáte úroveň 1 pouze pro kód, který byl vyvinut s .NET Framework 3,5 nebo starším, který používá <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut nebo nepoužívá model transparentnosti. Například použijte transparentnost první úrovně pro sestavení .NET Framework 2,0, která umožňují volání z částečně důvěryhodných volajících (APTCA). Pro kód vyvinutý pro .NET Framework 4 vždy použijte transparentnost úrovně 2.

### <a name="level-2-transparency"></a>Transparentnost úrovně 2

Transparentnost úrovně 2 byla představena v .NET Framework 4. Tři principy tohoto modelu jsou transparentní kód, bezpečný a kritický kód pro zabezpečení a kód kritický pro zabezpečení.

- Transparentní kód, bez ohledu na oprávnění udělená (včetně úplné důvěryhodnosti), může volat pouze jiný transparentní kód nebo bezpečný a kritický kód pro zabezpečení. Pokud je kód částečně důvěryhodný, může provádět pouze akce, které jsou povoleny sadou oprávnění domény. Transparentní kód nemůže provádět následující:

  - Provedení <xref:System.Security.CodeAccessPermission.Assert%2A> operace nebo zvýšení oprávnění.

  - Obsahuje nezabezpečený nebo neověřitelný kód.

  - Přímo zavolejte kritický kód.

  - Zavolejte nativní kód nebo kód, který má <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atribut.

  - Zavolejte člen, který je chráněn pomocí <xref:System.Security.Permissions.SecurityAction.LinkDemand> .

  - Dědí z kritických typů.

    Transparentní metody navíc nemohou přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.

- Bezpečný a kritický kód pro zabezpečení je plně důvěryhodný, ale je vydaný transparentním kódem. Zpřístupňuje omezený plošný prostor s plně důvěryhodným kódem. K ověření správnosti a zabezpečení dochází v kódu bezpečného kritického.

- Kód kritický pro zabezpečení může volat jakýkoli kód a je plně důvěryhodný, ale nemůže být volán transparentním kódem.

### <a name="level-1-transparency"></a>Transparentnost první úrovně

Model transparentnosti úrovně 1 byl představen v .NET Framework verze 2,0, který vývojářům umožňuje snížit množství kódu podléhajícího auditu zabezpečení. Přestože transparentnost první úrovně byla veřejně k dispozici ve verzi 2,0, byla primárně používána pouze v rámci společnosti Microsoft pro účely auditování zabezpečení. Prostřednictvím poznámek mohou vývojáři deklarovat, které typy a členové mohou provádět zvýšení úrovně zabezpečení a jiné důvěryhodné akce (kritické pro zabezpečení) a které nemohou (zabezpečení transparentní). Kód, který je identifikován jako transparentní, nevyžaduje vysoký stupeň auditování zabezpečení. 1. úroveň transparentnosti je, že vynucení transparentnosti je omezeno na v rámci sestavení. Jinými slovy, všechny veřejné typy nebo členy, které jsou identifikovány jako kritické pro zabezpečení, jsou kritické pro zabezpečení pouze v rámci sestavení. Pokud chcete vyhodnotit zabezpečení pro tyto typy a členy, když jsou volány mimo sestavení, je nutné použít požadavky propojení pro úplný vztah důvěryhodnosti. Pokud to neuděláte, veřejně viditelné typy kritické pro zabezpečení a členy jsou považovány za kritické a bezpečné pro zabezpečení a mohou být volány částečně důvěryhodným kódem mimo sestavení.

Model transparentnosti úrovně 1 má následující omezení:

- Typy kritické pro zabezpečení a členy, které jsou veřejné, jsou přístupné z kódu transparentního pro zabezpečení.

- Anotace transparentnosti jsou vynutily pouze v rámci sestavení.

- Typy a členy kritické pro zabezpečení musí použít požadavky propojení k vymáhání zabezpečení pro volání mimo sestavení.

- Pravidla dědičnosti nejsou vynutila.

- Potenciál existuje pro transparentní kód, který umožňuje škodlivé věci při spuštění v úplném vztahu důvěryhodnosti.

## <a name="transparency-enforcement"></a>Vynucování transparentnosti

Pravidla transparentnosti se nevynutily, dokud se nevypočítá průhlednost. V tomto okamžiku <xref:System.InvalidOperationException> je vyvolána výjimka, pokud je porušeno pravidlo transparentnosti. Čas, kdy je transparentnost počítána, závisí na několika faktorech a nelze je předpovědět. Počítá se co nejblíže. V .NET Framework 4 proběhne výpočet transparentnosti na úrovni sestavení dřív než v .NET Framework 2,0. Jedinou jistotou je, že k výpočtu transparentnosti dojde v době, kdy je to potřeba. To se podobá tomu, jak kompilátor JIT (just-in-time) může změnit bod, když je metoda zkompilována, a zda jsou zjištěny chyby v této metodě. Výpočet transparentnosti není viditelný, pokud váš kód neobsahuje žádné chyby transparentnosti.

## <a name="see-also"></a>Viz také

- [Kód transparentní pro zabezpečení, úroveň 1](security-transparent-code-level-1.md)
- [Transparentní kód pro zabezpečení, úroveň 2](security-transparent-code-level-2.md)
