---
title: Knihovny tříd rozhraní .NET
description: Zjistěte, jak knihovny tříd rozhraní .NET umožňují skupiny užitečné funkce na moduly, které můžete používat více aplikací.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: 7d2f81ef08892c994163d609a56008c1accadaa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="net-class-libraries"></a>Knihovny tříd rozhraní .NET

Knihovny tříd se [sdílenou knihovnu](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) koncept pro .NET. Ty umožňují componentize užitečné funkce do modulů, které můžete používat více aplikací. Můžete také používají jako prostředek k načítání funkce, které nejsou potřeba nebo není známý při spuštění aplikace. Knihovny tříd jsou popsány pomocí [formát souboru sestavení .NET](assembly-format.md).

Existují tři typy knihovny tříd, které můžete použít:

*   **Specifické pro platformu** knihovny tříd mají přístup k rozhraním API v dané platformy (pro rozhraní .NET Framework, například Xamarin iOS), ale dá použít jenom aplikace a knihovny, které cílí na této platformě.
*   **Přenosné** knihovny tříd mít přístup k podmnožinu rozhraní API a mohou být využívána aplikace a knihovny, které více cílových platforem.
*   **.NET standard** knihovny tříd jsou fúze konceptu specifické pro platformu a přenosné knihovny do jednoho model, který poskytuje nejlepší z obou.

## <a name="platform-specific-class-libraries"></a>Knihovny tříd specifických pro platformy

Specifické pro platformu knihovny je vázána na jediná implementace rozhraní .NET (například rozhraní .NET Framework v systému Windows) a může trvat proto důležité závislosti na prostředí pro spouštění známé. Takové prostředí bude vystavit známé sada rozhraní API (rozhraní .NET a rozhraní API operačního systému) a bude udržovat a vystavit očekávanému stavu (například registru systému Windows).

Vývojáři vytvářející konkrétní knihovny platformy můžete plně využít základní platformy. Knihovny bude vždy jen spustit na který danou platformu, provádění kontroly platformy nebo jiné formy podmíněného kód nepotřebné (modulo jedné zdrojové kódu pro různé platformy).

Knihovny specifické pro platformu byla typu knihovny primární třídou pro rozhraní .NET Framework. I v jiných implementacích .NET vyplývá, specifické pro platformu knihovny zůstaly typu dominantní knihovny.

## <a name="portable-class-libraries"></a>Knihovny přenosných tříd

Přenosné knihovny jsou podporovány na více implementace rozhraní .NET. Se stále může trvat závislosti na prostředí pro spouštění známé, ale prostředí je syntetické ten, který je generován průnik sadu konkrétní implementace rozhraní .NET. To znamená, že zveřejněné předpoklady rozhraní API a platformy, jsou podmnožinou co by být k dispozici pro knihovnu specifické pro platformu.

Konfigurace platformy zvolíte při vytvoření přenosné knihovny. Jedná se o sadu platformy, které potřebujete podporovat (například rozhraní .NET Framework 4.5 +, Windows Phone 8.0 +). Další platformy, které se rozhodnete podporu, méně rozhraní API a méně předpoklady platformy můžete nastavit, nejnižší společný jmenovatel. Tato vlastnost může být složitá na první pohled od osob, které jsou často uvažování "víc je lepší", ale najít další podporované platformy výsledky v menší počet dostupných rozhraní API.

Celá řada vývojářů knihovny, že jste přepnuli neměly více knihoven specifické pro platformu z jednoho zdroje (pomocí direktivy Podmíněná kompilace) na přenosné knihovny. Existují [několik přístupů](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) pro přístup k specifické pro platformu funkcionalitu v rámci přenosné knihovny s [návnada a přepínače](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) maximum široce přijat technika v tomto okamžiku.

### <a name="net-standard-class-libraries"></a>Knihovny standardní tříd rozhraní .NET

.NET standard knihovny jsou náhradní koncepty specifické pro platformu a přenosné knihovny. Jsou specifické pro platformu v tom smyslu, že jejich zpřístupnění všechny funkce ze základní platformy (žádné syntetické platformy nebo průnikům platformy). Jsou přenosné v tom smyslu, že fungují na všech platformách podpůrné.

.NET Standard poskytuje sadu knihovny _kontrakty_. Implementace rozhraní .NET musí podporovat každé smlouvě, plně nebo vůbec. Každá implementace proto podporuje sadu .NET standardní smluv. Důsledkem je, že každý .NET Standard knihovny tříd je podporována na platformách, které ji podporují je kontrakt závislosti.

.NET Standard nevystavuje celý funkce rozhraní .NET Framework (ani je, že cílem), ale vystavit mnoho další rozhraní API než přenosné knihovny tříd. V čase se přidají další rozhraní API.

Na následujících platformách podporují .NET Standard knihovny:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Univerzální platforma Windows (UPW)
* Windows
* Windows Phone
* Windows Phone Silverlight

Další informace najdete v tématu [.NET Standard](net-standard.md) tématu.

### <a name="mono-class-libraries"></a>Knihovny tříd mono

Knihovny tříd jsou podporovány na Mono, včetně tři typy knihoven popsané výše. Mono často ukázala (správně) jako napříč platformami implementace rozhraní Microsoft .NET Framework. V části to byl, protože specifické pro platformu .NET Framework knihovny může spustit na Mono runtime bez úprav nebo opětovnou kompilaci. Tato vlastnost byla na místě před vytvoření knihovny tříd portable, takže se na zřejmé volbu Povolit binární přenositelnost mezi rozhraní .NET Framework a Mono (i když to šlo jenom v jednom směru).
