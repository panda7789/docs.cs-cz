---
title: 'C# vyhrazené atributy: Globální atributy'
ms.date: 04/09/2020
description: Atributy poskytují metadata, která kompilátor používá k pochopení další sémantiky programu.
ms.openlocfilehash: f855f32cd7349da34ffbd20fededdf42c3023938
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389854"
---
# <a name="reserved-attributes-assembly-level-attributes"></a>Vyhrazené atributy: Atributy úrovně sestavení

Většina atributů je použita pro určité jazykové prvky, jako jsou třídy nebo metody; některé atributy jsou však globální – platí pro celé sestavení nebo modul. <xref:System.Reflection.AssemblyVersionAttribute> Atribut lze například použít k vložení informací o verzi do sestavení, například takto:

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
```

Globální atributy se zobrazí ve zdrojovém kódu za všechny direktivy nejvyšší úrovně `using` a před jakýmkoli typem, modulem nebo deklaracemi oboru názvů. Globální atributy se mohou objevit ve více zdrojových souborech, ale soubory musí být zkompilovány v jednom průchodu kompilace. Visual Studio přidává globální atributy do souboru AssemblyInfo.cs v projektech rozhraní .NET Framework. Tyto atributy nejsou přidány do projektů .NET Core.

Atributy sestavení jsou hodnoty, které poskytují informace o sestavení. Spadají do následujících kategorií:

- Atributy identity sestavení
- Informační atributy
- Atributy manifestu sestavení

## <a name="assembly-identity-attributes"></a>Atributy identity sestavení

Identitu sestavení určují tři atributy (případně se silným názvem) název sestavení: název, verze a jazyková verze. Tyto atributy tvoří úplný název sestavení a jsou vyžadovány, když na něj odkazujete v kódu. Můžete nastavit verzi sestavení a jazykovou verzi pomocí atributů. Hodnota názvu je však nastavena kompilátorem, ide sady Visual Studio v [dialogovém okně informace o sestavení](/visualstudio/ide/reference/assembly-information-dialog-box)nebo propojovacím zařízení sestavení (Al.exe) při vytvoření sestavení. Název sestavení je založen na manifestu sestavení. Atribut <xref:System.Reflection.AssemblyFlagsAttribute> určuje, zda může existovat více kopií sestavení.

V následující tabulce jsou uvedeny atributy identity.

|Atribut|Účel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyVersionAttribute>|Určuje verzi sestavení.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Určuje, kterou jazykovou verzi sestavení podporuje.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Určuje, zda sestavení podporuje souběžné spuštění ve stejném počítači, ve stejném procesu nebo ve stejné doméně aplikace.|

## <a name="informational-attributes"></a>Informační atributy

Informační atributy slouží k poskytnutí dalších informací o společnosti nebo produktu pro sestavení. V následující tabulce jsou uvedeny informační <xref:System.Reflection?displayProperty=nameWithType> atributy definované v oboru názvů.

|Atribut|Účel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Určuje název produktu manifestu sestavení.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Určuje ochrannou známku manifestu sestavení.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Určuje informační verzi manifestu sestavení.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Určuje název společnosti manifestu sestavení.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definuje vlastní atribut, který určuje autorská práva pro manifest sestavení.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Nastaví konkrétní číslo verze pro prostředek verze souboru Win32.|
|<xref:System.CLSCompliantAttribute>|Označuje, zda je sestavení kompatibilní se specifikací CLS (Common Language Specification).|

## <a name="assembly-manifest-attributes"></a>Atributy manifestu sestavení

Atributy manifestu sestavení můžete použít k poskytnutí informací v manifestu sestavení. Atributy zahrnují název, popis, výchozí alias a konfiguraci. V následující tabulce jsou uvedeny atributy manifestu sestavení definované v oboru <xref:System.Reflection?displayProperty=nameWithType> názvů.

|Atribut|Účel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Určuje název sestavení manifestu sestavení.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Určuje popis sestavení manifestu sestavení.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Určuje konfiguraci sestavení (například maloobchodní nebo ladicí) pro manifest sestavení.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definuje popisný výchozí alias pro manifest sestavení.|
