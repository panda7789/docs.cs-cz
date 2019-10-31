---
title: Kompatibilita aplikací v rozhraní .NET Framework
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: cf0d556dd5df773958e24ff1efcefbc3d8a8d3a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126334"
---
# <a name="application-compatibility-in-the-net-framework"></a>Kompatibilita aplikací v rozhraní .NET Framework

## <a name="introduction"></a>Úvod
Kompatibilita je velice důležitým cílem každé verze rozhraní .NET. Kompatibilita zajišťuje, že každá verze je doplňková, takže předchozí verze budou fungovat i nadále. Na druhé straně změny předchozí funkce (za účelem vylepšení výkonu, řešení potíží se zabezpečením nebo opravy chyb) můžou způsobit problémy s kompatibilitou v existujícím kódu nebo v existujících aplikacích, které běží v novější verzi. .NET Framework rozpoznává změny cíle a změny v běhu. Změny cíle ovlivňují aplikace, které cílí na konkrétní verzi .NET Framework, ale běží v novější verzi. Změny v modulu runtime ovlivňují všechny aplikace spuštěné v konkrétní verzi.

Každá aplikace cílí na konkrétní verzi .NET Framework, kterou lze určit pomocí:

- Definování cílové architektury v aplikaci Visual Studio.
- Určení cílové architektury v souboru projektu.
- Použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ke zdrojovému kódu.

Při spuštění v novější verzi, než je cílová, .NET Framework použije chování quirked k napodobování starší cílové verze. Jinými slovy, aplikace bude spuštěna v novější verzi rozhraní, ale funguje jako v případě, že běží na starší verzi. Mnohé z problémů s kompatibilitou mezi verzemi .NET Framework jsou zmírnit prostřednictvím tohoto modelu quirking. Verze .NET Framework, na kterou aplikace cílí, je určena cílovou verzí záznamu pro doménu aplikace, ve které kód běží. Všechna další sestavení načtená v této cílové doméně aplikace, která .NET Framework verzi. Například v případě spustitelného souboru je rozhraní, které cílí na spustitelný soubor, v režimu kompatibility všechna sestavení v dané doméně AppDomain budou spouštěna v.

## <a name="runtime-changes"></a>Změny modulu runtime

Problémy za běhu jsou ty, které vznikají při umístění nového modulu runtime do počítače a spuštění stejných binárních souborů, ale je vidět jiné chování. Pokud byl binární soubor kompilován pro .NET Framework 4,0, bude spuštěn v režimu kompatibility .NET Framework 4,0 na 4,5 nebo novějších verzích. Mnohé změny, které ovlivňují 4,5, nebudou mít vliv na binární kompilováno pro 4,0. To je specifické pro doménu AppDomain a závisí na nastavení položky sestavení.

## <a name="retargeting-changes"></a>Změny cíle

Změny cíle se projevují v případě, že sestavení, které cílí na 4,0, je teď nastavené na target 4,5. Nyní se sestavení výslovný do nových funkcí a také potenciální problémy s kompatibilitou se starými funkcemi. Znovu, toto je určeno sestavením záznamu, aby Konzolová aplikace používala sestavení, nebo web, který odkazuje na sestavení.

## <a name="net-compatibility-diagnostics"></a>Diagnostika kompatibility rozhraní .NET

Diagnostika kompatibility rozhraní .NET jsou Roslyn analyzátory založené na technologii, které vám pomůžou identifikovat problémy s kompatibilitou aplikací mezi verzemi .NET Framework. Tento seznam obsahuje všechny dostupné analyzátory, i když se u jakékoli konkrétní migrace uplatní jenom podmnožina. Analyzátory určí, které problémy se vztahují k plánované migraci, a budou je jenom naploché.

Každý problém zahrnuje následující informace:

- Popis toho, co se změnilo v předchozí verzi.

- Jaký vliv má změna na zákazníky a zda jsou k dispozici jakákoli alternativní řešení pro zachování kompatibility napříč verzemi.

- Posouzení důležitosti změny. Problémy s kompatibilitou aplikací jsou zařazené do kategorií následujícím způsobem:

    |   |   |
    |---|---|
    |Hlavní|Významná změna ovlivňující velký počet aplikací nebo vyžaduje značnou úpravu kódu.|
    |Vedlejší|Změna, která má vliv na malý počet aplikací nebo které vyžadují menší úpravu kódu.|
    |Okrajový případ|Změna ovlivňující aplikace v rámci velmi konkrétních neobvyklých scénářů.|
    |transparentnost|Změna bez znatelného efektu pro vývojáře nebo uživatele aplikace.|

- Verze označuje, kdy se změna v rozhraní zobrazí jako první. Některé změny jsou představeny v konkrétní verzi a vráceny v pozdější verzi. To je také uvedeno.

- Typ změny:

    |   |   |
    |---|---|
    |Změna cílení|Tato změna ovlivní aplikace, které jsou znovu zkompilovány, aby byly cíleny na novou verzi .NET Framework.|
    |Modul runtime|Tato změna má vliv na existující aplikaci, která cílí na předchozí verzi .NET Framework, ale běží v novější verzi.|

- Ovlivněná rozhraní API, pokud existují.

- ID dostupné diagnostiky

## <a name="usage"></a>Použití
Začněte tím, že vyberete typ změny kompatibility níže:

- [Odlišnosti ve změnách cílení](./retargeting/index.md)
- [Změny v modulu runtime](./runtime/index.md)

## <a name="see-also"></a>Viz také:

- [Verze a závislosti](versions-and-dependencies.md)
- [Co je nového](../whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../whats-new/whats-obsolete.md)
