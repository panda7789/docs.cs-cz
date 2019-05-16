---
title: příkaz DotNet nápovědy
description: Příkaz dotnet help Zobrazí podrobnější online dokumentaci pro zadaný příkaz.
ms.date: 12/04/2018
ms.openlocfilehash: 8694494720cdb9a540754fdf79eeb99d5dbe61ef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631990"
---
# <a name="dotnet-help-reference"></a>odkaz na nápovědu DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Name

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
