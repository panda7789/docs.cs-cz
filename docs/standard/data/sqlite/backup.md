---
title: Online zálohování
ms.date: 12/13/2019
description: Naučte se používat funkci online zálohování SQLite.
ms.openlocfilehash: 885aa2c5555b58deb2551c0a4e6933742a093457
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447095"
---
# <a name="online-backup"></a>Online zálohování

SQLite může zálohovat soubory databáze, když je aplikace spuštěná. Tato funkce je k dispozici v Microsoft. data. sqlite jako metoda <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> v `SqliteConnection`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

V současné době `BackupDatabase` zálohuje databázi co nejrychleji a zablokuje další připojení pro zápis do databáze. Problém [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) by poskytoval alternativní rozhraní API pro zálohování databáze na pozadí a povolení dalších připojení k přerušení zálohování a zápisu do databáze. Pokud vás zajímá, poskytněte nám svůj názor na problém.
