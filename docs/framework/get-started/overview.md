---
title: Přehled rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7a3548cb0d7e841f32824eda52565e64279536e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052002"
---
# <a name="overview-of-the-net-framework"></a>Přehled rozhraní .NET Framework

.NET Framework je technologie, která podporuje sestavování a spouštění nové generace aplikací a webových služeb XML. .NET Framework je navržena tak, aby splňovala následující cíle:

- K poskytnutí konzistentního programovacího prostředí orientovaného na objekty bez ohledu na to, jestli je kód objektu uložený a spuštěný místně, spuštěný místně, ale prostřednictvím Internetu nebo vzdáleně prováděný.

- Aby bylo možné poskytovat prostředí pro spouštění kódu, které minimalizuje nasazení softwaru a konflikty verzí.

- Aby bylo možné poskytovat prostředí pro provádění kódu, které propaguje bezpečné spuštění kódu, včetně kódu vytvořeného neznámou nebo částečně důvěryhodnou třetí stranou.

- Pro zajištění prostředí pro provádění kódu, které eliminuje problémy s výkonem skriptovacích nebo interpretovaných prostředí.

- Aby bylo prostředí pro vývojáře konzistentní v nejrůznějších různých typech aplikací, jako jsou aplikace založené na Windows a webové aplikace.

- Chcete-li vytvořit veškerou komunikaci v oborových standardech a zajistit tak, že kód na základě .NET Framework bude integrován s jakýmkoli jiným kódem.

> [!NOTE]
> Obecný úvod k .NET Framework pro uživatele a vývojáře naleznete v tématu [Začínáme](index.md).

.NET Framework se skládá z modulu CLR (Common Language Runtime) a knihovny tříd .NET Framework. Modul CLR (Common Language Runtime) je základem .NET Framework. Představte si modul runtime jako agenta, který spravuje kód v době spuštění a poskytuje základní služby, jako je například Správa paměti, Správa vláken a Vzdálená komunikace, a zároveň vynucování striktního zabezpečení typu a dalších forem přesnosti kódu, které podporují zabezpečení a odolnost. Ve skutečnosti koncept správy kódu je základní princip modulu runtime. Kód, který cílí na modul runtime, je označován jako spravovaný kód, zatímco kód, který necílí na modul runtime, je označován jako nespravovaný kód. Knihovna tříd je komplexní, objektově orientované kolekce opakovaně použitelných typů, které slouží k vývoji aplikací od tradičních aplikací z příkazového řádku nebo grafického uživatelského rozhraní (GUI) do aplikací na základě nejnovějších inovací poskytovaných službou ASP.NET, jako je například web. Formuláře a webové služby XML.

.NET Framework mohou být hostovány nespravovanými komponentami, které načítají modul CLR (Common Language Runtime) do procesů a iniciují provádění spravovaného kódu, čímž se vytvoří softwarové prostředí, které zneužije spravované i nespravované funkce. .NET Framework neposkytuje pouze několik hostitelů modulu runtime, ale podporuje také vývoj hostitelů modulu runtime třetích stran.

Například ASP.NET hostuje modul runtime, aby poskytoval škálovatelné prostředí na straně serveru pro spravovaný kód. ASP.NET pracuje přímo s modulem runtime a povoluje ASP.NET aplikace a webové služby XML, které jsou popsány dále v tomto tématu.

Internet Explorer je příkladem nespravované aplikace, která je hostitelem modulu runtime (ve formě rozšíření typu MIME). Použití aplikace Internet Explorer k hostování modulu runtime umožňuje vkládat spravované součásti nebo ovládací prvky model Windows Forms v dokumentech HTML. Hostování modulu runtime tímto způsobem zpřístupňuje spravovaný mobilní kód, ale s významnými vylepšeními, které nabízí jenom spravované kód, jako je částečně důvěryhodné spuštění a izolované úložiště souborů.

Následující ilustrace znázorňuje vztah společného jazykového modulu runtime a knihovny tříd k vašim aplikacím a celkovému systému. Ilustrace také ukazuje, jak spravovaný kód funguje v rámci větší architektury.

![Snímek obrazovky, který ukazuje, jak spravovaný kód funguje v rámci větší architektury.](./media/overview/language-runtime-class-library-relationship.gif)

V následujících částech jsou podrobněji popsány hlavní funkce .NET Framework.

## <a name="features-of-the-common-language-runtime"></a>Funkce modulu CLR (Common Language Runtime)

Modul CLR (Common Language Runtime) spravuje paměť, provádění vlákna, provádění kódu, ověřování v zabezpečení kódu, kompilaci a další systémové služby. Tyto funkce jsou vnitřní pro spravovaný kód, který běží v modulu CLR (Common Language Runtime).

V souvislosti s zabezpečením jsou spravované komponenty přidávány různě stupni důvěryhodnosti v závislosti na řadě faktorů, které zahrnují jejich původ (například Internet, podniková síť nebo místní počítač). To znamená, že spravovaná součást může nebo nemusí být schopná provádět operace přístupu k souborům, operace přístupu k registru nebo jiné citlivé funkce, i když se používá ve stejné aktivní aplikaci.

