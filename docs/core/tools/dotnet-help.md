---
title: dotnet – příkaz helpu
description: Příkaz dotnet Help zobrazuje podrobnější dokumentaci k uvedenému příkazu v online režimu.
ms.date: 08/08/2019
ms.openlocfilehash: 533f2c47fa7ec14d31368538092fec2490234820
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117714"
---
# <a name="dotnet-help-reference"></a>Referenční dokumentace k dotnet

**Tento článek se týká: ✓** .net Core 2,0 SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a>Name

`dotnet help`– Zobrazí podrobnější dokumentaci k určitému příkazu online.

## <a name="synopsis"></a>Stručný obsah

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Popis

`dotnet help` Příkaz otevře referenční stránku, kde najdete podrobnější informace o zadaném příkazu na adrese docs.Microsoft.com.

## <a name="arguments"></a>Arguments

* **`COMMAND_NAME`**

  Název .NET Core CLI příkazu Seznam platných příkazů rozhraní příkazového řádku najdete v tématu [příkazy rozhraní příkazového řádku](index.md#cli-commands).

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

## <a name="examples"></a>Příklady

* Otevře stránku dokumentace pro příkaz [dotnet New](dotnet-new.md) :

  ```dotnetcli
  dotnet help new
  ```
