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
# <a name="online-backup"></a><span data-ttu-id="a9609-103">Online zálohování</span><span class="sxs-lookup"><span data-stu-id="a9609-103">Online backup</span></span>

<span data-ttu-id="a9609-104">SQLite může zálohovat soubory databáze, když je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="a9609-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="a9609-105">Tato funkce je k dispozici v Microsoft. data. sqlite jako metoda <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> v `SqliteConnection`.</span><span class="sxs-lookup"><span data-stu-id="a9609-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="a9609-106">V současné době `BackupDatabase` zálohuje databázi co nejrychleji a zablokuje další připojení pro zápis do databáze.</span><span class="sxs-lookup"><span data-stu-id="a9609-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="a9609-107">Problém [#13834](https://github.com/dotnet/efcore/issues/13834) by poskytoval alternativní rozhraní API pro zálohování databáze na pozadí a povolení dalších připojení k přerušení zálohování a zápisu do databáze.</span><span class="sxs-lookup"><span data-stu-id="a9609-107">Issue [#13834](https://github.com/dotnet/efcore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="a9609-108">Pokud vás zajímá, poskytněte nám svůj názor na problém.</span><span class="sxs-lookup"><span data-stu-id="a9609-108">If you're interested, provide feedback on the issue.</span></span>
