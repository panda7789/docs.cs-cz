---
title: Jak nainstalovat Tvůrce modelů
description: Zjistěte, jak nainstalovat nástroj ML.NET model Builder.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b0d45ab7807bf84b98c58e85580d5aa04d0c5f7d
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306329"
---
# <a name="how-to-install-mlnet-model-builder"></a>Postup instalace Tvůrce modelů ML.NET

Naučte se instalovat tvůrce modelů ML.NET a přidat do aplikací .NET strojové učení.

> [!NOTE]
> Tvůrce modelů je aktuálně ve verzi Preview.

## <a name="pre-requisites"></a>Požadavky

- Visual Studio 2017 15.9.12 nebo novější/Visual Studio 2019
- Sada .NET Core 2,1 nebo novější SDK

## <a name="limitations"></a>Omezení

- Rozšíření tvůrce modelů ML.NET je aktuálně funguje pouze v sadě Visual Studio ve Windows.
- Školení pro datovou sadu o velikosti 1 GB
- SQL Server má limit 100 000 řádků pro školení
- Microsoft SQL Server Data Tools for Visual Studio 2017 se nepodporuje.

## <a name="install"></a>Instalace

Tvůrce modelů ML.NET se dá nainstalovat buď prostřednictvím Visual Studio Marketplace, nebo v sadě Visual Studio. 

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. Stáhnout z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Podle zobrazených výzev nainstalujte do příslušné verze sady Visual Studio.

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. V řádku nabídek vyberte rozšíření **nástrojů** > **a aktualizace** .

    ![Dialogové okno VS2017 Open Extensions Manager](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. V okně s výzvou k *rozšíření a aktualizaci* vyberte *online* uzel.
1. Na panelu hledání vyhledejte *Tvůrce modelů ml.NET* a z výsledků vyberte ml.NET model Builder (Preview).

    ![VS2017 vyhledat a nainstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2017-install-model-builder.png)

1. Podle pokynů dokončete instalaci.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na panelu nabídek vyberte **rozšíření** > **Spravovat rozšíření** .

    ![Dialogové okno VS2019 Open Extensions Manager](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. V okně s výzvou k *rozšíření a aktualizaci* vyberte *online* uzel.
1. Do panelu hledání zadejte *ml.NET model Builder* , vyberte ml.NET model Builder (Preview).

    ![VS2019 vyhledat a nainstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2019-install-model-builder.png)

1. Podle pokynů dokončete instalaci.

## <a name="uninstall"></a>Odinstalovat

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na řádku nabídek vyberte rozšíření **nástrojů** > **a aktualizace** .

    ![VS2017 otevřít dialogové okno Správa rozšíření](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. V příkazovém řádku *rozšíření a aktualizace* rozbalte *nainstalovaný* uzel a vyberte *nástroje* .
1. V seznamu nástrojů vyberte Tvůrce modelů ML.NET (Preview) a pak vyberte *odinstalovat* .

    ![VS2017 vyhledat a odinstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Dokončete odinstalaci podle pokynů.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na panelu nabídek vyberte **rozšíření** > **Spravovat rozšíření** .

    ![VS2019 otevřít dialogové okno Správa rozšíření](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. V příkazovém řádku *rozšíření a aktualizace* rozbalte *nainstalovaný* uzel a vyberte *nástroje* .
1. V seznamu nástrojů vyberte Tvůrce modelů ML.NET (Preview) a pak vyberte *odinstalovat* .

    ![VS2019 vyhledat a odinstalovat rozšíření tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Dokončete odinstalaci podle pokynů.

## <a name="upgrade"></a>Přejít

Proces upgradu je podobný procesu instalace. Buď si stáhněte nejnovější verzi z Visual Studio Marketplace nebo použijte Správce rozšíření v aplikaci Visual Studio.
