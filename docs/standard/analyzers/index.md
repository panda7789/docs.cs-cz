---
title: Platformě Roslyn na základě analyzátory – .NET
description: Další informace o analyzátory Roslyn na základě, které najít problémy a navrhují opravy těchto problémů.
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 226482d1d385078811f2b1c5ee138e24287a785e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154330"
---
# <a name="the-roslyn-based-analyzers"></a>Analyzátory založené platformě Roslyn

Založené na platformě Roslyn analyzátory analyzovat zdrojový kód projektu k vyhledání problémů a opravy zobrazovat pomocí sady SDK kompilátoru .NET (Roslyn API). Různé analyzátory vyhledejte různých tříd problémů, od postupů, které můžou způsobovat chyby k zajištění zabezpečení pro kompatibilitu s rozhraními API.

Založené na platformě Roslyn analyzátory funguje interaktivně a během sestavení. Analyzátor obsahuje různé pokyny, když v sadě Visual Studio nebo v sestavení příkazového řádku.

Při úpravách kódu v sadě Visual Studio spustit analyzátory při provádění změn, informace o možných problémech zachycování, jakmile vytvoříte kód, který se týká aktivace. Všechny problémy jsou zvýrazněny podtržení vlnovkou pod jakýkoli problém. Visual Studio zobrazí žárovka a když na ni kliknete Analyzátor se navrhují možné opravy pro daný problém. Při vytváření projektu v sadě Visual Studio nebo z příkazového řádku se analyzuje zdrojový kód a analyzátor poskytuje úplný seznam potenciální problémy. Následující obrázek ukazuje příklad.

![problémech ohlášených analyzátor architektury](./media/framework-analyzers-2.png)

Založené na platformě Roslyn analyzátory ohlásit potenciální problémy jako chyby, upozornění nebo informace v závislosti na závažnosti problému.

Je založené na platformě Roslyn analyzátory nainstalovat jako balíčky NuGet ve vašem projektu. Nakonfigurované analyzátory a všechna nastavení pro každý Analyzátor se obnovit a spustit na počítači pro všechny vývojáře pro daný projekt.

> [!NOTE]
> Uživatelské prostředí u založené na platformě Roslyn Analyzátory se liší od, který knihoven analýzy kódu, jako je starší verze FxCop a analytické nástroje zabezpečení.  Není nutné explicitně spustit analyzátory založené na platformě Roslyn. Není nutné použít položky nabídky "Spustit analýzu kódu" v sadě Visual Studio v nabídce "Analyzovat". Založené na platformě Roslyn analyzátory poběží nekopírovat při práci. 

## <a name="more-information-on-specific-analyzers"></a>Další informace o konkrétní analyzátory

Následující analyzátory jsou popsané v této části:

* [Analyzátor rozhraní API](api-analyzer.md): Tento analyzátor prozkoumá váš kód pro potenciální rizika nebo používá rozhraní API nepoužívané.    
* [Analyzátor architektury](framework-analyzer.md): Tento analyzátor prozkoumá váš kód k zajištění, že splňuje pravidla pro aplikace .NET Framework. Tato pravidla zahrnují několik doporučení na základě zabezpečení.
* [.NET portability Analyzeru](portability-analyzer.md): Tento analyzátor prozkoumá váš kód chcete zobrazit, kolik práce je nutná k zajištění aplikace kompatibilní s jinými implementace .NET a profily, včetně .NET Core, .NET Standard, UPW a Xamarin pro iOS, Android a macu. 
