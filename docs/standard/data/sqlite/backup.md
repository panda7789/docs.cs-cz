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
# <a name="online-backup"></a><span data-ttu-id="5be5e-103">Online zálohování</span><span class="sxs-lookup"><span data-stu-id="5be5e-103">Online backup</span></span>

<span data-ttu-id="5be5e-104">SQLite může zálohovat soubory databáze, když je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="5be5e-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="5be5e-105">Tato funkce je k dispozici v Microsoft. data. sqlite jako metoda <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> v `SqliteConnection`.</span><span class="sxs-lookup"><span data-stu-id="5be5e-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="5be5e-106">V současné době `BackupDatabase` zálohuje databázi co nejrychleji a zablokuje další připojení pro zápis do databáze.</span><span class="sxs-lookup"><span data-stu-id="5be5e-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="5be5e-107">Problém [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) by poskytoval alternativní rozhraní API pro zálohování databáze na pozadí a povolení dalších připojení k přerušení zálohování a zápisu do databáze.</span><span class="sxs-lookup"><span data-stu-id="5be5e-107">Issue [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="5be5e-108">Pokud vás zajímá, poskytněte nám svůj názor na problém.</span><span class="sxs-lookup"><span data-stu-id="5be5e-108">If you're interested, provide feedback on the issue.</span></span>
