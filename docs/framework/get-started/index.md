---
title: "Začínáme s rozhraním .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7d84b55abd6c7d72c3a74d17b4f24d00e117a0c
ms.sourcegitcommit: f416ac259c1a771e4e6c72728d8c11a77082f11c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/01/2017
---
# <a name="get-started-with-the-net-framework"></a>Začínáme s rozhraním .NET Framework

Rozhraní .NET Framework je prostředí pro spuštění modulu runtime, který spravuje aplikace cílených rozhraní .NET Framework. Obsahuje modul common language runtime, která poskytuje Správa paměti a jiných služeb system a rozsáhlé třídy knihovny, která umožňuje programátorům využít výhod odolnosti, spolehlivého kódu pro všechny hlavní oblasti o vývoj aplikací.

> [!NOTE] 
> Rozhraní .NET Framework je k dispozici pouze pro systémy Windows. Můžete použít [.NET Core](../../core/index.md) ke spuštění aplikace v systému Windows, systému MacOS a Linux. 

<a name="Introducing"></a>
## <a name="what-is-the-net-framework"></a>Novinky rozhraní .NET Framework

Rozhraní .NET Framework je spravovaného spouštění prostředí pro Windows, který poskytuje celou řadu služeb jeho spuštěné aplikace. Obsahuje dvě hlavní součásti: modul CLR (CLR), což je modul provádění, která zpracovává spuštění aplikace a knihovna tříd rozhraní .NET Framework, který poskytuje knihovnu otestovat, opakovaně použitelný kód, který vývojářům můžete volat z vlastních aplikacích. Služby, které rozhraní .NET Framework poskytuje pro spouštění aplikací zahrnují následující:

- Správa paměti. V řadě programovacích jazyků programátory zodpovídají pro přidělování a uvolňování paměti a zpracování životnosti objektu. V aplikacích rozhraní .NET Framework CLR poskytuje tyto služby jménem aplikace.

- Obecný systém typů. V tradiční programovací jazyky jsou definovány základní typy kompilátoru, který ztěžuje vzájemná funkční spolupráce mezi jazyky. Základní typy v rozhraní .NET Framework, jsou definovány v systému typ rozhraní .NET Framework a jsou společné pro všechny jazyky, které cílí na rozhraní .NET Framework.

- Knihovna rozsáhlé tříd. Místo nutnosti psaní obrovské objemy kód pro zpracování běžné operace nízké úrovně programování, použití programátory snadno přístupné knihovny typů a jejich členové z knihovně tříd rozhraní .NET Framework.

- Architektury pro vývoj a technologie. Rozhraní .NET Framework zahrnuje knihovny pro konkrétní oblasti vývoj aplikací, jako je například technologie ASP.NET pro webové aplikace, technologie ADO.NET pro přístup k datům, Windows Communication Foundation pro aplikace orientované na služby a aplikacích klasické pracovní plochy Windows Presentation Foundation pro systém Windows.

- Vzájemná funkční spolupráce jazyka. Kompilátory jazyka cílených na rozhraní .NET Framework emitování zadání zprostředkující kódu s názvem běžné zprostředkující jazyk souboru CIL (), který je pak kompilované za běhu pomocí modul common language runtime. Pomocí této funkce jsou přístupné do jiných jazyků a programátory zaměřit na vytváření aplikací v jejich upřednostňovaný jazycích rutiny, které jsou napsané v jednom jazyce.

- Kompatibilita verzí. S výjimečných výjimkami aplikace vyvinuté pomocí konkrétní verzi rozhraní .NET Framework pracovat bez úprav na novější verzi.

- Spuštění vedle sebe. Rozhraní .NET Framework pomůže vyřešit konflikty verzí tím, že se několik verzí common language runtime existovat ve stejném počítači. To znamená, že více verzí aplikací mohou existovat vedle sebe a že aplikaci lze spustit na verzi rozhraní .NET Framework, ke kterému bylo vytvořeno. Souběžně sdílená provádění se vztahuje na skupiny rozhraní .NET Framework verze 1.0/1.1, 2.0/3.0/3.5 a 4/4.5.x/4.6.x/4.7.x.

- Cílení na více verzí. Pomocí cílení [.NET Standard](~/docs/standard/net-standard.md), vývojáři vytvářet knihovny tříd, které fungují ve více platformách rozhraní .NET Framework v příslušné verzi standardní podporovány. Například knihovny, které cílí na rozhraní .NET 2.0 standardní lze aplikace, které se zaměřují rozhraní .NET Framework 4.6.1, rozhraní .NET 2.0 jádra a UWP 10.0.16299. 

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Rozhraní .NET Framework pro uživatele

Pokud nemáte vyvíjet aplikace rozhraní .NET Framework, ale je používáte, není nutné mít specifické znalosti o rozhraní .NET Framework nebo jeho provoz. Ve většině případů je rozhraní .NET Framework pro uživatele zcela transparentní.

Pokud používáte operační systém Windows, rozhraní .NET Framework může být již nainstalován ve vašem počítači. Kromě toho pokud nainstalujete aplikaci, která vyžaduje rozhraní .NET Framework, instalační program aplikace nainstalovat na konkrétní verzi rozhraní .NET Framework ve vašem počítači. V některých případech se může zobrazit dialogové okno se žádostí o instalaci rozhraní .NET Framework. Pokud jste právě pokusili spustit aplikaci, pokud se zobrazí toto dialogové okno a v případě, že má počítač přístup k Internetu, můžete přejít na webovou stránku, která umožňuje nainstalovat chybějící verzi rozhraní .NET Framework. Další informace najdete v tématu [Průvodce instalací](../install/index.md).

