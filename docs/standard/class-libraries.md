---
title: Knihovny tříd .NET
description: Zjistěte, jak knihovny tříd rozhraní .NET umožňují seskupit užitečné funkce do modulů, které mohou být používány více aplikacemi.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.openlocfilehash: b7934e5def202760ab05d363ee5fcda5d012ca72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124582"
---
# <a name="net-class-libraries"></a>Knihovny tříd .NET

Knihovny tříd jsou koncept [sdílené knihovny](https://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) pro rozhraní .NET. Umožňují komponentovat užitečné funkce do modulů, které mohou být použity více aplikacemi. Mohou být také použity jako prostředek načítání funkce, která není potřeba nebo není známa při spuštění aplikace. Knihovny tříd jsou popsány pomocí [formátu souboru sestavení .NET](assembly/file-format.md).

Existují tři typy knihoven tříd, které můžete použít:

* Knihovny tříd **specifické pro platformu** mají přístup ke všem rozhraním API v dané platformě (například .NET Framework, Xamarin iOS), ale mohou být použity pouze aplikacemi a knihovnami, které cílí na tuto platformu.
* **Přenosné** knihovny tříd mají přístup k podmnožině api a mohou je používat aplikace a knihovny, které cílí na více platforem.
* **Knihovny** tříd .NET Standard jsou sloučením konceptu knihovny specifického pro platformu a přenosné knihovny do jednoho modelu, který poskytuje to nejlepší z obou.

## <a name="platform-specific-class-libraries"></a>Knihovny tříd specifických pro platformu

Knihovny specifické pro platformu jsou vázány na jednu implementaci rozhraní .NET (například rozhraní .NET Framework v systému Windows) a proto mohou mít významné závislosti na známém prostředí provádění. Takové prostředí zpřístupní známou sadu rozhraní API (.NET a Rozhraní API operačního systému) a bude udržovat a vystavit očekávaný stav (například registr systému Windows).

Vývojáři, kteří vytvářejí knihovny specifické pro platformu, mohou plně využívat základní platformu. Knihovny budou vždy spuštěny pouze na dané platformě, takže kontroly platformy nebo jiné formy podmíněného kódu jsou zbytečné (modulo single sourcing code pro více platforem).

Knihovny specifické pro platformu byly typem knihovny primární třídy pro rozhraní .NET Framework. I když se objevily další implementace rozhraní .NET, knihovny specifické pro platformu zůstaly dominantním typem knihovny.

## <a name="portable-class-libraries"></a>Přenosné knihovny tříd

Přenosné knihovny jsou podporovány ve více implementacích rozhraní .NET. Stále mohou trvat závislosti na známé spuštění prostředí, ale prostředí je syntetický, který je generován průsečík u sady konkrétních implementací .NET. To znamená, že vystavené rozhraní API a předpoklady platformy jsou podmnožinou toho, co by bylo k dispozici pro knihovnu specifickou pro platformu.

Konfiguraci platformy zvolíte při vytváření přenosné knihovny. Jedná se o sadu platforem, které potřebujete podporovat (například rozhraní .NET Framework 4.5+, Windows Phone 8.0+). Čím více platforem se rozhodnete podporovat, tím méně api a méně předpokladů platformy můžete provést, nejnižší společný jmenovatel. Tato charakteristika může být zpočátku matoucí, protože lidé si často myslí, že "více je lepší", ale zjistíte, že více podporovaných platforem vede k menšímu počtu dostupných rozhraní API.

Mnoho vývojářů knihovny přešlo z výroby více knihoven specifických pro platformu z jednoho zdroje (pomocí direktiv podmíněné kompilace) na přenosné knihovny. Existuje [několik přístupů](https://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) pro přístup k funkcím specifickým pro platformu v přenosných knihovnách, přičemž [návnada a přepínač](https://log.paulbetts.org/the-bait-and-switch-pcl-trick/) jsou v tomto okamžiku nejpoužívanější technikou.

## <a name="net-standard-class-libraries"></a>Knihovny tříd .NET Standard

Knihovny .NET Standard jsou náhradou konceptů knihoven specifických pro platformu a přenosných knihoven. Jsou specifické pro platformu v tom smyslu, že zveřejňují všechny funkce z podkladové platformy (žádné syntetické platformy nebo křižovatky platformy). Jsou přenosné v tom smyslu, že pracují na všech podpůrných platformách.

Standard .NET standard zpřístupňuje sadu _smluv_knihovny . Implementace rozhraní .NET musí plně podporovat každou smlouvu nebo vůbec. Každá implementace proto podporuje sadu smluv .NET Standard. Důsledek je, že každá knihovna tříd .NET Standard je podporována na platformách, které podporují její závislosti smluv.

Standard .NET nezveřejňuje všechny funkce rozhraní .NET Framework (ani je to cíl), ale zveřejňují mnohem více rozhraní API než knihovny přenosných tříd. Další api budou přidány v průběhu času.

Následující platformy podporují knihovny .NET Standard:

* .NET Core
* .NET Framework
* Mono
* Xamarin.iOS, Xamarin.Mac, Xamarin.Android
* Univerzální platforma Windows (UPW)
* Windows
* Windows Phone
* Windows Phone Silverlight

Další informace naleznete v tématu [.NET Standard.](net-standard.md)

## <a name="mono-class-libraries"></a>Knihovny tříd Mono

Knihovny tříd jsou podporovány na Mono, včetně tří typů knihoven popsaných výše. Mono je často vnímána (správně) jako implementace rozhraní Microsoft .NET Framework napříč platformami. Částečně to bylo proto, že knihovny rozhraní .NET Framework specifické pro platformu mohly být spuštěny v souboru Mono runtime bez úprav nebo rekompilace. Tato charakteristika byla na místě před vytvořením knihovny přenosných tříd, takže byla zřejmá volba povolit binární přenositelnost mezi rozhraním .NET Framework a Mono (i když to fungovalo pouze v jednom směru).
