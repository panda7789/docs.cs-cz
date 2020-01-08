---
title: Rozšíření
ms.date: 12/13/2019
description: Přečtěte si, jak načíst rozšíření SQLite.
ms.openlocfilehash: ab00ccf31b8a22407fc177c18149fe4825a19091
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447256"
---
# <a name="extensions"></a>Rozšíření

SQLite podporuje načítání rozšíření v době běhu. Mezi přípony patří například další funkce SQL, kolace, virtuální tabulky a další.

.NET Core zahrnuje další logiku pro vyhledání nativních knihoven na dalších místech, jako jsou odkazované balíčky NuGet. Omlouváme se, ale SQLite nemůže tuto logiku využít; volá rozhraní API platformy přímo k načtení knihoven. Z tohoto důvodu může vaše aplikace před načtením rozšíření SQLite potřebovat změnit cestu, LD_LIBRARY_PATH nebo DYLD_LIBRARY_PATH proměnných prostředí. Na GitHubu je [Ukázka](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) , která ukazuje nalezení binárních souborů pro aktuální modul runtime v rámci odkazovaného balíčku NuGet.

Chcete-li načíst rozšíření, zavolejte metodu <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>. Microsoft. data. sqlite zajistí, že rozšíření zůstane načteno i v případě, že je připojení zavřeno a znovu otevřeno.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Viz také:

* [Spustitelný rozšíření běhu](https://www.sqlite.org/loadext.html)
