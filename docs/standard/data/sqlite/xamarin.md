---
title: Omezení Xamarin
ms.date: 12/13/2019
description: Popisuje některá omezení, která se objeví při použití Xamarin.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447165"
---
# <a name="xamarin-limitations"></a>Omezení Xamarin

Microsoft. data. sqlite cílí .NET Standard 2,0 a jsou podporovány v Xamarin. Následující tabulka ukazuje, které platformy výchozí sada SQLitePCLRaw poskytuje nativní binární soubory SQLite pro. Podrobnosti o používání jiné sady prostředků nebo poskytování vlastních nativních binárních souborů SQLite najdete v tématu [vlastní verze SQLite](custom-versions.md) .

| Platforma | Binární soubory SQLite |
| --- | --- |
| **Xamarin.Android** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | ✔ |
| **Xamarin.iOS** | ✔ |
| **Xamarin.Mac** | ✔ |
| **Xamarin. TVOS** | ✔ |
| **UPW** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |

## <a name="ios"></a>iOS

Microsoft. data. sqlite se pokusí automaticky inicializovat sady SQLitePCLRaw. Vzhledem k tomu, že došlo k omezení kompilace v předstihu (AOT) pro Xamarin. iOS, pokus se nezdaří a zobrazí se následující chyba.

> Musíte volat `SQLitePCL.raw.SetProvider()`. Pokud používáte balíček sady prostředků, je to provedeno voláním `SQLitePCL.Batteries.Init()`.

Pro inicializaci sady přidejte do aplikace následující řádek kódu před použitím Microsoft. data. sqlite.

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a>Viz také:

* [Asynchronní omezení](async.md)
* [Vlastní verze SQLite](custom-versions.md)
