---
title: Instalace Tvůrce modelu
description: Zjistěte, jak nainstalovat nástroj Tvůrce modelu ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410650"
---
# <a name="how-to-install-mlnet-model-builder"></a>Instalace Tvůrce modelu ML.NET

Zjistěte, jak nainstalovat Tvůrce modelu ML.NET přidání machine learningu do aplikací .NET.

> [!NOTE]
> Tvůrce modelu je aktuálně ve verzi Preview.

## <a name="pre-requisites"></a>Požadavky

- Visual Studio 2017 15.9.12 nebo vyšší / Visual Studio. 2019
- .NET core 2.1 nebo novější sady SDK

## <a name="limitations"></a>Omezení

- Rozšíření Tvůrce modelu ML.NET aktuálně funguje pouze v sadě Visual Studio na Windows.
- Trénovací datové sady limit 1GB
- SQL Server má limit 100 tisíc řádků pro školení
- Microsoft SQL Server Data Tools pro Visual Studio 2017 se nepodporuje.

## <a name="install"></a>Instalace

Tvůrce modelu ML.NET se dají nainstalovat přes Visual Studio Marketplace nebo v rámci sady Visual Studio. 

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. Stáhnout z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Postupujte podle pokynů k instalaci na příslušnou verzi sady Visual Studio

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. V panelu nabídek vyberte **nástroje** > **rozšíření a aktualizace**
1. Uvnitř *rozšíření a aktualizace* příkazový řádek, vyberte *Online* uzlu.
1. Na panelu hledání vyhledejte *Tvůrce modelu ML.NET* a ve výsledcích vyberte ML.NET Tvůrce modelu (Preview)
1. Postupujte podle pokynů k dokončení instalace

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na panelu nabídek vyberte **rozšíření** > **spravovat rozšíření**
1. Uvnitř *rozšíření a aktualizace* příkazový řádek, vyberte *Online* uzlu.
1. Typ *Tvůrce modelu ML.NET* do panelu vyhledávání vyberte ML.NET Tvůrce modelu (Preview)
1. Postupujte podle pokynů k dokončení instalace

## <a name="uninstall"></a>Odinstalovat

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na panelu nabídek vyberte **nástroje** > **rozšíření a aktualizace**
1. Uvnitř *rozšíření a aktualizace* výzvu, rozbalte *nainstalováno* uzel a vyberte možnost *nástroje*
1. Ze seznamu nástrojů vyberte ML.NET Tvůrce modelu (Preview) a pak vyberte *odinstalace*
1. Postupujte podle pokynů k dokončení odinstalace.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na panelu nabídek vyberte **rozšíření** > **spravovat rozšíření**
1. Uvnitř *rozšíření a aktualizace* výzvu, rozbalte *nainstalováno* uzel a vyberte možnost *nástroje*
1. Ze seznamu nástrojů vyberte ML.NET Tvůrce modelu (Preview) a pak vyberte *odinstalace*
1. Postupujte podle pokynů k dokončení odinstalace.

## <a name="upgrade"></a>Upgrade

Proces upgradu je podobný procesu instalace. Stáhněte si nejnovější verzi z webu Visual Studio Marketplace nebo pomocí Správce rozšíření v sadě Visual Studio.