Modul runtime také vynutil odolnost kódu implementací infrastruktury striktního typu a-Code-ověřování označované jako CTS (Common Type System). CTS zajišťuje, aby veškerý spravovaný kód byl samy popisující. Různé kompilátory jazyka Microsoft a třetích stran generují spravovaný kód, který odpovídá CTS. To znamená, že spravovaný kód může spotřebovávat jiné spravované typy a instance a přitom striktně vynucuje věrnost typu a bezpečnost typů.

Spravované prostředí modulu runtime navíc eliminuje mnoho běžných problémů se softwarem. Například modul runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty a uvolňuje je, když již nejsou používány. Tato automatická správa paměti řeší dvě nejběžnější chyby aplikací, nevracení paměti a neplatné odkazy na paměť.

Modul runtime také zrychluje produktivitu vývojářů. Například programátoři zapisují aplikace v jejich vývojovém jazyce, ale ještě plně využívají výhod modulu runtime, knihovny tříd a komponent napsaných v jiných jazycích jinými vývojáři. Každý dodavatel s kompilátorem, který se rozhodne cílit na modul runtime, může to provést. Kompilátory jazyka, které cílí na .NET Framework zpřístupňují funkce .NET Framework existujícímu kódu napsanému v daném jazyce, což výrazně zjednodušuje proces migrace pro stávající aplikace.

I když je modul runtime navržený pro software v budoucnu, podporuje také dnešní a včerejší software. Vzájemná funkční spolupráce mezi spravovaným a nespravovaným kódem umožňuje vývojářům pokračovat v používání nezbytných komponent modelu COM a knihoven DLL.

Modul runtime je navržený tak, aby zvýšil výkon. I když modul CLR (Common Language Runtime) poskytuje mnoho standardních služeb runtime, spravovaný kód není nikdy interpretován. Funkce označovaná jako JIT (just-in-time) umožňuje veškerému spravovanému kódu běžet v nativním strojovém jazyce systému, ve kterém je prováděna. Mezitím správce paměti odebírá možnosti fragmentované paměti a zvyšuje místní paměť – odkaz na další zvýšení výkonu.

Nakonec lze modul runtime hostovat pomocí vysoce výkonných aplikací na straně serveru, například Microsoft SQL Server a Internetová informační služba (IIS). Tato infrastruktura vám umožňuje používat spravovaný kód k psaní obchodní logiky a stále využívat vynikající výkon nejlepších podnikových serverů, které podporují hostování modulu runtime.

## <a name="net-framework-class-library"></a>.NET Framework – knihovna tříd

Knihovna tříd .NET Framework je kolekce opakovaně použitelných typů, které se úzce integrují s modulem CLR (Common Language Runtime). Knihovna tříd je objektově orientované a poskytuje typy, ze kterých vlastní spravovaný kód odvodí funkčnost. To nejen usnadňuje použití typů .NET Framework, ale také zkracuje čas spojený s učením nových funkcí .NET Framework. Kromě toho komponenty třetích stran integrují plynule s třídami v .NET Framework.

Třídy kolekce .NET Framework například implementují sadu rozhraní pro vývoj vlastních tříd kolekcí. Vaše kolekce tříd se hladce promísí se třídami v .NET Framework.

Vzhledem k tomu, že byste očekávali od objektově orientované knihovny tříd, .NET Framework typy umožňují provádět řadu běžných programovacích úloh, včetně úloh, jako je správa řetězců, shromažďování dat, připojení k databázi a přístup k souborům. Kromě těchto běžných úkolů zahrnuje knihovna tříd typy, které podporují různé specializované vývojové scénáře. .NET Framework můžete použít k vývoji následujících typů aplikací a služeb:

- Konzolové aplikace. Viz [Sestavování konzolových aplikací](../../standard/building-console-apps.md).

- Aplikace Windows GUI (model Windows Forms). Viz [model Windows Forms](../winforms/index.md).

- Aplikace Windows Presentation Foundation (WPF). Viz [Windows Presentation Foundation](../wpf/index.md).

- ASP.NET aplikace. Viz [webové aplikace s ASP.NET](../develop-web-apps-with-aspnet.md).

- Služby systému Windows. Viz [Úvod do aplikací služby systému Windows](../windows-services/introduction-to-windows-service-applications.md).

- Aplikace orientované na služby využívající Windows Communication Foundation (WCF). Přečtěte si téma [aplikace orientované na služby se službou WCF](../wcf/index.md).

- Aplikace podporující pracovní postupy používající programovací model Windows Workflow Foundation (WF). Viz [programovací model Windows Workflow Foundation](../windows-workflow-foundation/index.md).

Třídy model Windows Forms jsou komplexní sada opakovaně použitelných typů, které zjednodušují vývoj grafického uživatelského rozhraní systému Windows. Pokud napíšete aplikaci webového formuláře ASP.NET, můžete použít třídy webových formulářů.

## <a name="see-also"></a>Viz také:

- [Požadavky na systém](system-requirements.md)
- [Průvodce instalací](../install/index.md)
- [Průvodce vývojem](../development-guide.md)
- [Nástroje](../tools/index.md)
- [Ukázky a kurzy .NET](../../samples-and-tutorials/index.md)
- [Knihovna tříd .NET Framework](https://go.microsoft.com/fwlink/?LinkID=227195)
