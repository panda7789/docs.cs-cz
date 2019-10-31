---
title: Spuštění a změna cílení na změny – .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196694"
---
# <a name="application-compatibility-in-the-net-framework"></a>Kompatibilita aplikací v .NET Framework

Kompatibilita je důležitým cílem každé verze rozhraní .NET. Kompatibilita zajišťuje, že každá verze je doplňková, takže předchozí verze budou fungovat i nadále. Na druhé straně změny předchozí funkce (například pro zlepšení výkonu, řešení potíží se zabezpečením nebo opravy chyb) mohou způsobit problémy s kompatibilitou v existujícím kódu nebo v existujících aplikacích, které jsou spuštěny v novější verzi.

Každá aplikace cílí na konkrétní verzi .NET Framework podle:

- Definování cílové architektury v aplikaci Visual Studio.
- Určení cílové architektury v souboru projektu.
- Použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ke zdrojovému kódu.

Při migraci z jedné verze .NET Framework na jinou existují dva typy změn, které je třeba vzít v úvahu:

- [Změny modulu runtime](#runtime-changes)
- [Změny cíle](#retargeting-changes)

## <a name="runtime-changes"></a>Změny modulu runtime

Problémy za běhu jsou ty, které vznikají při umístění nového modulu runtime do počítače a změny chování aplikace. Při spuštění v novější verzi, než je cílová, .NET Framework používá chování *quirked* k napodobování starší cílové verze. Aplikace běží na novější verzi, ale funguje jako v případě, že běží na starší verzi. Mnohé z problémů s kompatibilitou mezi verzemi .NET Framework jsou zmírnit prostřednictvím tohoto modelu quirking. Například pokud byl binární soubor kompilován pro .NET Framework 4,0, ale běží na počítači s .NET Framework 4,5 nebo novějším, běží v .NET Framework 4,0 režim kompatibility. To znamená, že mnoho změn v novější verzi nemá vliv na binární soubor.

Verze .NET Framework, na kterou aplikace cílí, je určena cílovou verzí záznamu pro doménu aplikace, ve které kód běží. Všechna další sestavení načtená v této aplikační doméně cílí na verzi. Například v případě spustitelného souboru je verze, kterou spustitelný soubor cílí, režim kompatibility všechna sestavení v dané doméně aplikace běží pod.

Pokud chcete zobrazit seznam změn za běhu, které se vztahují k vašemu prostředí, vyberte verzi .NET Framework, na kterou aktuálně cílíte, a pak verzi, na kterou chcete migrovat:

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Změny cíle

Změny cíle se projeví, když se sestavení znovu zkompiluje do cíle novější verze. Cílení na novější verzi znamená, že se sestavení výslovný do nových funkcí a také potenciální problémy s kompatibilitou pro staré funkce.

Pokud chcete zobrazit seznam změn cíle, které se vztahují k vašemu prostředí, vyberte verzi .NET Framework, na kterou aktuálně cílíte, a pak verzi, na kterou chcete migrovat:

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Klasifikace dopadu

V tématech popisujících modul runtime a změny cíle, například změny [cíle pro migraci z 4.7.2 na 4,8](retargeting/4.7.2-4.8.md), jednotlivé položky jsou klasifikovány podle očekávaného dopadu následujícím způsobem:

**Hlavní** \
Významná změna, která má vliv na velký počet aplikací nebo která vyžaduje podstatnou úpravu kódu.

**Vedlejší**\
Změna, která má vliv na malý počet aplikací nebo které vyžadují menší úpravu kódu.

\ **okrajového případu**
Změna ovlivňující aplikace v rámci velmi specifických scénářů, které nejsou běžné.

**Transparentní**\
Změna, která nemá znatelný vliv na vývojáře nebo uživatele aplikace. Z důvodu této změny by aplikace neměla vyžadovat úpravy.

## <a name="see-also"></a>Viz také:

- [Verze a závislosti](versions-and-dependencies.md)
- [Co je nového](../whats-new/index.md)
- [Zastaralé položky](../whats-new/whats-obsolete.md)
