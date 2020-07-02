---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619984"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Chybějící zástupný název rozhraní Target Framework má za následek 4,0 chování.

#### <a name="details"></a>Podrobnosti

Aplikace bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> použití na úrovni sestavení se automaticky spustí pomocí sémantiky (adaptivní) .NET Framework 4,0. Aby se zajistila vysoká kvalita, doporučujeme, aby všechny binární soubory byly explicitně přiděleny s <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> označením verze .NET Framework, se kterou byly vytvořeny. Všimněte si, že použití monikeru cílového rozhraní v souboru projektu způsobí, že nástroj MSBuild automaticky použije <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> .

#### <a name="suggestion"></a>Návrh

<xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>Měla by být zadána buď prostřednictvím přidání atributu přímo do sestavení, nebo zadáním cílové architektury v [souboru projektu nebo pomocí grafického uživatelského rozhraní Visual Studio vlastností projektu](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4.5|
|Typ|Modul runtime|
