---
title: Analyzátory založené na Roslyn - .NET
description: Seznamte se s analyzátory založenými na Roslyn, které naleznou problémy a navrhnou opravy těchto problémů.
author: billwagner
ms.author: wiwagn
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 436cfb3904f0891f8c18bb5890563a13d65e2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "62003051"
---
# <a name="the-roslyn-based-analyzers"></a>Analyzátory založené na Roslyn

Analyzátory založené na roslyn používají .NET Compiler SDK (Roslyn API) k analýze zdrojového kódu projektu k nalezení problémů a navržení oprav. Různé analyzátory hledat různé třídy problémů, od postupů, které mohou způsobit chyby na obavy zabezpečení na kompatibilitu rozhraní API.

Analyzátory založené na roslyn pracují interaktivně i během sestavení. Analyzátor poskytuje různé pokyny v sadě Visual Studio nebo v sestavení příkazového řádku.

Při úpravách kódu v sadě Visual Studio se analyzátory spustí při provádění změn a zachycují možné problémy, jakmile vytvoříte kód, který aktivuje obavy. Všechny problémy jsou zvýrazněny klikyháky pod jakýmkoli problémem. Visual Studio zobrazí žárovku a po kliknutí na ni analyzátor navrhne možné opravy tohoto problému. Při vytváření projektu, buď v sadě Visual Studio nebo z příkazového řádku, je analyzován veškerý zdrojový kód a analyzátor poskytuje úplný seznam potenciálních problémů. Následující obrázek ukazuje jeden příklad.

![problémy hlášené rámcovým analyzátorem](./media/framework-analyzers-2.png)

Analyzátory založené na roslynu hlásí potenciální problémy jako chyby, upozornění nebo informace založené na závažnosti problému.

Analyzátory založené na Roslyn jako balíčky NuGet ve vašem projektu. Nakonfigurované analyzátory a všechna nastavení pro každý analyzátor jsou obnoveny a spuštěny v počítači libovolného vývojáře pro tento projekt.

> [!NOTE]
> Uživatelské prostředí pro analyzátory založené na Roslyn je jiné než u knihoven analýzy kódu, jako jsou starší verze FxCop a nástroje pro analýzu zabezpečení.  Není nutné explicitně spustit analyzátory založené na Roslyn. Není nutné používat položky nabídky "Spustit analýzu kódu" v nabídce "Analyzovat" v sadě Visual Studio. Analyzátory založené na roslyn běží asynchronně při práci.

## <a name="more-information-on-specific-analyzers"></a>Více informací o konkrétních analyzátorech

V této části jsou uvedeny následující analyzátory:

* [Analyzátor rozhraní API](api-analyzer.md): Tento analyzátor zkoumá váš kód pro potenciální rizika kompatibility nebo použití zastaralé rozhraní API.
* [Framework Analyzer](framework-analyzer.md): Tento analyzátor zkontroluje váš kód a zajistí, že se bude řídit pokyny pro aplikace rozhraní .NET Framework. Tato pravidla zahrnují několik doporučení založených na zabezpečení.
* [.NET Přenositelnost Analyzer](portability-analyzer.md): Tento analyzátor zkoumá váš kód, aby zjistil, kolik práce je nutné, aby vaše aplikace kompatibilní s jinými implementacemi a profily .NET, včetně .NET Core, .NET Standard, UpWp a Xamarin pro iOS, Android a Mac.
