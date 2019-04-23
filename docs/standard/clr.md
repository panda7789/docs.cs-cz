---
title: Přehled modelu Common Language Runtime (CLR) – .NET Framework
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
author: rpetrusha
ms.author: ronpet
ms.custom: updateeachrelease
ms.openlocfilehash: 798b3d29a13434511f64dfc358fb7690948cacfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59972950"
---
# <a name="common-language-runtime-clr-overview"></a>Přehled modelu Common Language Runtime (CLR)

Rozhraní .NET Framework poskytuje běhové prostředí volá modul common language runtime, která spustí kód a poskytuje služby, které usnadňují proces vývoje.

Kompilátory a nástroje poskytují funkcionalitu modulu common language runtime a umožňují také napsat kód, které mají výhody z tohoto spravovaného prostředí pro spouštění. Kód, který vyvíjíte s kompilátorem jazyka, který se zaměřuje na modul runtime se nazývá spravovaný kód. výhody plynou z vlastností, jako je podpory mezi jazykové integrace, mezi jazykové zpracování vyjímek, vylepšené zabezpečení, správy verzí a nasazení, zjednodušený model pro interakci komponent, ladění a profilovací služby.

> [!NOTE]
> Kompilátory a nástroje jsou schopny vytvořit výstup, který modul common language runtime může použít, protože systém typů, formát metadat a prostředí runtime (systém virtuálního spuštění) jsou definovány veřejným standardem jazyka ECMA společné Specifikace infrastruktury. Další informace najdete v tématu [ECMA C# a společné jazykové infrastruktury specifikace](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Pokud chcete povolit modul runtime k poskytování služeb pro spravovaný kód, musí kompilátory jazyka poskytl metadata popisující typy, členy a odkazy ve vašem kódu. Metadata jsou uložena s kódem; každý zaveditelný common language runtime přenosný spustitelný (PE) soubor obsahuje metadata. Modul runtime používá metadata k vyhledání a načtení tříd, rozmístění instancí v paměti, vyřešení vyvolávání metod, generování nativního kódu, vynutit zabezpečení a nastavení hranic kontextu za běhu.

Modul runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty. uvolňuje je, když jsou již používány. Objekty, jejichž existence jsou spravovány tímto způsobem se nazývají spravovaná data. Uvolňování paměti eliminuje nevracení paměti, jakož i některé jiné běžné programovací chyby. Pokud váš kód řízen, můžete použít spravovaná data, nespravovaná data nebo spravovaných i nespravovaných dat ve vaší aplikaci rozhraní .NET Framework. Protože kompilátory jazyka poskytují jejich vlastní typy, jako jsou například primitivní typy pravděpodobně ne vždy znáte (nebo potřebovat znát) určuje, zda vaše data spravována.

Modul common language runtime usnadňuje návrh komponent a aplikací, jejichž objekty vzájemně komunikují napříč jazyky. Objekty, které jsou napsány v různých jazycích mohou komunikovat mezi sebou a jejich chování může být pevně integrováno. Můžete například definovat třídu a potom použít jiný jazyk k odvození třídy z té původní nebo zavolat metodu ve zdrojové třídě. Můžete také předat instanci třídy metodě třídy napsané v jiném jazyce. Tato integrace napříč jazyky je možné, protože kompilátory a nástroje, které se zaměřují na modul runtime použít obecný systém typů definované modulem runtime a řídí se pravidly modulu runtime pro definování nových typů, stejně jako pro vytváření, používání, uchovávání, a vázání typů.

Všechny spravované komponenty jako součást svých metadat nesou informaci o součástech a zdrojích, které byly vytvořeny. Modul runtime používá tyto informace k zajištění, že vaše komponenta nebo aplikace má specifikovány verze všeho, co potřebuje, díky tomu váš kód pravděpodobnost zhroucení z důvodu nesplnění nějaké závislosti. Registrační informace a stavová data jsou již uloženy v registru, ve kterém může být složité jejich zavedení a udržovat. Místo toho informace o vámi definovaných typech (a jejich závislostech) uložena s kódem jako metadata. Toto činí úkoly spojené s replikací a odebráním komponent mnohem méně komplikované.

Kompilátory a nástroje poskytují funkcionalitu modulu runtime takovým způsobem, který má být užitečný a intuitivní pro vývojáře. To znamená, že některé funkce modulu runtime může být více patrné v jednom prostředí než v jiném. Možnosti modulu runtime závisí na jaké kompilátory a nástroje jazyka použijete. Například pokud jste vývojář Visual Basic, můžete si všimnout, že se modul common language runtime jazyka Visual Basic má více objektově orientovaných vlastností než před. Modul runtime poskytuje následující výhody:

- Byl vylepšen výkon.

- Schopnost snadno používat komponenty vyvinuté v jiných jazycích.

- Rozšiřitelné typy poskytované knihovnou tříd.

- Jazykové vlastnosti zahrnující například dědičnost, rozhraní a přetížení pro objektově orientované programování.

- Podpora pro explicitní volné zřetězení umožňující vytváření vícevláknových a škálovatelných aplikací.

- Podpora pro strukturované zpracování výjimek.

- Podpora pro vlastní atributy.

- Uvolnění paměti.

- Použití delegátů namísto ukazatelů funkcí pro zvýšení typové bezpečnosti a zabezpečení. Další informace o delegátech naleznete v tématu [obecný systém typů](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Verze modulu CLR

Číslo verze rozhraní .NET Framework není nemusí nutně odpovídat číslu verze modulu CLR, které obsahuje. Následující tabulka ukazuje, jak souvisí čísla dvou verzí:

|Verze rozhraní .NET Framework|Zahrnuje verzi CLR|
|----------------------------|--------------------------|
|1.0|1.0|
|1.1|1.1|
|2.0|2.0|
|3.0|2.0|
|3.5|2.0|
|4|4|
|4.5 (včetně 4.5.1 a 4.5.2)|4|
|4.6 (včetně 4.6.1 a 4.6.2)|4|
|4.7 (včetně 4.7.1 a 4.7.2)|4|
|4.8|4|

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Proces spravovaného spuštění](managed-execution-process.md)|Popisuje kroky potřebné k využití modulu common language runtime.|
|[Automatická správa paměti](automatic-memory-management.md)|Popisuje, jak systému uvolňování paměti přiděluje a uvolňuje paměť.|
|[Přehled rozhraní .NET Framework](../framework/get-started/overview.md)|Popisuje klíčové pojmy rozhraní .NET Framework, jako je obecný systém typů, vzájemná funkční spolupráce mezi jazyky, spravované spouštění, aplikační domény a sestavení.|
|[Obecný systém typů](./base-types/common-type-system.md)|Popisuje, jak jsou typy deklarovány, používat a spravovány v modulu runtime kvůli podpoře mezi jazykové integrace.|

## <a name="see-also"></a>Viz také:

- [Verze a závislosti](../framework/migration-guide/versions-and-dependencies.md)