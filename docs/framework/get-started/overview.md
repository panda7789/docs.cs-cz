---
title: Přehled rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
ms.openlocfilehash: de9cbdab5d5786b9d59d23ba675fa3f78f807716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181597"
---
# <a name="overview-of-net-framework"></a>Přehled rozhraní .NET Framework

Rozhraní .NET Framework je technologie, která podporuje vytváření a spouštění aplikací pro Windows a webových služeb. Rozhraní .NET Framework je navrženo tak, aby splňovalo následující cíle:

- Chcete-li poskytnout konzistentní objektově orientované programovací prostředí, zda je objektový kód uložen a spuštěn místně, spuštěn místně, ale webový distribuovaný nebo spuštěn vzdáleně.

- Chcete-li poskytnout prostředí pro spuštění kódu, které minimalizuje konflikty nasazení softwaru a správy verzí.

- Chcete-li poskytnout prostředí pro spuštění kódu, které podporuje bezpečné spuštění kódu, včetně kódu vytvořeného neznámou nebo částečně důvěryhodnou třetí stranou.

- Chcete-li poskytnout prostředí spuštění kódu, které eliminuje problémy s výkonem skriptovaných nebo interpretovaných prostředí.

- Aby bylo vývojářské prostředí konzistentní napříč velmi odlišnými typy aplikací, jako jsou aplikace pro Windows a webové aplikace.

- Chcete-li vytvořit veškerou komunikaci na oborové standardy, aby bylo zajištěno, že kód založený na rozhraní .NET Framework integruje s jiným kódem.

> [!NOTE]
> Obecný úvod do rozhraní .NET Framework pro uživatele i vývojáře naleznete v [tématu Začínáme](index.md).

Rozhraní .NET Framework se skládá z běžného jazyka runtime (CLR) a knihovny tříd rozhraní .NET Framework. Běžný jazyk runtime je základem rozhraní .NET Framework. Představte si runtime jako agenta, který spravuje kód v době spuštění, poskytuje základní služby, jako je správa paměti, správa vláken a vzdálená komunikace, a zároveň vynucuje přísnou bezpečnost typů a další formy přesnosti kódu, které podporují zabezpečení a robustnost. Ve skutečnosti je koncept správy kódu základním principem běhu. Kód, který cílí na runtime, se označuje jako spravovaný kód, zatímco kód, který necílí na runtime, se označuje jako nespravovaný kód. Knihovna tříd je komplexní, objektově orientovaná kolekce opakovaně použitelných typů, které používáte k vývoji aplikací od tradičních aplikací příkazového řádku nebo grafického uživatelského rozhraní (GUI) až po aplikace založené na nejnovějších inovacích poskytovaných ASP.NET, jako je web Formuláře a webové služby XML.

Rozhraní .NET Framework může být hostováno nespravovanými součástmi, které načítají do procesů zaběhu společného jazyka a iniciují provádění spravovaného kódu, čímž vytvářejí softwarové prostředí, které využívá spravované i nespravované funkce. Rozhraní .NET Framework poskytuje nejen několik hostitelů runtime, ale také podporuje vývoj hostitelů za běhu třetích stran.

Například ASP.NET hostuje za běhu, aby poskytoval škálovatelné prostředí na straně serveru pro spravovaný kód. ASP.NET pracuje přímo s runtime povolit ASP.NET aplikace a webové služby XML, které jsou popsány dále v tomto článku.

Internet Explorer je příkladem nespravované aplikace, která hostuje runtime (ve formě rozšíření typu MIME). Použití aplikace Internet Explorer k hostování modulu runtime umožňuje vložit spravované součásti nebo ovládací prvky windows forms do dokumentů HTML. Hostování runtime tímto způsobem umožňuje spravovaný mobilní kód, ale s významnými vylepšeními, která nabízí pouze spravovaný kód, jako je například částečně důvěryhodné spuštění a izolované úložiště souborů.

Následující obrázek znázorňuje vztah běžného zaběhu jazyka a knihovny tříd k vašim aplikacím a k celkovému systému. Obrázek také ukazuje, jak spravovaný kód funguje v rámci větší architektury.

![Snímek obrazovky, který ukazuje, jak spravovaný kód funguje v rámci větší architektury.](./media/overview/language-runtime-class-library-relationship.gif)

Následující části popisují hlavní funkce rozhraní .NET Framework podrobněji.

## <a name="features-of-the-common-language-runtime"></a>Funkce běžného jazykového běhu

Běžný jazyk runtime spravuje paměť, spuštění podprocesu, spuštění kódu, ověření bezpečnosti kódu, kompilace a další systémové služby. Tyto funkce jsou vlastní spravovanému kódu, který běží na běžném jazyku runtime.

Pokud jde o zabezpečení, spravované součásti jsou uděleny různé stupně důvěryhodnosti, v závislosti na řadě faktorů, které zahrnují jejich původ (například Internet, podnikové sítě nebo místní počítač). To znamená, že spravovaná komponenta může nebo nemusí být schopna provádět operace přístupu k souborům, operace přístupu k registru nebo jiné citlivé funkce, i když se používá ve stejné aktivní aplikaci.

