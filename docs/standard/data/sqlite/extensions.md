---
title: Rozšíření
ms.date: 12/13/2019
description: Přečtěte si, jak načíst rozšíření SQLite.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242956"
---
# <a name="extensions"></a>Rozšíření

SQLite podporuje načítání rozšíření v době běhu. Mezi přípony patří například další funkce SQL, kolace, virtuální tabulky a další.

.NET Core zahrnuje další logiku pro vyhledání nativních knihoven na dalších místech, jako jsou odkazované balíčky NuGet. Omlouváme se, ale SQLite nemůže tuto logiku využít; volá rozhraní API platformy přímo k načtení knihoven. Z tohoto důvodu může být nutné před načtením rozšíření SQLite změnit cestu, LD_LIBRARY_PATH nebo DYLD_LIBRARY_PATH proměnných prostředí. Na GitHubu je [Ukázka](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) , která ukazuje nalezení binárních souborů pro aktuální modul runtime v rámci odkazovaného balíčku NuGet.

Chcete-li načíst rozšíření, zavolejte <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> metodu. Microsoft. data. sqlite zajistí, že rozšíření zůstane načteno i v případě, že je připojení zavřeno a znovu otevřeno.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Viz také

* [Spustitelný rozšíření běhu](https://www.sqlite.org/loadext.html)
