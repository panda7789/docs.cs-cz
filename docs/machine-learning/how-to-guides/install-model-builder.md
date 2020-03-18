---
title: Jak nainstalovat Tvůrce modelů
description: Přečtěte si, jak nainstalovat nástroj ML.NET Tvůrce modelů
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848649"
---
# <a name="how-to-install-mlnet-model-builder"></a>Jak nainstalovat ML.NET Tvůrce modelů

Přečtěte si, jak nainstalovat ML.NET Tvůrce modelů a přidat strojové učení do aplikací .NET.

> [!NOTE]
> Tvůrce modelů je momentálně ve verzi Preview.

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 verze 15.9.12 nebo novější / Visual Studio 2019
- Sada .NET Core 2.1 SDK nebo novější.

> [!NOTE]
> Sada .NET Core 3.0 SDK není aktuálně podporována.

## <a name="limitations"></a>Omezení

- ML.NET rozšíření Model Builder aktuálně funguje pouze v sadě Visual Studio v systému Windows.
- Trénovací datový set limit 1 GB
- SQL Server má limit 100 tisíc řádků pro školení
- Datové nástroje serveru Microsoft SQL Server pro Visual Studio 2017 nejsou podporovány.

## <a name="install"></a>Instalace

ML.NET model tvůrce lze nainstalovat buď prostřednictvím Webu Visual Studio Marketplace nebo z Visual Studio.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. Stažení z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Instalace do příslušné verze sady Visual Studio navazují na výzvy

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. V řádku nabídek vyberte**Rozšíření a aktualizace** **nástrojů.** > 

    ![Dialogové okno Správce otevřených rozšíření VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. Uvnitř výzvy *Rozšíření a Aktualizace* vyberte online uzel. *Online*
1. Na vyhledávacím panelu vyhledejte *ML.NET Tvůrce modelů* a z výsledků vyberte ML.NET Tvůrce modelů (Preview).

    ![VS2017 vyhledává a instaluje rozšíření Tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2017-install-model-builder.png)

1. Dokončete instalaci podle pokynů.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na řádku nabídek vyberte **Rozšíření** > **Spravovat rozšíření.**

    ![Dialogové okno Správce otevřených rozšíření VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. Uvnitř výzvy *Rozšíření a Aktualizace* vyberte online uzel. *Online*
1. Zadejte *ML.NET Tvůrce modelů* do vyhledávacího panelu vyberte ML.NET Tvůrce modelů (Náhled)

    ![VS2019 vyhledává a instaluje rozšíření Tvůrce modelů v dialogovém okně Správce rozšíření](./media/install-model-builder/vs2019-install-model-builder.png)

1. Dokončete instalaci podle pokynů.

## <a name="uninstall"></a>Odinstalace

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na řádku nabídek vyberte**Rozšíření a aktualizace** **nástrojů.** > 

    ![Dialogové okno Otevřít rozšíření v správě VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. V rámci výzvy *Rozšíření a Aktualizace* rozbalte *nainstalovaný* uzel a vyberte *Nástroje.*
1. Vyberte ML.NET Tvůrce modelů (Preview) ze seznamu nástrojů a pak vyberte *Odinstalovat*

    ![VS2017 vyhledávání a odinstalovat rozšíření Model Builder v dialogovém okně správce rozšíření](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Podle pokynů dokončete odinstalaci.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na řádku nabídek vyberte **Rozšíření** > **Spravovat rozšíření.**

    ![Dialogové okno Otevřít rozšíření v Správě VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. V rámci výzvy *Rozšíření a Aktualizace* rozbalte *nainstalovaný* uzel a vyberte *Nástroje.*
1. Vyberte ML.NET Tvůrce modelů (Preview) ze seznamu nástrojů a pak vyberte *Odinstalovat*

    ![VS2019 vyhledávání a odinstalovat rozšíření Model Builder v dialogovém okně správce rozšíření](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Podle pokynů dokončete odinstalaci.

## <a name="upgrade"></a>Upgrade

Proces upgradu je podobný procesu instalace. Stáhněte si nejnovější verzi z webu Visual Studio Marketplace nebo použijte Správce rozšíření v sadě Visual Studio.
