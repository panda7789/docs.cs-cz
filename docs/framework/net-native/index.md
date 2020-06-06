---
title: Kompilování aplikací pomocí .NET Native
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
ms.openlocfilehash: 1f176e81905fe68c6d740a13240fe814659a7a59
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128379"
---
# <a name="compiling-apps-with-net-native"></a>Kompilování aplikací pomocí .NET Native

.NET Native je předkompilační technologie pro sestavování a nasazování aplikací pro Windows, které jsou součástí sady Visual Studio 2015 a novějších verzí. Automaticky zkompiluje vydanou verzi aplikací, které jsou napsány ve spravovaném kódu (C# nebo Visual Basic) a cílí na .NET Framework a Windows 10 do nativního kódu.

Aplikace, které cílí na .NET Framework, jsou obvykle kompilovány do jazyka IL (Intermediate Language). V době běhu překládá kompilátor JIT (just-in-time) IL na nativní kód. Naproti tomu .NET Native zkompiluje aplikace pro Windows přímo do nativního kódu. Pro vývojáře to znamená:

- Vaše aplikace se zaměřením na výkon nativního kódu. Výkon je obvykle nadřazený kódu, který je nejprve zkompilován do IL a poté zkompilován do nativního kódu kompilátorem JIT.

- Můžete pokračovat v programu v jazyce C# nebo Visual Basic.

- Můžete nadále využívat prostředky poskytované .NET Framework, včetně knihovny tříd, automatické správy paměti a uvolňování paměti a zpracování výjimek.

Pro uživatele vašich aplikací .NET Native nabízí tyto výhody:

- Rychlejší doba provádění většiny aplikací a scénářů.

- Rychlejší časy spuštění většiny aplikací a scénářů.

- Nízké náklady na nasazení a aktualizaci.

- Optimalizované využití paměti aplikace.

> [!IMPORTANT]
> Pro většinu aplikací a scénářů nabízí .NET Native výrazně rychlejší dobu spuštění a špičkový výkon v porovnání s aplikací zkompilovanou do IL nebo do image NGEN. Výsledky se ale můžou lišit. Chcete-li zajistit, aby vaše aplikace využila vylepšení výkonu .NET Native, měli byste porovnat jeho výkon s verzí non-.NET Native vaší aplikace. Další informace najdete v tématu [Přehled relace výkonu](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).

Ale .NET Native zahrnuje více než kompilaci do nativního kódu. Transformuje způsob, jakým se sestavují a spouštějí aplikace .NET Framework. Zejména jde o toto:

- V průběhu předkompilace jsou požadované části .NET Framework staticky propojeny do vaší aplikace. To umožňuje aplikaci běžet s knihovnami místních aplikací .NET Framework a kompilátor provede globální analýzu pro doručení služby WINS výkonu. V důsledku toho aplikace spouští konzistentně rychleji, i když .NET Framework aktualizace.

- Modul runtime .NET Native je optimalizován pro statickou předkompilaci a v obrovské většině případů nabízí špičkový výkon. Ve stejnou dobu zachovává základní funkce reflexe, které vývojáři hledají tak, aby byly tak produktivní.

- .NET Native používá stejný back-end jako kompilátor jazyka C++, který je optimalizován pro statické scénáře předkompilace.

.NET Native je možné přenést výhody z hlediska výkonu pro vývojáře spravovaného kódu, protože používá stejné nebo podobné nástroje jako C++ v digestoři, jak je znázorněno v této tabulce.

||.NET Native|C++|
|-|----------------------------------------------------------------|-----------|
|Knihovny|.NET Framework + prostředí Windows Runtime|Win32 + prostředí Windows Runtime|
|Compiler|Kompilátor pro optimalizaci UTC|Kompilátor pro optimalizaci UTC|
|Nainstalována|Soubory připravené ke spuštění|Hotové binární soubory připravené k běhu (ASM)|
|Modul runtime|MRT. dll (minimální modul CLR Runtime)|CRT. dll (běhové prostředí C)|

Pro aplikace pro Windows pro Windows 10 nahrajete .NET Native binárních souborů kompilace kódu v balíčcích aplikací (soubory. appx) do Windows Storu.

## <a name="in-this-section"></a>V tomto oddílu

Další informace o vývoji aplikací pomocí kompilace kódu .NET Native najdete v těchto tématech:

- [Začínáme s kompilací kódu .NET Native: Návod k vývojovému prostředí](getting-started-with-net-native.md)

- [.NET Native a kompilace:](net-native-and-compilation.md) Jak .NET Native zkompiluje projekt do nativního kódu.

- [Reflexe a .NET Native](reflection-and-net-native.md)

  - [Rozhraní API, která závisí na reflexi](apis-that-rely-on-reflection.md)

  - [Informace o rozhraní API reflexe](net-native-reflection-api-reference.md)

  - [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)

- [Serializace a metadata](serialization-and-metadata.md)

- [Migrace aplikace pro Windows Store do .NET Native](migrating-your-windows-store-app-to-net-native.md)

- [Obecné řešení potíží s .NET Native](net-native-general-troubleshooting.md)
