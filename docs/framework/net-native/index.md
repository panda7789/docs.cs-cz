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
ms.openlocfilehash: 6900bca2bd94f52ea5603c752681163cde52ce19
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="compiling-apps-with-net-native"></a>Kompilování aplikací pomocí .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] je předkompilace technologie pro vytváření a nasazování aplikací pro Windows, která je součástí sady Visual Studio 2015 a novější verze. Zkompiluje automaticky prodejní verze aplikace, které jsou zapsány v spravovaného kódu (C# nebo Visual Basic), že cílové rozhraní .NET Framework a Windows 10 do nativního kódu.  
  
 Aplikace, které cílí na rozhraní .NET Framework jsou obvykle zkompilovány do převodního jazyka (IL). V době běhu kompilátoru za běhu (JIT) překládá IL do nativního kódu. Naproti tomu [!INCLUDE[net_native](../../../includes/net-native-md.md)] zkompiluje aplikací pro Windows přímo do nativního kódu. Pro vývojáře to znamená:  
  
-   Vaše aplikace funkce výkon nativního kódu. Obvykle bude výkon hodnotu větší než kód, který je napřed zkompilovat IL a pak zkompilují do nativního kódu kompilátoru za běhu. 
  
-   Můžete nadále programu v C# nebo Visual Basic.  
  
-   Můžete nadále využívat prostředky poskytované rozhraní .NET Framework, včetně jeho knihovny tříd, správu a uvolňování paměti kolekce automatické paměti a výjimek.  
  
 Pro uživatele vaší aplikace [!INCLUDE[net_native](../../../includes/net-native-md.md)] nabízí tyto výhody:  
  
-   Rychlejší doby provádění pro většinu aplikací a scénáře.
  
-   Kratší časy spuštění pro většinu aplikací a scénáře. 
  
-   Nízké náklady na nasazení a aktualizace.  
  
-   Optimalizovat využití paměti v aplikaci.  

> [!IMPORTANT]
> Valná většina scénáře a aplikace .NET Native nabízí výrazně rychlejší spouštění a vynikající výkon ve srovnání s zkompilovat IL nebo bitovou kopii NGEN aplikace. Výsledky se však mohou lišit. Aby se zajistilo, že vaše aplikace využívaly vylepšení výkonu systému .NET Native, byste měli porovnat jeho výkon s u jiných - .NET Native verzi vaší aplikace. Další informace najdete v tématu [přehled výkonnostní relace](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).
 
Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] zahrnuje více než kompilace nativního kódu. Ho transformuje způsobu, jakým jsou vytvořené a provést aplikací rozhraní .NET Framework. Zejména:  
  
-   Při předkompilaci jsou požadované části rozhraní .NET Framework staticky propojené do vaší aplikace. To umožňuje aplikaci spustit s knihovnami místní aplikace rozhraní .NET Framework a kompilátor provádět globální analýzu k poskytování výkonu služby wins. Výsledkem je aplikace budou spouštět rychleji i po aktualizací rozhraní .NET Framework.  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] Runtime je optimalizovaná pro statické předkompilaci a v valná většina případů nabízí vyšší výkon. Ve stejnou dobu zůstane zachován funkce reflexe jádra, které vývojáři najít tak produktivitu.  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] používá stejný zpět ukončení jako C++ compiler, která je optimalizovaná pro statické předkompilace scénáře.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] je přináší výhody výkonu C++ na vývojářům spravovaného kódu protože používá nástroje stejné nebo podobné jako C++ pod pokličkou, jak je znázorněno v této tabulce.  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C++|  
|-|----------------------------------------------------------------|-----------|  
|Knihovny|Rozhraní .NET Framework a prostředí Windows Runtime|Win32 + prostředí Windows Runtime|  
|Kompilátoru|Optimalizace kompilátoru UTC|Optimalizace kompilátoru UTC|  
|Nasazení|Binární soubory připravené k použití|Binární soubory připravené k použití (ASM)|  
|Modul runtime|MRT.dll (minimální CLR Runtime)|CRT.dll (C Runtime)|  
  
 Pro aplikace pro Windows pro Windows 10 nahrajte kompilace nativního kódu .NET binárních souborů v aplikaci balíčky (soubory .appx) na web Windows Store.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Další informace o vývoji aplikací s nativní kompilace kódu rozhraní .NET naleznete v následujících tématech:  
  
-   [Začínáme s .NET kompilace nativního kódu: návod prostředí vývojáře](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   [.NET native a kompilace:](../../../docs/framework/net-native/net-native-and-compilation.md) jak .NET Native zkompiluje projekt do nativního kódu.  
  
-   [Reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [Rozhraní API, která závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [Informace o rozhraní API reflexe](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [Serializace a metadata](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [Migrace aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [Obecné řešení potíží s .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
