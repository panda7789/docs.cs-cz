---
title: dotnet – příkaz helpu
description: Příkaz dotnet Help zobrazuje podrobnější dokumentaci k uvedenému příkazu v online režimu.
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503727"
---
# <a name="dotnet-help-reference"></a>Referenční dokumentace k dotnet

**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet help` – Zobrazí podrobnější dokumentaci k určitému příkazu online.

## <a name="synopsis"></a>Stručný obsah

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Popis

Příkaz `dotnet help` otevře referenční stránku, kde najdete podrobnější informace o zadaném příkazu na adrese docs.microsoft.com.

## <a name="arguments"></a>Argumenty

- **`COMMAND_NAME`**

  Název .NET Core CLI příkazu Seznam platných příkazů rozhraní příkazového řádku najdete v tématu [příkazy rozhraní příkazového řádku](index.md#cli-commands).

## <a name="options"></a>Možnosti

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

## <a name="examples"></a>Příklady

- Otevře stránku dokumentace pro příkaz [dotnet New](dotnet-new.md) :

  ```dotnetcli
  dotnet help new
  ```
