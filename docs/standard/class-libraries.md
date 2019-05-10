---
title: Knihovny tříd .NET
description: Zjistěte, jak knihovny tříd .NET umožňují skupiny užitečné funkce do modulů, které mohou být využívána více aplikacemi.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: c918883d8620513749826680f9f1b6d89ae87585
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664605"
---
# <a name="net-class-libraries"></a>Knihovny tříd .NET

Knihovny tříd jsou [sdílenou knihovnu](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) konceptem pro .NET. Umožňují componentize užitečné funkce do modulů, které mohou být využívána více aplikacemi. Můžete se také používá jako způsob načítání funkcí, které se nevyžaduje nebo neznámý. při spuštění aplikace. Knihovny tříd jsou popsány pomocí [formát souborů sestavení .NET](assembly/file-format.md).

Existují tři typy knihoven tříd, které můžete použít:

* **Specifické pro platformu** knihovny tříd mají přístup ke všem rozhraním API v dané platformy (pro rozhraní .NET Framework, například Xamarin pro iOS), ale jde použít jenom aplikace a knihovny cílené na této platformě.
* **Přenosné** knihovny tříd mají přístup k podmnožinu rozhraní API a mohou využívat aplikace a knihovny cílené na více platforem.
* **.NET standard** knihovny tříd jsou spojení konceptů specifických pro platformu a přenosné knihovny do jednoho modelu, který poskytuje nejlepší z obou.

## <a name="platform-specific-class-libraries"></a>Knihovny tříd pro konkrétní platformu

Knihovny pro konkrétní platformu je vázána na jedné implementace rozhraní .NET (například rozhraní .NET Framework na Windows) a mohou tedy důležité závislosti na známé spouštěcí prostředí. Takové prostředí bude vystavení známé sady rozhraní API (.NET a rozhraní API operačního systému) a bude udržovat a vystavit očekávaný stav (například registr Windows).

Vývojáři, kteří vytvářejí knihovny pro konkrétní platformy můžete plně využít základní platformy. Tyto knihovny spustí vždy jen na daným platformě, což kontroly platformy nebo jiné formy podmíněný kód zbytečné (modulo jedné zdrojové kódu pro různé platformy).

Typ knihovny primární třída pro rozhraní .NET Framework byl knihovny pro konkrétní platformu. Dokonce i v jiných implementacích .NET umístila, zůstaly knihovny pro konkrétní platformu typ dominantní knihovny.

## <a name="portable-class-libraries"></a>Přenosné knihovny tříd

Přenosné knihovny se podporují na více implementací rozhraní .NET. Závislosti se pořád moct použít na známé spouštěcí prostředí, ale prostředí jsou syntetické ten, který je generován průnik sadu konkrétní implementace rozhraní .NET. To znamená, že vystavené rozhraní API a platforma předpoklady podmnožinu toho, co by být k dispozici do knihovny pro konkrétní platformu.

Volíte konfiguraci platformy tak při vytvoření přenosné knihovny. Jde o sadu platformy, které budete potřebovat pro podporu (například rozhraní .NET Framework 4.5 +, Windows Phone 8.0 +). Další platformy, které se rozhodnete pro podporu, méně rozhraní API a méně platformy předpoklady, které můžete provést, nejnižší společným faktorem. Tato vlastnost může být matoucí zpočátku od lidé často přemýšlení "více je lepší", ale, že v menší počet dostupných rozhraní API podporované platformy výsledky hledání.

Mnoho vývojářů knihovny přešli z vytváření více knihovny pro konkrétní platformu z jednoho zdroje (pomocí direktivy podmíněné kompilace) na přenosných knihoven. Existují [několik přístupů](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) pro přístup k funkce specifické pro platformu v rámci přenosných knihoven s [návnada a přepínač](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) nejvíce široce přijat postup v tomto okamžiku.

## <a name="net-standard-class-libraries"></a>Knihovny tříd .NET standard

Knihovny .NET standard jsou nahrazení konceptů specifických pro platformu a přenosných knihoven. Jsou specifické pro platformu v tom smyslu, že zveřejňovaly všechny funkce ze základní platformy (bez syntetického platformy nebo průniky platformu). Jsou to v tom smyslu, že fungují na všech platformách doprovodné přenosné.

Sada knihovny .NET Standard poskytuje _kontrakty_. Implementace .NET musí podporovat každou smlouvu plně nebo vůbec ne. Každá implementace, proto podporuje sadu .NET Standard smluv. Důsledkem je, že každý knihovny třídy .NET Standard se podporuje na platformách, které podporují závislých kontraktu.

.NET Standard nevystavuje celé funkce rozhraní .NET Framework (ani je, že cíl), ale zveřejňovaly mnoho další rozhraní API než přenosné knihovny tříd. Postupně přibudou další rozhraní API.

Následující platformy podporují knihovny .NET Standard:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Univerzální platforma Windows (UPW)
* Windows
* Windows Phone
* Windows Phone Silverlight

Další informace najdete v tématu [.NET Standard](net-standard.md) tématu.

## <a name="mono-class-libraries"></a>Knihovny tříd mono

Knihovny tříd jsou podporovány v Mono, včetně tři typy knihoven, které je popsáno výše. Mono často ukázala (správně) jako na více platforem implementace rozhraní Microsoft .NET Framework. V části to bylo, protože knihovny specifické pro platformu .NET Framework by mohla spustit na modul Mono runtime bez změny nebo opětovnou kompilaci. Tato vlastnost byla na místě před vytvořením knihovny tříd portable, proto byla jasnou volbou povolit binární přenositelnost mezi rozhraní .NET Framework a Mono (i když to šlo jenom v jednom směru).
