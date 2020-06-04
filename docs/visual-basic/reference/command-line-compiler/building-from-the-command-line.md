---
title: Sestavení z příkazového řádku
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: ec6ae3328c2042af950d1ee78a33d3de97219f10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414295"
---
# <a name="building-from-the-command-line-visual-basic"></a>Sestavení z příkazového řádku (Visual Basic)

Visual Basic projekt se skládá z jednoho nebo více samostatných zdrojových souborů. Během procesu známého jako kompilace jsou tyto soubory společně umístěny do jednoho balíčku – jeden spustitelný soubor, který lze spustit jako aplikaci.

Visual Basic poskytuje kompilátor příkazového řádku jako alternativu k kompilování programů z integrovaného vývojového prostředí (IDE) sady Visual Studio. Kompilátor příkazového řádku je určený pro situace, kdy nevyžadujete úplnou sadu funkcí v rozhraní IDE – například při použití nebo psaní počítačů s omezeným systémovou pamětí nebo prostorem úložiště.

Chcete-li kompilovat zdrojové soubory z integrovaného vývojového prostředí sady Visual Studio, v nabídce **sestavení** klikněte na příkaz **sestavit** .

> [!TIP]
> Při sestavování souborů projektu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio můžete zobrazit informace o přidruženém příkazu **Vbc** a jeho přepínačích v okně výstup. Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavte a spusťte](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **Podrobnosti výstupu sestavení projektu MSBuild** na **normální** nebo vyšší úroveň podrobností. Další informace najdete v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).

Soubory projektu (. vbproj) můžete kompilovat na příkazovém řádku pomocí nástroje MSBuild. Další informace naleznete v tématu [Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference) a [Návod: použití nástroje MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: volání kompilátoru příkazového řádku](how-to-invoke-the-command-line-compiler.md) \
Popisuje, jak vyvolat kompilátor příkazového řádku v příkazovém řádku systému MS-DOS nebo z konkrétního podadresáře.

[Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md) \
Poskytuje seznam ukázkových příkazových řádků, které můžete upravit pro vlastní použití.

## <a name="related-sections"></a>Související oddíly

[Visual Basic Kompilátor příkazového řádku](index.md) \
Obsahuje seznam možností kompilátoru uspořádaných podle abecedy nebo podle účelu.

[Podmíněná kompilace](../../programming-guide/program-structure/conditional-compilation.md) \
Popisuje, jak zkompilovat konkrétní oddíly kódu.

[Sestavování a čištění projektů a řešení v aplikaci Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
Popisuje, jak uspořádat, co bude zahrnuto v různých sestaveních, zvolit vlastnosti projektu a zajistit, aby se projekty vytvořily ve správném pořadí.
