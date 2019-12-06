---
title: Přehled modulu CLR (Common Language Runtime) – .NET Framework
ms.date: 04/02/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
ms.custom: updateeachrelease
ms.openlocfilehash: 6f9ad8aafc37039b55ae3bf6eb743e07ad8e2235
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884407"
---
# <a name="common-language-runtime-clr-overview"></a>Modul CLR (Common Language Runtime) – přehled

Rozhraní .NET Framework poskytuje běhové prostředí, nazvané modul CLR (Common Language Runtime). Toto běhové prostředí spouští kód a poskytuje služby, které usnadňují proces vývoje.

Kompilátory a nástroje poskytují funkcionalitu modulu CLR (Common Language Runtime) a umožňují vám zapisovat kód, který z tohoto spravovaného prostředí pro spouštění získává výhody. Kód, který vyvíjíte s kompilátorem jazyka, a který se zaměřuje na modul runtime se nazývá spravovaný kód. Jeho výhody plynou z vlastností, jako jsou integrace mezi jazyky, mezi jazykové zpracování vyjímek, vylepšené zabezpečení, podpora pro správu verzí a nasazení, zjednodušený model pro interakci komponent, ladění a profilovací služby.

> [!NOTE]
> Kompilátory a nástroje jsou schopny vytvořit výstup, který společný jazykový modul runtime může použít, protože systém typů, formát metadat i prostředí runtime (systém virtuálního spuštění) jsou definovány veřejným standardem, specifikací ECMA společné jazykové infrastruktury. Další informace naleznete v tématu [specifikace C# ECMA a Common Language Infrastructure](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Chcete-li v modulu runtime povolit poskytování služeb pro spravovaný kód, tak je nutné, aby kompilátor jazyka poskytl metadata popisující typy, členy a odkazy ve vašem kódu. Metadata jsou uložena s kódem; každý zaveditelný modul CLR (Common Language Runtime) přenosného spustitelného souboru (PE) obsahuje metadata. Modul runtime používá metadata k nalezení a načtení tříd, rozmístění instancí v paměti, vyřešení vyvolávání metod, generování nativního kódu, vynucení zabezpečení a nastavení hranic kontextu za běhu.

Modul runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty. Uvolňuje je, když již nejsou déle používány. Objekty, jejichž existence jsou spravovány tímto způsobem se nazývají spravovaná data. Uvolňování paměti eliminuje nevracení paměti stejně jako některé jiné běžné programovací chyby. Pokud je váš kód řízen, můžete ve vaší aplikaci rozhraní .NET Frameworku použít spravovaná data, nespravovaná data nebo obojí. Protože kompilátory jazyka poskytují jejich vlastní typy, například primitivní typy pravděpodobně ne vždy víte (nebo potřebujete vědět), zda jsou vaše data spravována.

modul CLR (Common Language Runtime) usnadňuje návrh komponent a aplikací, jejichž objekty vzájemně komunikují napříč jazyky. Objekty, které jsou napsány v různých jazycích, mohou vzájemně komunikovat a jejich chování může být pevně integrováno. Můžete například definovat třídu a potom použít jiný jazyk k odvození nové třídy z té původní nebo zavolat metodu ve zdrojové třídě. Můžete také předat instanci třídy metodě třídy napsané v jiném jazyce. Mezi jazyková integrace je možná, protože kompilátory a nástroje jazyka, které se zaměřují na modul runtime používají specifikaci CTS (Common Type System), která je definována tímto modulem. Řídí se pravidly modulu runtime pro definování nových typů, stejně jako pro vytváření, používání, uchovávání a vázání typů.

Všechny spravované komponenty jako součást svých metadat nesou informaci o součástech a zdrojích, oproti kterým byly vybudovány. Modul runtime používá tuto informaci, aby zajistil, že vaše komponenta nebo aplikace má specifikovány verze všeho potřebného. Toto snižuje pravděpodobnost zhroucení vašeho kódu z důvodu nesplnění nějaké závislosti. Registrační informace a stavová data nejsou již uloženy v registru, kde je složité jejich zavedení a správa. Místo toho je informace o vámi definovaných typech (a jejich závislostech) uložena s kódem jako metadata. Toto činí úkoly spojené s replikací a odebráním komponent mnohem méně komplikované.

Kompilátory a nástroje jazyka předkládají funkcionalitu modulu runtime takovým způsobem, který je užitečný a intuitivní pro vývojáře. To znamená, že některé vlastnosti tohoto modulu mohou být více patrné v jednom prostředí než v jiném. Možnosti modulu runtime závisí na tom,  jaké kompilátory a nástroje jazyka použijete. Například pokud jste vývojář Visual Basic aplikací, můžete si všimnout, že modul CLR (Common Language Runtime) jazyka Visual Basic má více objektově-orientovaných vlastností než dříve. Modul runtime poskytuje následující výhody:

- Byl vylepšen výkon.

- Schopnost snadno používat komponenty vyvinuté v jiných jazycích.

- Rozšiřitelné typy poskytované knihovnou tříd.

- Jazykové vlastnosti zahrnující například dědičnost, rozhraní a přetížení pro objektově orientované programování.

- Podporu pro explicitní volné zřetězení umožňující vytváření vícevláknových a škálovatelných aplikací.

- Podporu pro strukturované zpracování výjimek.

- Podporu pro vlastní atributy.

- Uvolňování paměti.

- Použití delegátů namísto ukazatelů funkcí pro zvýšení typové bezpečnosti a zabezpečení. Další informace o delegátech naleznete v tématu [Common Type System](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Verze CLR

Číslo verze .NET Framework nutně neodpovídá číslu verze CLR, který zahrnuje. Seznam verzí .NET Framework a jejich odpovídajících verzí modulu CLR naleznete v tématu [.NET Framework verze a závislosti](../framework/migration-guide/versions-and-dependencies.md). Verze .NET Core mají jednu verzi produktu, to znamená, že neexistuje žádná samostatná verze CLR. Seznam verzí .NET Core najdete v tématu [stažení .NET Core](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="related-topics"></a>Příbuzná témata

|Název|Popis|
|-----------|-----------------|
|[Proces spravovaného spuštění](managed-execution-process.md)|Popisuje kroky potřebné k využití modulu CLR (Common Language Runtime).|
|[Automatická správa paměti](automatic-memory-management.md)|Popisuje, jak systém uvolňování paměti přiděluje a uvolňuje paměť.|
|[Přehled .NET Framework](../framework/get-started/overview.md)|Popisuje klíčové pojmy rozhraní .NET Frameworku jako je specifikace CTS (Common Type System), vzájemná funkční spolupráce mezi jazyky, spravované spouštění, domény aplikace a sestavení.|
|[Obecný systém typů](./base-types/common-type-system.md)|Popisuje, jak jsou v modulu runtime kvůli podpoře mezi jazykové integrace typy deklarovány, používány a spravovány.|
