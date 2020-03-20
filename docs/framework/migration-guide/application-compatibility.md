---
title: Runtime a retargeting změny - .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196694"
---
# <a name="application-compatibility-in-the-net-framework"></a>Kompatibilita aplikací v rozhraní .NET Framework

Kompatibilita je důležitým cílem každé verze .NET. Kompatibilita zajišťuje, že každá verze je aditivní, takže předchozí verze budou i nadále fungovat. Na druhou stranu změny předchozích funkcí (například ke zlepšení výkonu, řešení problémů se zabezpečením nebo opravě chyb) mohou způsobit problémy s kompatibilitou v existujícím kódu nebo existujících aplikacích, které běží v novější verzi.

Každá aplikace cílí na konkrétní verzi rozhraní .NET Framework podle následujících cílů:

- Definování cílového rozhraní v sadě Visual Studio.
- Určení cílového rozhraní v souboru projektu.
- Použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute> a na zdrojový kód.

Při migraci z jedné verze rozhraní .NET Framework do jiné ho lze zvážit dvěma typy změn:

- [Změny za běhu](#runtime-changes)
- [Změny opětovného cílení](#retargeting-changes)

## <a name="runtime-changes"></a>Změny v modulu runtime

Problémy s runtime jsou ty, které vznikají při umístění nového runtime do počítače a změny chování aplikace. Při spuštění na novější verzi, než co bylo cílené, rozhraní .NET Framework používá *vtípek* chování napodobovat starší cílenou verzi. Aplikace běží na novější verzi, ale funguje, jako by byla spuštěna na starší verzi. Mnoho problémů s kompatibilitou mezi verzemi rozhraní .NET Framework je zmírněno prostřednictvím tohoto modelu quirking. Pokud byl například binární soubor zkompilován pro rozhraní .NET Framework 4.0, ale běží v počítači s rozhraním .NET Framework 4.5 nebo novějším, běží v režimu kompatibility rozhraní .NET Framework 4.0. To znamená, že mnoho změn v novější verzi nemá vliv na binární.

Verze rozhraní .NET Framework, na kterou se aplikace zaměřuje, je určena cílovou verzí vstupního sestavení pro doménu aplikace, ve které je kód spuštěn. Všechna další sestavení načtená v této doméně aplikace cílí na tuto verzi. Například v případě spustitelného souboru verze, která je spustitelný mýše cíle režim kompatibility všechna sestavení v této doméně aplikace spustit pod.

Chcete-li zobrazit seznam změn za běhu, které se vztahují na vaše prostředí, vyberte verzi rozhraní .NET Framework, na kterou aktuálně cílíte, a verzi, na kterou chcete migrovat:

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Změny cílení

Retargeting změny jsou ty, které vznikají při sestavení je znovu zkompilován cílit novější verzi. Cílení na novější verzi znamená, že sestavení se rozhodne pro nové funkce, stejně jako potenciální problémy s kompatibilitou starých funkcí.

Chcete-li zobrazit seznam změn opětovného cílení, které se vztahují na vaše prostředí, vyberte verzi rozhraní .NET Framework, na kterou aktuálně cílíte, a verzi, na kterou chcete migrovat:

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Klasifikace dopadů

V tématech, která popisují změny za běhu a retargeting, například [Změny retargetingu pro migraci z 4.7.2 na 4.8](retargeting/4.7.2-4.8.md), jsou jednotlivé položky klasifikovány podle očekávaného dopadu takto:

**Hlavní**\
Významná změna, která ovlivňuje velký počet aplikací nebo která vyžaduje podstatnou změnu kódu.

**Menší**\
Změna, která má vliv na malý počet aplikací nebo která vyžaduje menší úpravy kódu.

**Pouzdro edge**\
Změna, která ovlivňuje aplikace ve velmi specifických scénářích, které nejsou běžné.

**Průhledné**\
Změna, která nemá žádný znatelný vliv na vývojáře nebo uživatele aplikace. Z důvodu této změny by aplikace neměla vyžadovat úpravy.

## <a name="see-also"></a>Viz také

- [Verze a závislosti](versions-and-dependencies.md)
- [Co je nového](../whats-new/index.md)
- [Co je zastaralé](../whats-new/whats-obsolete.md)
