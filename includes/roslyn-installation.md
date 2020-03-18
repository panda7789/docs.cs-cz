---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "72526738"
---
## <a name="installation-instructions---visual-studio-installer"></a>Pokyny k instalaci – Instalační služba sady Visual Studio

Existují dva různé způsoby, jak najít **sdk platformy kompilátoru .NET** v **Instalační službě sady Visual Studio**:

### <a name="install-using-the-visual-studio-installer---workloads-view"></a>Instalace pomocí instalačního programu sady Visual Studio – zobrazení úloh

Sada SDK platformy kompilátoru .NET není automaticky vybrána jako součást vývojového zatížení rozšíření sady Visual Studio. Je nutné ji vybrat jako volitelnou součást.

1. Spuštění **instalačního programu sady Visual Studio**
1. Vybrat **změnit**
1. Zkontrolujte zatížení **vývoje rozšíření Visual Studio.**
1. Otevřete uzel **vývoje rozšíření Visual Studio** ve stromu souhrnu.
1. Zaškrtněte políčko **u sady .NET Compiler Platform SDK**. Najdete ji jako poslední pod volitelnými součástmi.

Volitelně budete také chtít, aby **editor DGML** zobrazoval grafy ve vizualizéru:

1. Otevřete uzel **jednotlivých komponent** ve stromu souhrnu.
1. Zaškrtněte políčko **pro editor DGML**

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a>Instalace pomocí karty Instalační služba sady Visual Studio – jednotlivé součásti

1. Spuštění **instalačního programu sady Visual Studio**
1. Vybrat **změnit**
1. Výběr karty **Jednotlivé komponenty**
1. Zaškrtněte políčko **u sady .NET Compiler Platform SDK**. Najdete ji v horní části **kompilátory, vytvářet nástroje a runtimes** části.

Volitelně budete také chtít, aby **editor DGML** zobrazoval grafy ve vizualizéru:

1. Zaškrtněte políčko **pro editor DGML**. Najdete ji v části **Nástroje kódu.**
