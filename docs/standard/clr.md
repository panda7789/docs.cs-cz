---
title: Přehled clr (Common Language Runtime) – rozhraní .NET Framework
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74884407"
---
# <a name="common-language-runtime-clr-overview"></a>Přehled clr (Common Language Runtime)

Rozhraní .NET Framework poskytuje prostředí za běhu nazývané za běhu common jazyka, který spouští kód a poskytuje služby, které usnadňují proces vývoje.

Kompilátory a nástroje zveřejňují funkce běžného jazyka runtime a umožňují psát kód, který těží z tohoto prostředí spravovaného spuštění. Kód, který vyvíjíte pomocí kompilátoru jazyka, který cílí na runtime se nazývá spravovaný kód; využívá funkce, jako je integrace mezi jazyky, zpracování výjimek mezi jazyky, rozšířené zabezpečení, správa verzí a podpora nasazení, zjednodušený model pro interakci s komponentami a služby ladění a profilování.

> [!NOTE]
> Kompilátory a nástroje jsou schopny vytvářet výstupy, které může modul COMMON Language runtime využívat, protože typový systém, formát metadat a runtime prostředí (systém virtuálního spuštění) jsou definovány veřejným standardem, společným jazykem ECMA Specifikace infrastruktury. Další informace naleznete v [tématech ECMA C# a Common Language Infrastructure Specifications](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Chcete-li povolit modul runtime poskytovat služby spravovaného kódu, musí kompilátory jazyka vyzařovat metadata, která popisují typy, členy a odkazy ve vašem kódu. Metadata jsou uložena s kódem; každý načítatelný přenosný spustitelný soubor modulu RUNTIME (PE) s common language runtime obsahuje metadata. Modul runtime používá metadata k vyhledání a načtení tříd, rozložení instancí v paměti, řešení vyvolání metody, generování nativního kódu, vynucení zabezpečení a nastavení hranic kontextu běhu.

Runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty, jejich uvolnění, když jsou již používány. Objekty, jejichž životnost je spravována tímto způsobem, se nazývají spravovaná data. Uvolňování paměti eliminuje nevracení paměti, stejně jako některé další běžné chyby programování. Pokud je váš kód spravován, můžete použít spravovaná data, nespravovaná data nebo spravovaná i nespravovaná data v aplikaci rozhraní .NET Framework. Vzhledem k tomu, že kompilátory jazyka poskytují své vlastní typy, jako jsou primitivní typy, nemusí vždy vědět (nebo potřebujete vědět), zda jsou vaše data spravována.

Běžný jazyk runtime usnadňuje navrhování komponent a aplikací, jejichž objekty interagují v různých jazycích. Objekty napsané v různých jazycích mohou vzájemně komunikovat a jejich chování může být úzce integrováno. Můžete například definovat třídu a potom použít jiný jazyk k odvození třídy z původní třídy nebo volání metody na původní třídě. Instanci třídy můžete také předat metodě třídy napsané v jiném jazyce. Tato integrace mezi jazyky je možná, protože kompilátory jazyka a nástroje, které se zaměřují na runtime, používají společný typový systém definovaný runtime a řídí se pravidly za běhu pro definování nových typů, stejně jako pro vytváření, používání, uchování a vazbu na typy.

Jako součást svých metadat všechny spravované součásti nesou informace o součástech a prostředcích, proti kterým byly vytvořeny. Runtime používá tyto informace k zajištění, že vaše součást nebo aplikace má zadané verze vše, co potřebuje, což snižuje pravděpodobnost přerušení kódu z důvodu některé neuspokojené závislosti. Registrační informace a údaje o stavu již nejsou uloženy v registru, kde může být obtížné je vytvořit a udržovat. Místo toho informace o typech, které definujete (a jejich závislosti) je uložen s kódem jako metadata, takže úkoly replikace komponent a odebrání mnohem méně složité.

Kompilátory jazyka a nástroje zveřejňují funkce runtime způsoby, které jsou určeny k užitečné a intuitivní pro vývojáře. To znamená, že některé funkce běhu může být výraznější v jednom prostředí než v jiném. Způsob, jakým dochází k běhu, závisí na tom, které kompilátory jazyka nebo nástroje používáte. Například pokud jste vývojář jazyka Visual Basic, můžete si všimnout, že s běžným jazykem runtime, jazyk jazyka Visual Basic má více objektově orientovaných funkcí než dříve. Runtime poskytuje následující výhody:

- Byl vylepšen výkon.

- Schopnost snadno používat komponenty vyvinuté v jiných jazycích.

- Rozšiřitelné typy poskytované knihovnou tříd.

- Funkce jazyka, jako je dědičnost, rozhraní a přetížení pro objektově orientované programování.

- Podpora explicitního volného podprocesu, který umožňuje vytváření vícevláknových, škálovatelných aplikací.

- Podpora pro strukturované zpracování výjimek.

- Podpora vlastních atributů.

- Uvolněné.

- Použití delegátů namísto ukazatelů funkce pro zvýšení bezpečnosti a zabezpečení typu. Další informace o delegátech naleznete [v tématu Common Type System](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Verze CLR

Číslo verze rozhraní .NET Framework nemusí nutně odpovídat číslo verze CLR, které obsahuje. Seznam verzí rozhraní .NET Framework a jejich odpovídajících verzí CLR naleznete v [tématu verze rozhraní .NET Framework a závislosti](../framework/migration-guide/versions-and-dependencies.md). Verze .NET Core mají jednu verzi produktu, to znamená, že neexistuje žádná samostatná verze CLR. Seznam verzí jádra rozhraní .NET naleznete v [tématu Stažení jádra .NET](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Proces spravovaného spouštění](managed-execution-process.md)|Popisuje kroky potřebné k využití běžného jazyka runtime.|
|[Automatická správa paměti](automatic-memory-management.md)|Popisuje, jak systém uvolňování paměti přiděluje a uvolňuje paměť.|
|[Přehled rozhraní .NET Framework](../framework/get-started/overview.md)|Popisuje koncepty rozhraní KEY .NET Framework, jako je například běžný systém typů, interoperabilita mezi jazyky, spravované spuštění, aplikační domény a sestavení.|
|[Obecný systém typů](./base-types/common-type-system.md)|Popisuje, jak jsou typy deklarovány, používány a spravovány v době běhu na podporu integrace mezi jazyky.|
