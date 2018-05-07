---
title: Roslyn na základě analyzátorů - rozhraní .NET
description: Další informace o Roslyn na základě analyzátory, které najít problémy a navrhněte opravy těchto problémů.
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: ec153b8fed08ef245a3a0f58970b4e3955dfacb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="the-roslyn-based-analyzers"></a>Roslyn na základě analyzátory

Na základě Roslyn analyzátorů používat sadu .NET SDK kompilátoru (Roslyn rozhraní API) k analýze vašeho projektu zdrojového kódu k vyhledání problémů a opravy zobrazovat. Různé analyzátory vyhledejte různé třídy problémy, od postupů, které mohou způsobit chyby k zabezpečení se k rozhraní API kompatibility.

Na základě Roslyn analyzátorů fungovat i interaktivně a během sestavení. Nástroje analyzer obsahuje různé pokyny, když v sadě Visual Studio nebo v sestavení příkazového řádku.

Během úprav kódu v sadě Visual Studio spusťte analyzátory při provádění změn, jakmile vytvoříte kód, který aktivuje obavy zachytávání možných problémů. Všechny problémy se zvýrazněnou s podtržení vlnovkou pod jakýkoli problém. Visual Studio zobrazí žárovky, a když na ni kliknete analyzátor navrhovat možné opravy pro daný problém. Při sestavování projektu v sadě Visual Studio nebo z příkazového řádku zdrojového kódu se analyzují a nástroje analyzer poskytuje úplný seznam potenciální problémy. Následující obrázek znázorňuje jedním z příkladů.

![problémy hlášené analyzátor framework](./media/framework-analyzers-2.png)

Na základě Roslyn analyzátorů sestavy potenciální problémy jako chyby, upozornění a informace na základě jejich závažnosti problému.

Nainstalujete na základě Roslyn analyzátorů jako balíčky NuGet ve vašem projektu. Nakonfigurované analyzátory a všechna nastavení pro každou analyzátor jsou obnovit a spustit na počítači pro všechny vývojáře pro tento projekt.

> [!NOTE]
> Uživatelské prostředí na základě Roslyn analyzátorů je jiné než u knihovny analýz kód jako starší verze FxCop a nástrojů pro analýzu zabezpečení.  Nemusíte explicitně spustit na základě Roslyn analyzátorů. Není nutné používat položky nabídky "analýza kódu spustit" v sadě Visual Studio v nabídce "Analyzovat". Na základě Roslyn analyzátorů spustit asychronously při práci. 

## <a name="more-information-on-specific-analyzers"></a>Další informace o konkrétní analyzátory

Následující analyzátorů jsou popsané v této části:

[Rozhraní API analyzátor](api-analyzer.md): Tento analyzátor prozkoumá kódu pro potenciální rizika kompatibility nebo používá zastaralá rozhraní API.    
[Analyzátor Framework](framework-analyzer.md): Tento analyzátor prozkoumá kódu zajistit postupuje podle pokynů pro aplikace .NET Framework. Mezi tato pravidla patří několik doporučení na základě zabezpečení.
