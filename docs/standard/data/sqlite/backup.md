---
title: Online zálohování
ms.date: 12/13/2019
description: Naučte se používat funkci online zálohování SQLite.
ms.openlocfilehash: d857dcb69f2b2d10b034a0abf222b30c2e20bb41
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901285"
---
# <a name="online-backup"></a>Online zálohování

SQLite může zálohovat soubory databáze, když je aplikace spuštěná. Tato funkce je k dispozici v Microsoft. data. sqlite <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> jako metoda `SqliteConnection`na.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

V současné `BackupDatabase` době bude databáze zálohována co nejrychleji a zablokuje další připojení z zápisu do databáze. Problém [#13834](https://github.com/dotnet/efcore/issues/13834) by poskytoval alternativní rozhraní API pro zálohování databáze na pozadí a povolení dalších připojení k přerušení zálohování a zápisu do databáze. Pokud vás zajímá, poskytněte nám svůj názor na problém.
