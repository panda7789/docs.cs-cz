---
title: Databáze v paměti
ms.date: 12/13/2019
description: Naučte se používat databáze SQLite v paměti.
ms.openlocfilehash: b125ff5aa4128bd4c3ff558c5573b7d11802090a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447242"
---
# <a name="in-memory-databases"></a>Databáze v paměti

Databáze v paměti v paměti jsou databáze uložené výhradně v paměti, nikoli na disku. K vytvoření databáze v paměti použijte `:memory:` speciální název souboru zdroje dat. Po zavření připojení se databáze odstraní. Při použití `:memory:`vytvoří každé připojení svou vlastní databázi.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Sdílené databáze v paměti

Databáze v paměti lze sdílet mezi více připojeními pomocí `Mode=Memory` a `Cache=Shared` v připojovacím řetězci. Klíčové slovo `Data Source` slouží k poskytnutí názvu databáze v paměti. Připojovací řetězce používající stejný název budou přistupovat ke stejné databázi v paměti. Databáze zůstane v otevřeném umístění, dokud není otevřeno alespoň jedno připojení. [Ukázka](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) , která demonstruje tuto hodnotu, je k dispozici na GitHubu.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
