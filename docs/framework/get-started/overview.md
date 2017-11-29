---
title: "Přehled rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
caps.latest.revision: "34"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c41a7760afb03f1d14d433a30cc12194dcecfcb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="overview-of-the-net-framework"></a>Přehled rozhraní .NET Framework

Rozhraní .NET Framework je technologie, která podporuje vytváření a spouštění nové generace aplikace a webové služby XML. Rozhraní .NET Framework je navržen pro splnění tyto cíle:

- Poskytnout konzistentní objektově orientované programovací prostředí, zda kód objektu je uložena a spustit místně, spuštěn lokálně ale pracujícími na Internetu, nebo spustit vzdáleně.

- Poskytuje prostředí provádění kódu, který minimalizuje konfliktů nasazení a správa verzí softwaru.

- K zajištění prostředí provádění kódu, které podporuje bezpečné spouštění kódu, včetně kód vytvořený neznámý nebo polovičním důvěryhodná třetí strany.

- K poskytování provádění kódu prostředí, která řeší problémy s výkonem skripty nebo interpretovat prostředí.

- Chcete-li vývojářské zkušenosti konzistentní napříč nejrůznějšími typy aplikací, jako je například aplikace pro Windows a webové aplikace.

- Sestavit všechnu komunikaci v oborových standardů k zajištění kódu založené na rozhraní .NET Framework, které se integruje s jakýkoli jiný kód.

> [!NOTE]
> Obecný úvod do rozhraní .NET Framework pro uživatele a vývojáře, najdete v části [Začínáme](../../../docs/framework/get-started/index.md).

Rozhraní .NET Framework se skládá z common language runtime (CLR) a knihovně tříd rozhraní .NET Framework. Modul CLR je základem rozhraní .NET Framework. Modul runtime si můžete představit jako agenta, který spravuje kódu v době provedení poskytuje základní služby, jako je správa paměti, správa vláken a vzdálenou komunikaci, a také vynucuje přísné typu zabezpečení a jiné formy přesnosti kódu, které podporují zabezpečení a odolnosti. Ve skutečnosti koncept správy kódu je základní princip modulu runtime. Kód, aby cíle modulu runtime se označuje jako spravovaného kódu, zatímco kód, který není zaměřují na modul runtime se označuje jako nespravovaný kód. Knihovna tříd je komplexní, objektově orientovaný kolekce opakovaně použitelných typů, které používáte pro vývoj aplikací od tradičních příkazového řádku nebo grafické uživatelské rozhraní (GUI) aplikace až po aplikace založené na technologii ASP.NET, jako jsou webová nejnovější inovace Formuláře a webové služby XML.

Rozhraní .NET Framework se dají hostovat nespravované součásti, které načíst modul CLR do jejich procesy a zahájí provádění spravovaného kódu, a vytvoří tak prostředí softwaru, který zneužije spravovaných i nespravovaných funkcí. Rozhraní .NET Framework nejen poskytuje několik hostitelů modulu runtime, ale také podporuje vývoj modulu runtime třetích stran.

Technologie ASP.NET je hostitelem modulu runtime poskytuje škálovatelný, serverové prostředí pro spravovaný kód. ASP.NET pracuje přímo s modulem runtime umožňující aplikace ASP.NET a webové služby XML, které jsou popsané dále v tomto tématu.

Internet Explorer je příkladem nespravované aplikace, který je hostitelem modulu runtime (ve formě rozšíření pro typ MIME). Použijte Internet Explorer jako hostitele modulu runtime umožňuje vložit spravované součásti nebo ovládací prvky Windows Forms v dokumentech HTML. Hostování prostředí runtime tímto způsobem umožňuje spravovaný mobilní kód, ale s výrazným vylepšením tohoto pouze spravovaného kódu nabízí, jako je například částečně důvěryhodné spouštění a izolované úložiště souborů.

Následující obrázek znázorňuje vztah modul common language runtime a knihovny tříd pro vaše aplikace a celého systému. Na obrázku také ukazuje, jak spravovaného kódu pracuje v rámci větší architektury.

![Spravovaný kód v rámci větší architektury](../../../docs/framework/get-started/media/circle.gif "kruh") rozhraní .NET Framework v kontextu.

Následující části popisují hlavní funkce rozhraní .NET Framework podrobněji.

## <a name="features-of-the-common-language-runtime"></a>Funkce modulu CLR

Modul common language runtime spravuje paměti, provádění vlákna, provádění kódu, ověřování zabezpečení kódu, kompilace a dalších systémových služeb. Tyto funkce jsou vnitřní do spravovaného kódu, který běží na modulu CLR.

Týkající se zabezpečení součástí správy přidělených různým stupněm důvěryhodnosti, v závislosti na počtu faktorů, které zahrnují původu (například Internet, podnikové sítě nebo místní počítač). To znamená, že spravované součásti může nebo nemusí být možné provádět operace přístupu k souborům, přístup k registru provoz nebo jiných citlivých funkcí, i když se používá v stejné aplikace aktivní.

Modul runtime také vynucuje odolnost kódu implementací striktní infrastruktury typ a kód ověření názvem obecný systém typů (STS). CTS zajišťuje, že všechny spravovaný kód popisující samy sebe. Různé společnosti Microsoft a třetích stran kompilátory generovat spravovaného kódu, který odpovídá specifikaci CTS. To znamená, že spravovaného kódu můžete využívat jiné spravované typy a instance, při výhradně vynucování věrnosti a typ bezpečnost typů.

