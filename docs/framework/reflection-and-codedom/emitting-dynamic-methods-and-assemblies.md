---
title: Generování dynamických metod a sestavení
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6d5085b846a10fe86a87e19738e1b159e300c5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Generování dynamických metod a sestavení
Tato část popisuje sadu spravovaných typů v <xref:System.Reflection.Emit> obor názvů, který povolí kompilátoru nebo nástroj pro vydávání metadata a Microsoft (MSIL intermediate language) v době běhu a volitelně generovat soubor přenosné spustitelný soubor (PE) na disku. Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů. V této části, funkce poskytované <xref:System.Reflection.Emit> obor názvů se označuje jako reflexe emitování.  
  
 Emitování reflexe poskytuje následující možnosti:  
  
-   Definovat zjednodušené globální metody na spuštění čas, pomocí <xref:System.Reflection.Emit.DynamicMethod> třídy a spouštět je použití delegátů.  
  
-   Definování sestavení za běhu a jejich spuštění nebo je uložíte na disku.  
  
-   Definovat sestavení za běhu, spustit, je uvolnit a povolit uvolňování, abyste získali zpět jejich prostředky.  
  
-   Definování moduly v nové sestavení za běhu a spustit nebo je uložíte na disku.  
  
-   Definování typů v modulech v době běhu, vytváření instancí těchto typů a vyvolání své metody.  
  
-   Zadejte symbolické informace o definované moduly, které můžete používat nástroje, jako je ladicí programy a profilery kódu.  
  
 Kromě spravovaných typů v <xref:System.Reflection.Emit> obor názvů, existují rozhraní nespravované metadat, které jsou popsány v [rozhraní metadat](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) referenční dokumentace. Emitování reflexe spravované poskytuje vyšší kontrolu sémantických chyb a na vyšší úrovni abstrakce metadat než rozhraní nespravované metadat.  
  
 Další užitečné prostředek pro práci s metadata a MSIL je dokumentace společné jazykové infrastruktury (CLI), zejména "Oddílu II: Metadata definice a sémantiku" a "Oddílu III: soubor CIL instrukce nastavení". Dokumentace je k dispozici online na [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) a na [Ecma webu](http://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>V tomto oddílu
  
[Bezpečnostní problémy v generování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
Popisuje problémy související s vytvářením dynamické sestaveních pomocí reflexe emitování zabezpečení.  

[Postupy: definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md)   
Ukazuje, jak provést jednoduchý dynamické metody a dynamické metoda vázaný na instanci třídy.

[Postupy: definování obecného typu pomocí reflexe emitování](how-to-define-a-generic-type-with-reflection-emit.md)   
Ukazuje, jak chcete vytvořit jednoduché obecného typu s parametry dva typy, jak se má použít třídu rozhraní a zvláštní omezení pro parametry typu a postup vytvoření memers, které používají parametry typu třídy jako parametry a návratové typy.

[Postupy: definování obecné metody pomocí reflexe emitování](how-to-define-a-generic-method-with-reflection-emit.md)   
Ukazuje, jak k vytváření, vydávání a vyvolání jednoduché obecná metoda.

[Collectible sestavení pro generování dynamickém typu](collectible-assemblies.md)   
Představuje collectible sestavení, které jsou dynamická sestavení, které mohou být odpojen bez uvolnění domény aplikace, v jakém byly vytvořeny.
  
## <a name="reference"></a>Odkaz  
 <xref:System.Reflection.Emit.OpCodes>  
 Zařadí katalogu kódy MSIL instrukcí, které můžete použít k vytvoření těla metody.  
  
 <xref:System.Reflection.Emit>  
 Obsahuje spravované třídy používané k emitování dynamických metod a sestavení, typy.  
  
 <xref:System.Type>  
 Popisuje <xref:System.Type> třídy, která reprezentuje typy v spravované reflexe emitování reflexe a který je klíčová pro používání těchto technologií.  
  
 <xref:System.Reflection>  
 Obsahuje spravované třídy používané prozkoumat metadata a spravovaného kódu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Vysvětluje, jak prozkoumat metadata a spravovaného kódu.  
  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Poskytuje přehled o sestavení v rozhraní .NET implementace.
