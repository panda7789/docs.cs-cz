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
ms.openlocfilehash: c866e3d1a4de31361843f5c071510fd18247cb39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132816"
---
# <a name="common-language-runtime-clr-overview"></a>Modul CLR (Common Language Runtime) – přehled

.NET Framework poskytuje běhové prostředí označované jako modul CLR (Common Language Runtime), který spouští kód a poskytuje služby, které usnadňují proces vývoje.

Kompilátory a nástroje zpřístupňují funkce modulu CLR (Common Language Runtime) a umožňují psát kód, který je výhodou z tohoto spravovaného prováděcího prostředí. Kód, který vyvíjíte pomocí kompilátoru jazyka, který cílí na modul runtime, se nazývá spravovaný kód; využívá výhody funkcí, jako je například integrace mezi jazyky, zpracování výjimek v různých jazycích, vylepšené zabezpečení, Správa verzí a podpora nasazení, zjednodušený model pro interakci s komponentami a ladění a profilování služeb.

> [!NOTE]
> Kompilátory a nástroje jsou schopny vytvářet výstupy, které může modul CLR (Common Language Runtime) spotřebovat, protože systém typů, formát metadat a běhové prostředí (virtuální spouštěcí systém) jsou definovány veřejným standardem, společný jazyk ECMA Specifikace infrastruktury Další informace naleznete v tématu [specifikace C# ECMA a Common Language Infrastructure](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).

Aby modul runtime mohl poskytovat služby spravovanému kódu, musí kompilátory jazyka generovat metadata, která popisují typy, členy a odkazy v kódu. Metadata se ukládají s kódem; každý spustitelný společný spustitelný soubor PE (Common Language Runtime) obsahuje metadata. Modul runtime používá metadata k vyhledání a načtení tříd, rozmístění instancí v paměti, řešení vyvolání metod, generování nativního kódu, vymáhání zabezpečení a nastavování hranic kontextu v době běhu.

Modul runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty a uvolňuje je, když již nejsou používány. Objekty, jejichž životnost se spravují tímto způsobem, se nazývají spravovaná data. Uvolňování paměti eliminuje nevracení paměti a také některé další běžné chyby programování. Pokud je váš kód spravovaný, můžete v aplikaci .NET Framework použít spravovaná data, nespravovaná data nebo spravovaná i nespravovaná data. Vzhledem k tomu, že kompilátory jazyka poskytují své vlastní typy, například primitivní typy, nesmíte vždy znát (nebo potřebujete znát), zda jsou vaše data spravována.

Modul CLR (Common Language Runtime) usnadňuje návrh komponent a aplikací, jejichž objekty vzájemně komunikují napříč jazyky. Objekty napsané v různých jazycích mohou vzájemně komunikovat a jejich chování může být pevně integrovaná. Můžete například definovat třídu a potom použít jiný jazyk k odvození třídy z původní třídy nebo volat metodu v původní třídě. Můžete také předat instanci třídy metodě třídy napsané v jiném jazyce. Tato integrace mezi jazyky je možná, protože kompilátory a nástroje jazyka, které cílí na modul runtime, používají společný systém typů definovaný modulem runtime a dodržují pravidla modulu runtime pro definování nových typů a také pro vytváření, používání, zachování a vazba na typy.

V rámci svých metadat všechny spravované součásti přenášejí informace o komponentách a prostředcích, na které byly vytvořeny. Modul runtime používá tyto informace k zajištění toho, že vaše komponenta nebo aplikace má specifikované verze všeho, co IT potřebuje, což způsobí, že váš kód bude méně pravděpodobný v důsledku nesplnění závislosti. Informace o registraci a stavová data se už neukládají v registru, kde se můžou obtížně nakládat a udržovat. Místo toho jsou informace o typech, které definujete (a jejich závislosti), uloženy spolu s kódem jako metadata, takže úkoly replikace komponent a odebírání jsou mnohem méně komplikované.

Kompilátory a nástroje jazyka zpřístupňují funkcionalitu modulu runtime způsobem, který by měl být užitečný a intuitivní pro vývojáře. To znamená, že některé funkce modulu runtime mohou být více patrné v jednom prostředí než v jiném. Způsob, jakým se můžete setkat s modulem runtime, závisí na tom, jaké kompilátory jazyka nebo nástroje používáte. Například pokud jste vývojář Visual Basic, můžete si všimnout, že s modulem CLR (Common Language Runtime) má jazyk Visual Basic více funkcí orientovaných na objekty než předtím. Modul runtime poskytuje následující výhody:

- Byl vylepšen výkon.

- Možnost snadného používání komponent vyvinutých v jiných jazycích.

- Rozšiřitelné typy poskytované knihovnou tříd.

- Jazykové funkce, jako je dědičnost, rozhraní a přetížení pro objektově orientované programování.

- Podpora pro explicitní volné zřetězení, která umožňuje vytváření vícevláknových a škálovatelných aplikací.

- Podpora strukturovaného zpracování výjimek.

- Podpora vlastních atributů.

- Uvolňování paměti.

- Použití delegátů namísto ukazatelů na funkce pro zvýšení bezpečnosti a zabezpečení typů. Další informace o delegátech naleznete v tématu [Common Type System](../../docs/standard/base-types/common-type-system.md).

## <a name="clr-versions"></a>Verze CLR

Číslo verze .NET Framework nutně neodpovídá číslu verze CLR, který zahrnuje. Následující tabulka ukazuje, jakým způsobem korelují čísla těchto dvou verzí:

|Verze rozhraní .NET Framework|Zahrnuje verzi CLR|
|----------------------------|--------------------------|
|1.0|1.0|
|1.1|1.1|
|2.0|2.0|
|3.0|2.0|
|3.5|2.0|
|4|4|
|4,5 (včetně 4.5.1 a 4.5.2)|4|
|4,6 (včetně 4.6.1 a 4.6.2)|4|
|4,7 (včetně 4.7.1 a 4.7.2)|4|
|4,8|4|

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Proces spravovaného spuštění](managed-execution-process.md)|Popisuje kroky potřebné k využití modulu CLR (Common Language Runtime).|
|[Automatická správa paměti](automatic-memory-management.md)|Popisuje způsob, jakým systém uvolňování paměti přiděluje a uvolňuje paměť.|
|[Přehled .NET Framework](../framework/get-started/overview.md)|Popisuje klíčové .NET Framework koncepty, jako je například společný systém typů, vzájemná funkční spolupráce mezi jazyky, spravované spouštění, aplikační domény a sestavení.|
|[Obecný systém typů](./base-types/common-type-system.md)|Popisuje, jak jsou typy deklarovány, používány a spravovány v modulu runtime v rámci podpory integrace mezi jazyky.|

## <a name="see-also"></a>Viz také:

- [Verze a závislosti](../framework/migration-guide/versions-and-dependencies.md)
