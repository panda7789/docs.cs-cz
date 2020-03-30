---
title: Databáze v paměti
ms.date: 12/13/2019
description: Naučte se používat databáze SQLite v paměti.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391205"
---
# <a name="in-memory-databases"></a>Databáze v paměti

SQLite v paměti databáze jsou databáze uložené výhradně v paměti, nikoli na disku. Použijte název souboru `:memory:` zdroje dat speciální zdroj dat k vytvoření databáze v paměti. Po zavření připojení je databáze odstraněna. Při `:memory:`použití vytvoří každé připojení vlastní databázi.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Sdílet databáze v paměti

Databáze v paměti lze sdílet mezi více `Mode=Memory` `Cache=Shared` připojení pomocí a v připojovacím řetězci. Klíčové `Data Source` slovo se používá k tomu, aby databáze v paměti pojmenovala. Připojovací řetězce se stejným názvem budou mít přístup ke stejné databázi v paměti. Databáze zůstane zachována tak dlouho, dokud alespoň jedno připojení k ní zůstane otevřené. [Ukázka](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) prokazující to je k dispozici na GitHubu.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
