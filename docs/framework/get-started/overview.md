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
ms.openlocfilehash: 7e1227cbf85e72570bcb08f7f13168392b7c7b60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592572"
---
# <a name="overview-of-the-net-framework"></a>Přehled rozhraní .NET Framework

Rozhraní .NET Framework je technologií podporující vytváření a spouštění aplikací a webových služeb XML nové generace. Rozhraní .NET Framework je určen ke splnění následujících cílů:

- Poskytnout konzistentní objektově orientované programovací prostředí, kde je kód objektu uložen a spuštěn lokálně, spuštěn lokálně ale distribuován Internetu, nebo spuštěn vzdáleně.

- Poskytnout prostředí pro provádění kódu, které minimalizuje konflikty nasazení a správy verzí softwaru.

- Poskytnout prostředí pro zpracování kódu, který propaguje bezpečné zpracování kódu včetně kódu vytvoří neznámou nebo částečně důvěryhodnou třetí stranou.

- Spuštění kódu prostředí, které eliminuje výkonostní problémy skripty nebo interpretovaných prostředí.

- Chcete-li činit vývojářské zkušenosti konzistentní napříč nejrůznějšími typy aplikací, jako jsou aplikace založené na Windows a webová aplikace.

- Vytvářet veškerou komunikaci na průmyslových standardech, ujistěte se, že kód založený na rozhraní .NET Framework se integruje s jakýmkoliv jiným kódem.

> [!NOTE]
> Obecný úvod k rozhraní .NET Framework pro uživatele a vývojáře naleznete v tématu [Začínáme](../../../docs/framework/get-started/index.md).

Rozhraní .NET Framework se skládá z common language runtime (CLR) a knihovně tříd rozhraní .NET Framework. Modul common language runtime je základem rozhraní .NET Framework. Modul runtime můžete představit jako agenta, který spravuje kód v době provádění, poskytuje základní služby, jako je například správa paměti, správa vláken a vzdálené komunikace, současně také zajišťuje přísnou bezpečnost typů a další formy přesnosti kódu, které podporují zabezpečení a robustnost. Ve skutečnosti koncept správy kódu je základní princip modulu runtime. Kód, cílů modulu runtime je znám jako spravovaný kód, zatímco kód, který není zaměřují na modul runtime je znám jako nespravovaný kód. Knihovna tříd je komplexní, objektově orientovaná kolekce opakovaně použitelných typů, které používáte pro vývoj aplikací od tradiční příkazového řádku nebo grafické uživatelské rozhraní (GUI) aplikace až po aplikace založené na nejnovějších inovacích poskytovaných technologií ASP.NET, jako jsou webové Formuláře a webové služby XML.

Rozhraní .NET Framework může být hostováno nespravovanými komponentami, které načtou modul common language runtime do svých procesů a zahájí provádění spravovaného kódu, a tím vytváří softwarové prostředí, který zneužívá spravovaných i nespravovaných funkcí. Rozhraní .NET Framework nejen poskytuje několik hostitelských prostředí modulu runtime, ale také podporuje vývoj hostitelských prostředí modulu runtime třetích stran.

Například technologie ASP.NET je hostitelem modulu runtime poskytuje škálovatelné a serverové prostředí pro spravovaný kód. Technologie ASP.NET pracuje přímo s modulem runtime a povolit aplikace ASP.NET a webové služby XML, které jsou popsány dále v tomto tématu.

Aplikace Internet Explorer je příkladem nespravované aplikace, který je hostitelem modulu runtime (ve formě rozšíření typu standardu MIME). Pomocí aplikace Internet Explorer jako hostitele modulu runtime umožňuje vložit do HTML dokumentů spravovanou komponentu nebo ovládací prvky Windows Forms. Hostování modulu runtime tímto způsobem umožňuje spravovaný mobilní kód, ale s významnými vylepšeními této pouze spravovaný kód nabízí, jako je například částečně důvěryhodné spouštění a izolované úložiště souboru.

Následující obrázek znázorňuje relaci modulu common language runtime a knihovně tříd k vašim aplikacím a celkovému systému. Ilustraci je také znázorněno jak spravovaný kód pracuje v rámci větší architektury.

![Spravovaný kód v rámci větší architektury](../../../docs/framework/get-started/media/circle.gif "kruh") rozhraní .NET Framework v kontextu

Následující části popisují hlavní funkce rozhraní .NET Framework podrobněji.

## <a name="features-of-the-common-language-runtime"></a>Funkce modulu common language runtime

Modul CLR spravuje paměť, spouštění vláken, provádění kódu, ověření bezpečnosti kódu, kompilace a jiných služeb system. Tyto vlastnosti jsou přirozené pro spravovaný kód, který běží na modulu common language runtime.

Týkající se zabezpečení jsou spravované komponenty oceňovány různým stupněm důvěryhodnosti závisící na řadě faktorů, které zahrnují jejich původ (jako je například Internet, podniková síť nebo místní počítač). To znamená, že spravovaná komponenta může nebo nemusí být schopna provádět operace přístupu k souborům, operace přístupu k registru nebo jiné citlivé funkce, i když se používá ve stejné aktivní aplikaci.

Runtime modul vynucuje také odolnost kódu díky implementaci přísné typ a kódové ověřovací infrastruktury volá obecný systém typů (CTS). Specifikace CTS zajišťuje, že všechen spravovaný kód je samo-popisující. Různé kompilátory třetích stran a Microsoft generují spravovaný kód, který odpovídá specifikaci CTS. To znamená, že spravovaný kód může spotřebovat jiné spravované typy a instance při důsledném prosazování typ spolehlivosti a bezpečnosti typů.

