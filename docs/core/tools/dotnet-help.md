---
title: příkaz DotNet nápovědy
description: Příkaz dotnet help Zobrazí podrobnější online dokumentaci pro zadaný příkaz.
ms.date: 12/04/2018
ms.openlocfilehash: 44274b698ed83bd3cdb58787f433eeb5c555bc6d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168948"
---
# <a name="dotnet-help-reference"></a>odkaz na nápovědu DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Název

`dotnet help` – Zobrazí podrobnější online dokumentaci pro zadaný příkaz.

## <a name="synopsis"></a>Souhrn

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Popis

`dotnet help` Příkaz otevře stránku pro odkaz na podrobné informace o zadaném příkazu na webu docs.microsoft.com.

## <a name="arguments"></a>Arguments

* **`COMMAND_NAME`**

  Název příkazu rozhraní příkazového řádku .NET Core. Seznam platných příkazů rozhraní příkazového řádku najdete v tématu [příkazy rozhraní příkazového řádku](index.md#cli-commands).

## <a name="options"></a>Možnosti

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

## <a name="examples"></a>Příklady

* Otevře se stránka dokumentace pro [dotnet nové](dotnet-new.md) příkaz:

  ```console
  dotnet help new
  ```