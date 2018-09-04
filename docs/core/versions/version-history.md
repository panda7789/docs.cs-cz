---
title: Historie verzí .NET core
description: Zobrazit časovou osu pro verze modulu runtime .NET Core, .NET Core SDK, kompilátor jazyka C# a VB.NET kompilátoru.
ms.date: 07/26/2018
ms.openlocfilehash: 90fd4ba57620a3a005f2148c0335a76a6fa54a30
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519062"
---
# <a name="net-core-version-history"></a>Historie verzí .NET Core

Čísla verzí pro .NET Core jsou náročná, protože sady SDK .NET Core a .NET Core Runtime vydání na jinou cadences. Různé cadences znamená, že tým musela být proveďte pouze dvě následující tři věci:

1. Verze nezávisle na sobě, konkrétně povolení nástrojů, C# a VB k přechodu rychleji než modul Runtime .NET Core.
2. Zachovat zarovnání v číslech verzí mezi .NET Core SDK a modulu Runtime .NET Core.
3. Sémantické správy verzí pomocí sady SDK .NET Core a .NET Core Runtime.

2.0.0 vynucené verze zarovnání a hladce pokračovat pro jednu verzi. V prosinci 2017 bylo .NET Core SDK verze funkce s žádná odpovídající verzi v modulu Runtime .NET Core. Tým si zvolila cíle 1 a 3, ztráty zarovnání mezi .NET Core Runtime a sadu SDK. Několik verzí .NET Core SDK 2.1.x byly vydané dřív než .NET Core Runtime 2.1. Vzhledem k tomu, že sada SDK není předává kompatibilní, tato verze sady SDK 2.1.x nelze cílit na .NET Core Runtime 2.1. Tým odpověděl na značné zmatek přepnutím do cíle 1 a 2, zrušení sémantické správy verzí, jak je popsáno v [správy verzí .NET Core](index.md#versioning-details).

Z důvodu načasování rozhodnutí spustit metodu Abandon sémantické správy verzí, došlo k přechodné vydané verze v 2.1.10x a 2.1.20x verze počet rozsahů, které také nelze cílit na .NET Core Runtime 2.1.

První dvě číslice čísla verzí-li zarovnat s 2.1.0 verzi modulu Runtime .NET Core a 2.1.300 verzi .NET Core SDK.

Podrobné informace o verzích jednotlivých komponent, včetně verzí kompilátoru jazyka a architektury, najdete na [stránky pro stažení rozhraní .NET Core](https://www.microsoft.com/net/download/dotnet-core/current). Podrobné informace o předchozích verzích, vyberte požadovanou verzi z [stáhnout .NET Core archivuje stránky](https://www.microsoft.com/net/download/archives). Podrobné informace najdete v článku s popisem official je přínosné pro [zásady podpory .NET](https://www.microsoft.com/net/Support/Policy).