Kromě toho spravované prostředí runtime eliminuje mnoho běžných problémů se softwarem. Například modul runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty používají-li již probíhá. Tato automatická správa paměti řeší dva nejběžnějších chyb, aplikace, nevracení paměti a neplatné odkazy paměti.

Modul runtime také zrychluje produktivita vývojářů. Například programátory zápis aplikací ve vybraném jazyce vývoj ještě plně využít výhod modulu runtime, knihovny tříd a součásti, které jsou napsané v jiných jazycích ostatní vývojáři. Všechny kompilátoru dodavatele, který vybere zaměřit na modul runtime to provést. Kompilátory jazyka cílených na rozhraní .NET Framework zpřístupnit funkce rozhraní .NET Framework pro existující kód napsaný v tomto jazyce proces migrace pro existující aplikace.

Zatímco modul runtime je navržený pro software budoucí, podporuje také softwaru dnešní a dřívější. Vzájemná funkční spolupráce mezi spravovanými a nespravovanými kódu umožňuje vývojářům nadále používat nezbytné komponenty COM a knihovny DLL.

Modul runtime slouží ke zvýšení výkonu. I když modul common language runtime poskytuje mnoho služeb standardní runtime, interpretována nikdy spravovaného kódu. Funkci kompilace za běhu (JIT) umožňuje spouštět v nativním jazyce počítače systému, na kterém je prováděna všechny spravovaného kódu. Správce paměti současně odebere možnost fragmentace paměti a zvyšuje paměti polohu z – odkaz na další zvýšit výkon.

Nakonec modul runtime, mohou být hostovány systémem výkonné a serverové aplikace, například Microsoft SQL Server a Internetové informační služby (IIS). Tato infrastruktura umožňuje používat spravovaného kódu k zápisu obchodní logiky a zároveň i nadále využívat vynikající výkon odvětví nejlepší enterprise servery, které podporují hostování modulu runtime.

## <a name="net-framework-class-library"></a>.NET Framework – knihovna tříd

Knihovna tříd rozhraní .NET Framework je kolekce opakovaně použitelných typů, které jsou pevně integrovány s modul common language runtime. Knihovna tříd je objektově orientované, poskytuje typy, z něhož pochází vlastní spravovaný kód funkce. To nejen umožňuje snadno použitelný typy rozhraní .NET Framework, ale také snižuje dobu spojenou s učení nové funkce rozhraní .NET Framework. Kromě toho komponenty jiných výrobců bezproblémově integrovat s třídami v rozhraní .NET Framework.

Například kolekce tříd rozhraní .NET Framework implementovat sadu rozhraní pro vývoj vlastní kolekce tříd. Třídy kolekce bezproblémově s třídami v rozhraní .NET Framework.

Jak by uživatel očekával od objektově orientované třídy knihovny, typy rozhraní .NET Framework umožňují provádět řadu programovacích úloh, včetně úlohy, jako je správa řetězců, shromažďování dat, připojení k databázi a přístup k souborům. Kromě těchto běžné úkoly knihovny tříd obsahuje typy, které podporují celou řadu specializované vývojové scénáře. Použití rozhraní .NET Framework k vývoji následující typy aplikací a služeb:

- Aplikace konzoly. V tématu [sestavení aplikací konzoly](../../../docs/standard/building-console-apps.md).

- Windows grafického uživatelského rozhraní aplikace (Windows Forms). V tématu [Windows Forms](../../../docs/framework/winforms/index.md).

- Windows Presentation Foundation (WPF) aplikace. V tématu [Windows Presentation Foundation](../../../docs/framework/wpf/index.md).

- Aplikace ASP.NET. V tématu [webové aplikace s ASP.NET](../../../docs/framework/develop-web-apps-with-aspnet.md).

- Služby systému Windows. V tématu [Úvod do systému Windows služby aplikace](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md).

- Aplikace orientované na služby, pomocí služby Windows Communication Foundation (WCF). V tématu [aplikace orientované na služby s použitím technologie WCF](../../../docs/framework/wcf/index.md).

- Aplikace podporující pracovní postupy, pomocí Windows Workflow Foundation (WF). V tématu [vytváření pracovních postupů v rozhraní .NET Framework](http://msdn.microsoft.com/en-us/cbf3880f-dc7b-466d-b808-1109b1223f4a).

Windows Forms třídy jsou komplexní sadu opakovaně použitelných typů, které významně zjednodušují vývoj grafického uživatelského rozhraní systému Windows. Pokud píšete aplikaci webového formuláře ASP.NET, můžete použít třídy webových formulářů.

## <a name="see-also"></a>Viz také

[Požadavky na systém](../../../docs/framework/get-started/system-requirements.md)   
[Průvodce instalací](../../../docs/framework/install/index.md)   
[Průvodce vývojem](../../../docs/framework/development-guide.md)   
[Nástroje](../../../docs/framework/tools/index.md)   
[.NET framework – ukázky](http://msdn.microsoft.com/en-us/177055f8-4a1f-43e7-aee6-995c196079b1)   
[Knihovna tříd rozhraní .NET framework](http://go.microsoft.com/fwlink/?LinkID=227195)