Runtime také vynucuje robustnost kódu implementací přísné infrastruktury ověřování typu a kódu nazývané společný typový systém (CTS). CTS zajišťuje, že všechny spravované kód je self-describing. Různé kompilátory jazyka Microsoft a jiných výrobců generují spravovaný kód, který odpovídá CTS. To znamená, že spravovaný kód může využívat jiné spravované typy a instance, zatímco přísně vynucuje věrnost typů a bezpečnost typů.

Spravované prostředí běhu navíc eliminuje mnoho běžných problémů se softwarem. Například runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty, jejich uvolnění, když jsou již používány. Tato automatická správa paměti řeší dvě nejběžnější chyby aplikace, nevracení paměti a neplatné odkazy na paměť.

Doba runtime také zrychluje produktivitu vývojářů. Například programátoři zapisují aplikace ve svém zvoleném vývojovém jazyce, ale plně využívají runtime, knihovnu tříd a komponenty napsané v jiných jazycích jinými vývojáři. Může tak učinit každý dodavatel kompilátoru, který se rozhodne cílit na runtime. Kompilátory jazyka, které cílí na rozhraní .NET Framework, zpřístupňují funkce rozhraní .NET Framework existujícímu kódu napsanému v tomto jazyce, což značně zmírňuje proces migrace pro existující aplikace.

Zatímco runtime je určen pro software budoucnosti, podporuje také software dneška a včerejška. Interoperabilita mezi spravovanými a nespravovanými kódy umožňuje vývojářům nadále používat nezbytné součásti modelu COM a knihovny DLL.

Doba běhu je navržena tak, aby zvyšla výkon. Přestože běžný jazyk runtime poskytuje mnoho standardních runtime služeb, spravovaný kód není nikdy interpretován. Funkce s názvem kompilace just-in-time (JIT) umožňuje spuštění všech spravovaných kódů v nativním jazyce počítače systému, ve kterém je spuštěn. Mezitím správce paměti odebere možnosti fragmentované paměti a zvyšuje lokalitu paměti odkazu na další zvýšení výkonu.

Nakonec modul runtime může být hostován vysoce výkonnými aplikacemi na straně serveru, jako je například Microsoft SQL Server a Internetová informační služba (IIS). Tato infrastruktura umožňuje používat spravovaný kód k zápisu obchodní logiky a přitom si stále užívat vynikající výkon nejlepších podnikových serverů v oboru, které podporují hostování za běhu.

## <a name="net-framework-class-library"></a>.NET Framework – knihovna tříd

Knihovna tříd rozhraní .NET Framework je kolekce opakovaně použitelných typů, které jsou pevně integrovány s běžným jazykovým runtime. Knihovna tříd je objektově orientovaná a poskytuje typy, ze kterých vlastní spravovaný kód odvozuje funkce. To nejen umožňuje snadno používat typy rozhraní .NET Framework, ale také zkracuje čas spojený s učením se novým funkcím rozhraní .NET Framework. Kromě toho součásti třetích stran hladce integrovat s třídami v rozhraní .NET Framework.

Například třídy kolekce rozhraní .NET Framework implementují sadu rozhraní pro vývoj vlastních tříd kolekce. Vaše třídy kolekce se hladce prolnou s třídami v rozhraní .NET Framework.

Jak byste očekávali od knihovny tříd orientovaných na objekty, typy rozhraní .NET Framework umožňují provádět řadu běžných programovacích úloh, včetně úloh, jako je správa řetězců, shromažďování dat, připojení k databázi a přístup k souborům. Kromě těchto běžných úkolů obsahuje knihovna tříd typy, které podporují různé specializované scénáře vývoje. Pomocí rozhraní .NET Framework můžete vyvíjet následující typy aplikací a služeb:

- Konzolové aplikace. Viz [Aplikace konzoly ve vytváření .](../../standard/building-console-apps.md)

- Aplikace Gui pro Windows (Windows Forms). Viz [Windows Forms](../winforms/index.md).

- Aplikace Windows Presentation Foundation (WPF). Viz [Windows Presentation Foundation](../wpf/index.md).

- ASP.NET aplikací. Viz [Webové aplikace s ASP.NET](../develop-web-apps-with-aspnet.md).

- Služby systému Windows. Viz [úvod do aplikací služby Windows](../windows-services/introduction-to-windows-service-applications.md).

- Aplikace orientované na služby pomocí Windows Communication Foundation (WCF). Viz [Aplikace orientované na služby s WCF](../wcf/index.md).

- Aplikace s podporou pracovního postupu pomocí služby Windows Workflow Foundation (WF). Viz [Základ pracovního postupu windows](../windows-workflow-foundation/index.md).

Windows Forms třídy jsou komplexní sada opakovaně použitelných typů, které výrazně zjednodušují vývoj grafického uživatelského rozhraní systému Windows. Pokud píšete aplikaci ASP.NET webový formulář, můžete použít třídy Webových formulářů.

## <a name="see-also"></a>Viz také

- [Systémové požadavky](system-requirements.md)
- [Průvodce instalací](../install/index.md)
- [Průvodce vývojem](../development-guide.md)
- [Nástroje](../tools/index.md)
- [Ukázky a výukové programy rozhraní .NET](../../samples-and-tutorials/index.md)
- [Prohlížeč rozhraní .NET API](../../../api/index.md)