Obecně platí by neměl odinstalovat verze rozhraní .NET Framework, které jsou nainstalovány ve vašem počítači. Existují dva důvody:

- Pokud aplikace, kterou použijete, závisí na konkrétní verzi rozhraní .NET Framework, je možné při odebrání této verze ukončit aplikaci.

- Některé verze rozhraní .NET Framework jsou na místě aktualizace starší verze. Například [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] je na místě aktualizace na verzi 2.0 a rozhraní .NET Framework 4.7.1 je na místě aktualizace verze 4, 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2 a 4.7. Další informace najdete v tématu [rozhraní .NET Framework verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md).

Ve verzích systému Windows než Windows 8, pokud zvolíte možnost odebrat rozhraní .NET Framework, vždy používat **programy a funkce** v Ovládacích panelech odinstalujte jej. Verze rozhraní .NET Framework nikdy odeberte ručně. V systému Windows 8 a novější verze rozhraní .NET Framework je součástí operačního systému a nelze ho odinstalovat samostatně.

Všimněte si, že více verzí rozhraní .NET Framework mohou společně existovat v jednom počítači, ve stejnou dobu. To znamená, že nemusíte odinstalovat předchozí verze, aby bylo možné nainstalovat na novější verzi.

<a name="ForDevelopers"></a> 
## <a name="the-net-framework-for-developers"></a>Rozhraní .NET Framework pro vývojáře

Pokud jste vývojář, zvolte žádný programovací jazyk, který podporuje rozhraní .NET Framework pro vytvoření aplikace. Protože rozhraní .NET Framework poskytuje jazyková nezávislost a vzájemná funkční spolupráce, komunikovat s jinými aplikací rozhraní .NET Framework a součásti bez ohledu na jazyk, se kterým byly vyvinuty.

K vývoji aplikací rozhraní .NET Framework nebo součástí, postupujte takto:

1. Pokud není je předinstalován v operačním systému, nainstalujte verzi rozhraní .NET Framework, který bude cílit na vaše aplikace. Nejnovější verzi produkční je rozhraní .NET Framework 4.7.1, která je předinstalován v systému Windows 10 patří tvůrci aktualizací a je k dispozici ke stažení v dřívějších verzích operačního systému Windows. Požadavky na systém rozhraní .NET Framework, najdete v části [požadavky na systém](../../../docs/framework/get-started/system-requirements.md). Informace o instalaci jiných verzí rozhraní .NET Framework, najdete v části [Průvodce instalací](../../../docs/framework/install/guide-for-developers.md). Další balíčky rozhraní .NET Framework vydávají vzdálené správy, což znamená, že jste vydané na základě postupného mimo všechny verze regulární ani do plánovaných cyklus. Informace o těchto balíčcích najdete v tématu [rozhraní .NET Framework a Out-of-Band verze](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).

2. Vyberte jazyk nebo jazyků – podpora rozhraní .NET Framework, který chcete používat pro vývoj aplikací. Počet jazyků, které jsou k dispozici, včetně [jazyka Visual Basic](../../visual-basic/index.md), [C#](../../csharp/index.md), [F #](../../fsharp/index.md)a C + +/ CLI od společnosti Microsoft. (Programovací jazyk, který umožňuje vyvíjet aplikace pro rozhraní .NET Framework dodržuje [specifikace společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkId=199862).)

3. Vyberte a nainstalujte vývoj prostředí sloužící k vytvoření aplikace a že podporuje vybraný programovací jazyk nebo jazyky. Microsoft integrované vývojové prostředí (IDE) pro aplikace .NET Framework je [Visual Studio](http://go.microsoft.com/fwlink/?LinkId=325532). Je k dispozici v několika edicích.

Další informace o vývoji aplikací, které cílí na rozhraní .NET Framework, najdete v článku [Průvodce vývojem](../../../docs/framework/development-guide.md).

## <a name="related-topics"></a>Související témata

| Název | Popis |
| ----- |------------ |
| [Přehled](../../../docs/framework/get-started/overview.md) | Poskytuje podrobné informace pro vývojáře, kteří vytvářejí aplikace cílených rozhraní .NET Framework. |
| [Průvodce instalací](../../../docs/framework/install/index.md) | Poskytuje informace o instalaci rozhraní .NET Framework. |  
| [Rozhraní .NET Framework a Out-of-Band verze](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md) | Popisuje rozhraní .NET Framework verze vzdálené správy a jejich použití ve vaší aplikaci. |
| [Požadavky na systém](../../../docs/framework/get-started/system-requirements.md) | Uvádí požadavky na hardware a software pro spuštění rozhraní .NET Framework. |
| [.NET core a Open Source](../../../docs/framework/get-started/net-core-and-open-source.md) | Popisuje .NET Core ve vztahu k rozhraní .NET Framework a jak získat přístup k projektům .NET Core open source. |
| [Dokumentace k .NET core](https://docs.microsoft.com/dotnet/) | Poskytuje koncepční a referenční dokumentace rozhraní API pro .NET Core. |
| [Standardní rozhraní .NET](~/docs/standard/net-standard.md) | Popisuje standardní .NET verzí specifikace, které podporují jednotlivé implementace rozhraní .NET zaručit, že jsou k dispozici na několika platformách konzistentní sada rozhraní API.

## <a name="see-also"></a>Viz také

[.NET framework – Průvodce](../../../docs/framework/index.md)   
[Co je nového](../../../docs/framework/whats-new/index.md)   
[Prohlížeč rozhraní API .NET](/dotnet/api/)   
[Průvodce vývojem](../../../docs/framework/development-guide.md)
