---
ms.openlocfilehash: 29b8feb7959c718391b963c8402b97351b93fa49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803637"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Chybějící Moniker cílového rozhraní za následek 4.0 chování

|   |   |
|---|---|
|Podrobnosti|Aplikace bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> aplikována na úrovni se sestavení automaticky spustit pomocí sémantiky (adaptivní) rozhraní .NET Framework 4.0. K zajištění vysoce kvalitní, se doporučuje, aby všechny binární soubory explicitně přiřadit s <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> označující verzi rozhraní .NET Framework, kterými byly vytvořeny. Všimněte si, že pomocí moniker cílového rozhraní v souboru projektu způsobí, že nástroj MSBuild pro automatické použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>.|
|Doporučení|A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> by měl být zadán, buď přidat atribut přímo do sestavení nebo zadáním v rozhraní .NET framework [souboru projektu nebo pomocí sady Visual Studio projekt vlastnosti grafického uživatelského rozhraní](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).|
|Rozsah|Hlavní|
|Version|4.5|
|Type|Modul runtime|