Spravované prostředí modulu runtime navíc eliminuje mnoho běžných softwarových problémů. Například modul runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty. uvolňuje je, když jsou již používány. Tato automatická správa paměti řeší dvě nejběžnější chyby aplikace, nevrácenou paměť a neplatné odkazy paměti.

Modul runtime také zrychluje produktivitu vývojáře. Například programátoři zápis aplikací v jejich zvoleném vývojovém jazyce dosud plně využít modul runtime, knihovny tříd a komponent, které jsou napsané v jiných jazycích ostatní vývojáři. Jakýkoliv dodavatel kompilátoru, který se rozhodne zaměřit na modul runtime může tak učinit. Kompilátory, které jsou cíleny rozhraní .NET Framework zpřístupnit funkce rozhraní .NET Framework existujícímu kódu napsanému v tomto jazyce. značně zmírňují proces migrace pro existující aplikace.

Když runtime modul navržen pro software budoucnosti, podporuje také dnešní a dřívější software. Vzájemná funkční spolupráce mezi spravovaným a nespravovaným kódem umožňuje vývojářům nadále používat potřebné komponenty modelu COM a knihovny DLL.

Modul runtime je navržen k zvýšení výkonu. Přestože modul common language runtime poskytuje mnoho standardních služeb modulu runtime, spravovaný kód není nikdy interpretován. Funkci just-in-time (JIT) kompilaci umožňuje veškerému spravovanému kódu ke spuštění v nativním strojovém jazyku systému, na kterém je spuštěn. Mezitím správce paměti odstraňuje možnost fragmentace paměti a zvyšuje paměť lokality referenčního abyste dále zvýšili výkon.

Nakonec modul runtime může být hostován vysoce výkonné, serverové aplikace, jako je například Microsoft SQL Server a Internetové informační služby (IIS). Tato infrastruktura umožňuje používat spravovaný kód k psaní obchodní logiky, zároveň si užívat vynikajícího výkonu v oboru nejlepších podnikových serverů, které podporují hostování modulu runtime.

## <a name="net-framework-class-library"></a>.NET Framework – knihovna tříd

Knihovna tříd rozhraní .NET Framework je kolekce opakovaně použitelných typů, které jsou úzce integrovány s common language runtime. Knihovna tříd je objektově orientovaná, poskytující typy, z něhož pochází spravovaného kódu funkce. To nejen umožňuje snadno použitelné typy rozhraní .NET Framework, ale také snižuje dobu spojenou s učením nových vlastností rozhraní .NET Framework. Navíc komponenty třetích stran se hladce integrují s třídami v rozhraní .NET Framework.

Například kolekce tříd rozhraní .NET Framework implementuje sadu rozhraní pro vývoj vlastní kolekce tříd. Vaše kolekce tříd bezproblémově prolínat s třídami v rozhraní .NET Framework.

Jak by jste očekávali od objektově orientované třídy knihovny, typy rozhraní .NET Framework umožňují provádět řadu běžných programovacích úkolů, včetně úloh, jako je například správa řetězců, shromažďování dat, připojení k databázi a přístup k souborům. Kromě těchto běžných úkolů zahrnuje knihovna tříd typy podporující různé specializované vývojové scénáře. Rozhraní .NET Framework můžete vyvíjet následující typy aplikací a služeb:

- Aplikace konzoly. Zobrazit [vytváření konzolových aplikací](../../../docs/standard/building-console-apps.md).

- Windows grafickým uživatelským rozhraním aplikace (Windows Forms). Zobrazit [Windows Forms](../../../docs/framework/winforms/index.md).

- Windows Presentation Foundation (WPF) aplikace. Zobrazit [Windows Presentation Foundation](../../../docs/framework/wpf/index.md).

- Aplikace v ASP.NET. Zobrazit [webové aplikace s ASP.NET](../../../docs/framework/develop-web-apps-with-aspnet.md).

- Služby systému Windows. Zobrazit [Úvod do služby Windows Service aplikace](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md).

- Aplikace orientované na služby s využitím Windows Communication Foundation (WCF). Zobrazit [aplikace orientované na služby s použitím technologie WCF](../../../docs/framework/wcf/index.md).

- Aplikace podporující pracovní postupy s využitím Windows Workflow Foundation (WF). Zobrazit [vytváření pracovních postupů v rozhraní .NET Framework](https://msdn.microsoft.com/library/cbf3880f-dc7b-466d-b808-1109b1223f4a).

Třídy modelu Windows Forms jsou komplexní sadou opakovaně použitelných typů, které obrovsky zjednodušují vývoj grafického uživatelského rozhraní Windows. Pokud píšete aplikaci technologie ASP.NET webové formuláře, můžete použít třídy webového formuláře.

## <a name="see-also"></a>Viz také:

- [Požadavky na systém](../../../docs/framework/get-started/system-requirements.md)
- [Průvodce instalací](../../../docs/framework/install/index.md)
- [Průvodce vývojem](../../../docs/framework/development-guide.md)
- [Nástroje](../../../docs/framework/tools/index.md)
- [.NET framework – ukázky](https://msdn.microsoft.com/library/177055f8-4a1f-43e7-aee6-995c196079b1)
- [Knihovna tříd rozhraní .NET framework](https://go.microsoft.com/fwlink/?LinkID=227195)
