---
title: dotnet – příkaz helpu
description: Příkaz dotnet Help zobrazuje podrobnější dokumentaci k uvedenému příkazu v online režimu.
ms.date: 08/08/2019
ms.openlocfilehash: 9bb4e54d2634c000707752edf53b38af43c4344e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734230"
---
# <a name="dotnet-help-reference"></a>Referenční dokumentace k dotnet

**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]
-->

## <a name="name"></a>Název

`dotnet help` – Zobrazí podrobnější dokumentaci k určitému příkazu online.

## <a name="synopsis"></a>Stručný obsah

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Popis

Příkaz `dotnet help` otevře referenční stránku, kde najdete podrobnější informace o zadaném příkazu na adrese docs.microsoft.com.

## <a name="arguments"></a>Argumenty

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
