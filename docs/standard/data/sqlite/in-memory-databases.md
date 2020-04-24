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

Databáze v paměti v paměti jsou databáze uložené výhradně v paměti, nikoli na disku. K vytvoření databáze v paměti použijte `:memory:` speciální název souboru zdroje dat. Po zavření připojení se databáze odstraní. Při použití `:memory:`aplikace vytvoří každé připojení vlastní databázi.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Sdílené databáze v paměti

Databáze v paměti lze sdílet mezi více připojeními pomocí `Mode=Memory` a `Cache=Shared` v připojovacím řetězci. `Data Source` Klíčové slovo slouží k poskytnutí názvu databáze v paměti. Připojovací řetězce používající stejný název budou přistupovat ke stejné databázi v paměti. Databáze zůstane v otevřeném umístění, dokud není otevřeno alespoň jedno připojení. [Ukázka](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) , která demonstruje tuto hodnotu, je k dispozici na GitHubu.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
