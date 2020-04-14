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

SQLite podporuje načítání rozšíření za běhu. Rozšíření zahrnují například další funkce SQL, kolace, virtuální tabulky a další.

.NET Core obsahuje další logiku pro vyhledání nativních knihoven na dalších místech, jako jsou odkazované balíčky NuGet. Bohužel, SQLite nemůže využít tuto logiku; volá rozhraní API platformy přímo k načtení knihoven. Z tohoto důvodu může být nutné upravit path, LD_LIBRARY_PATH nebo DYLD_LIBRARY_PATH proměnné prostředí před načtením rozšíření SQLite. Existuje ukázka na [GitHubu,](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) která demonstruje hledání binárních souborů pro aktuální runtime uvnitř odkazované hobalíčku NuGet.

Chcete-li načíst <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> rozšíření, zavolejte metodu. Microsoft.Data.Sqlite zajistí, že rozšíření zůstane načteno i v případě, že je připojení uzavřeno a znovu otevřeno.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Viz také

* [Zaběhunatelná rozšíření](https://www.sqlite.org/loadext.html)
