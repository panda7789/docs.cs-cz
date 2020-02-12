---
title: Knihovny tříd .NET
description: Přečtěte si, jak knihovny tříd .NET umožňují seskupovat užitečné funkce do modulů, které může používat více aplikací.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: b7934e5def202760ab05d363ee5fcda5d012ca72
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124582"
---
# <a name="net-class-libraries"></a>Knihovny tříd .NET

Knihovny tříd jsou koncept [sdílené knihovny](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) pro rozhraní .NET. Umožňují componentize užitečné funkce v modulech, které může používat více aplikací. Lze je také použít jako způsob načítání funkcí, které nejsou potřeba nebo nejsou známy při spuštění aplikace. Knihovny tříd jsou popsány pomocí [formátu souboru sestavení .NET](assembly/file-format.md).

Existují tři typy knihoven tříd, které lze použít:

* Knihovny tříd **specifické pro platformu** mají přístup ke všem rozhraním API v dané platformě (například .NET Framework, Xamarin iOS), ale můžou je používat jenom aplikace a knihovny, které cílí na tuto platformu.
* **Přenositelné** knihovny tříd mají přístup k podmnožině rozhraní API a můžou je používat aplikace a knihovny, které cílí na více platforem.
* Knihovny tříd **.NET Standard** jsou fúzí konceptu knihovny specifické pro platformu a přenositelné knihovny do jediného modelu, který poskytuje nejlepší z obou.

## <a name="platform-specific-class-libraries"></a>Knihovny tříd specifické pro platformu

Knihovny specifické pro platformu jsou vázány na jednu implementaci rozhraní .NET (například .NET Framework ve Windows) a mohou proto mít významné závislosti na známém prostředí pro spuštění. Takové prostředí zveřejňuje známou sadu rozhraní API (rozhraní API .NET a OS) a bude udržovat a vystavovat očekávaný stav (například registr systému Windows).

Vývojáři, kteří vytvářejí knihovny specifické pro platformu, můžou plně využívat základní platformu. Knihovny se v této dané platformě budou spouštět jenom v případě, že se vydávají kontroly platforem nebo jiné formy podmíněného kódu, který není potřebný (modulo jeden kód pro více platforem).

Knihovny specifické pro platformu byly primární typ knihovny tříd pro .NET Framework. I v případě jiných implementací rozhraní .NET zůstaly knihovny specifické pro platformu dominantní typ knihovny.

## <a name="portable-class-libraries"></a>Přenositelné knihovny tříd

Přenosné knihovny jsou podporovány v několika implementacích rozhraní .NET. Stále můžou podniknout závislosti na známém prostředí pro spuštění, ale prostředí je syntetické, které se generuje v průsečíku sady konkrétních implementací .NET. To znamená, že vystavená rozhraní API a předpoklady platforem jsou podmnožinou toho, co by bylo k dispozici pro knihovnu specifickou pro konkrétní platformu.

Konfiguraci platformy zvolíte při vytváření přenosné knihovny. Jedná se o sadu platforem, které potřebujete podporovat (například .NET Framework 4.5 +, Windows Phone 8.0 +). Čím více platforem si nebudete podporovat, tím menšího společného jmenovatele můžete udělat méně rozhraní API a méně. Tato vlastnost může být zamatoucí jako první, protože lidé často uvažují o "více jsou lepší", ale zjistíte, že více podporovaných platforem má za následek méně dostupných rozhraní API.

Mnoho vývojářů knihovny přešlo z vytváření více knihoven specifických pro jednotlivé platformy z jednoho zdroje (pomocí direktiv podmíněné kompilace) do přenosných knihoven. Pro přístup k funkcím specifickým pro platformu v přenosných knihovnách je k dispozici [několik přístupů](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) , přičemž v tomto [okamžiku je v](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) tuto chvíli nejdůležitějším způsobem přijatelné.

## <a name="net-standard-class-libraries"></a>.NET Standard knihovny tříd

Knihovny .NET Standard jsou náhradou konceptů knihoven specifických pro platformu a přenosných knihoven. Jsou specifické pro platformu v tom smyslu, že zpřístupňují všechny funkce z základní platformy (žádné syntetické platformy nebo průniky platforem). Jsou přenosné v tom smyslu, že fungují na všech podporovaných platformách.

.NET Standard zveřejňuje sadu _kontraktů_knihoven. Implementace rozhraní .NET musí podporovat jednotlivé smlouvy zcela nebo vůbec. Každá implementace proto podporuje sadu .NET Standardch kontraktů. Corollary je, že každá knihovna tříd .NET Standard je podporována na platformách, které podporují závislosti jejich smluv.

.NET Standard nevystaví celou funkčnost .NET Framework (ani to není cílem), ale zveřejňuje mnoho dalších rozhraní API než přenosných knihoven tříd. V průběhu času bude přidáno více rozhraní API.

Následující platformy podporují knihovny .NET Standard:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Univerzální platforma Windows (UPW)
* Windows
* telefon se systémem Windows
* Windows Phone Silverlight

Další informace najdete v tématu [.NET Standard](net-standard.md) .

## <a name="mono-class-libraries"></a>Knihovny tříd mono

Knihovny tříd jsou podporovány v mono, včetně tří typů knihoven popsaných výše. Mono je často vidět (správně) jako implementace Microsoft .NET Framework pro různé platformy. Částečně to bylo způsobeno tím, že knihovny .NET Framework specifické pro platformu by mohly být spuštěny v Mono runtime bez změny nebo opětovné kompilace. Tato vlastnost byla provedena před vytvořením přenosných knihoven tříd, proto byla zřejmou volbou pro povolení binární přenositelnosti mezi .NET Framework a Mono (i když pracovala pouze v jednom směru).
