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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28b09bf07d831747be0006ffe1f1d8c5ac5171ce
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052647"
---
# <a name="compiling-apps-with-net-native"></a>Kompilování aplikací pomocí .NET Native
.NET native se technologie předkompilace pro sestavování a nasazování aplikací pro Windows, která je součástí sady Visual Studio 2015 a novější verze. Automaticky kompilaci verze vydání aplikace, které jsou zapsané ve spravovaném kódu (C# nebo Visual Basic) a do nativního kódu, který cílí na rozhraní .NET Framework a Windows 10.  
  
 Obvykle aplikace, které cílí rozhraní .NET Framework jsou kompilovány do (IL intermediate language). V době spuštění přeloží kompilátor just-in-time (JIT) IL na nativní kód. .NET Native zkompiluje naproti tomu aplikace Windows přímo do nativního kódu. Pro vývojáře to znamená, že:  
  
- Vaše aplikace funkcí výkonu nativního kódu. Obvykle se výkon vynikající kód, který je nejprve zkompilován do IL a potom kompilovány do nativního kódu, kompilátorem JIT. 
  
- Můžete pokračovat v aplikaci C# nebo Visual Basic.  
  
- Můžete nadále využívat prostředky poskytované rozhraní .NET Framework, včetně jeho knihovny tříd, správu a uvolňování paměti kolekce automatické paměti a zpracování výjimek.  
  
 Pro uživatele aplikací .NET Native nabízí tyto výhody:  
  
- Rychlejší spuštění s úspěšností pro většinu scénářů a aplikací.
  
- Rychlejší spuštění pro většinu scénářů a aplikací. 
  
- Nízké náklady na nasazení a aktualizace.  
  
- Optimalizované využití paměti aplikace.  

> [!IMPORTANT]
> Pro většinu scénářů a aplikací .NET Native nabízí výrazně rychlejší spouštění a špičkový výkon ve srovnání s aplikace zkompilována do IL nebo do NGEN image. Vaše výsledky se však může mírně lišit. Aby bylo zajištěno, že aplikace má prospěch z vylepšení výkonu .NET Native, porovnejte svůj výkon pomocí bez – .NET Native verze vaší aplikace. Další informace najdete v tématu [přehled výkonnostní relace](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).
 
Ale .NET Native vyžaduje více než kompilace do nativního kódu. Se mění způsob, jakým, že aplikace rozhraní .NET Framework jsou vytvořené a spustit. Zejména:  
  
- Při předkompilaci požadované části rozhraní .NET Framework staticky propojené do vaší aplikace. To umožňuje aplikaci spustit s knihovnami místní aplikace rozhraní .NET Framework, a kompilátor provede globální analýzu k zajištění výkonu wins. V důsledku toho aplikace budou spouštět rychleji i po aktualizace rozhraní .NET Framework.  
  
- Modul runtime .NET Native je optimalizovaná pro statické předkompilace a v převážné většině případů nabízí vynikající výkon. Ve stejnou dobu zůstane zachován reflexe základní funkce, které najít tak produktivitu vývojářů.  
  
- .NET native používá stejnou back-endu jako C++ kompilátoru, který je optimalizovaný pro statické předkompilace scénáře.  
  
 .NET native se bude moct přinést výhody výkonu C++ do spravovaného kódu vývojáři, protože používá stejné nebo podobné nástroje jako C++ pod pokličkou, jak je znázorněno v této tabulce.  
  
||.NET Native|C++|  
|-|----------------------------------------------------------------|-----------|  
|Knihovny|Rozhraní .NET Framework a prostředí Windows Runtime|Win32 a prostředí Windows Runtime|  
|Kompilátor|Optimalizující kompilátor UTC|Optimalizující kompilátor UTC|  
|nasazení|Připraveno ke spuštění binárních souborů|Připraveno ke spuštění binárních souborů (ASM)|  
|Modul runtime|MRT.dll (Minimal CLR Runtime)|CRT.dll (C Runtime)|  
  
 Pro aplikace Windows pro Windows 10 nahrát binární soubory nativní kompilační kód .NET v aplikaci balíčky (soubory .appx) pro Windows Store.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Další informace o vývoji aplikací s nativní kompilací kódu .NET najdete v těchto tématech:  
  
- [Začínáme s .NET kompilace nativního kódu: Průvodce prostředí pro vývojáře](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
- [.NET native a kompilace:](../../../docs/framework/net-native/net-native-and-compilation.md) .NET Native jak zkompiluje projekt do nativního kódu.  
  
- [Reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    - [Rozhraní API, která závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    - [Informace o rozhraní API reflexe](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    - [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
- [Serializace a metadata](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
- [Migrace aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
- [Obecné řešení potíží s .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
