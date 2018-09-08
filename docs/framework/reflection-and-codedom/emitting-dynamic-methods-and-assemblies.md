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
ms.openlocfilehash: 1a0ed1d02fd40a94d4ae63deea3c09b04bfc9bd8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183129"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Generování dynamických metod a sestavení
Tato část popisuje sadu spravovaných typů v <xref:System.Reflection.Emit> obor názvů, které umožní, aby kompilátor nebo nástroj generoval metadata a jazyk Microsoft intermediate language (MSIL) v době běhu a volitelně vygenerovat soubor (PE portable executable) na disku. Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů. V této části poskytuje funkce <xref:System.Reflection.Emit> obor názvů se označuje jako reflexe vygenerovat.  
  
 Emitování reflexe poskytuje následující možnosti:  
  
-   Definovat jednoduchý globální metody za běhu použití <xref:System.Reflection.Emit.DynamicMethod> třídy a spouštějte je pomocí delegátů.  
  
-   Definice sestavení v době běhu a jejich spuštění nebo uložení na disk.  
  
-   Definice sestavení v době běhu, spustit, je uvolnit a povolit uvolňování uvolnit jejich prostředky.  
  
-   Definování modulů v nová sestavení v době běhu a spouštět nebo uložit na disk.  
  
-   Definování typů v modulech v době běhu, vytváření instancí těchto typů a vyvolání jejich metod.  
  
-   Definujte informace o symbolech pro definovaný moduly, které můžete používat nástroje, jako je například ladicí programy a profilery kódu.  
  
 Kromě spravovaných typů v <xref:System.Reflection.Emit> obor názvů, nejsou nespravované metadat rozhraní, které jsou popsány v [rozhraní metadat](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) referenční dokumentaci. Emitování reflexe spravované nabízí silnější kontrolu sémantických chyb a vyšší úroveň abstrakce metadata než rozhraní nespravované metadat.  
  
 Další užitečné zdroje pro práci s metadata a jazyk MSIL je dokumentace společné jazykové infrastruktury (CLI), zejména "Oddíl II: Metadata definice a sémantika" a "Oddílu III: soubor CIL se NAČTE sadu instrukcí". Dokumentace je k dispozici online na [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) a [webu Ecma](https://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>V tomto oddílu
  
[Bezpečnostní problémy v generování reflexe](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
Popisuje problémy související s vytvářením dynamických sestavení pomocí operace reflection emit zabezpečení.  

[Postupy: definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md)   
Ukazuje, jak provést jednoduchou dynamickou metodu a dynamická metoda svázána s instancí třídy.

[Postupy: definování obecného typu pomocí reflexe generování](how-to-define-a-generic-type-with-reflection-emit.md)   
Ukazuje, jak vytvořit jednoduchý obecný typ s dvěma parametry typu, jak použít třídy, rozhraní a zvláštní omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.

[Postupy: definování obecné metody pomocí reflexe generování](how-to-define-a-generic-method-with-reflection-emit.md)   
Ukazuje, jak vytvořit, generovat a vyvolání jednoduchou obecnou metodu.

[Kolekční sestavení pro generování dynamických typů](collectible-assemblies.md)   
Zavádí kolekční sestavení, které jsou dynamické sestavení, které může být uvolněno bez uvolnění domény aplikace, ve kterém byly vytvořeny.
  
## <a name="reference"></a>Odkaz  
 <xref:System.Reflection.Emit.OpCodes>  
 Katalogy kódy instrukce jazyka MSIL, které můžete použít k sestavení těl metod.  
  
 <xref:System.Reflection.Emit>  
 Obsahuje spravované třídy použít ke generování dynamických metod a sestavení, typy.  
  
 <xref:System.Type>  
 Popisuje <xref:System.Type> reflexe spravované třídy, která představuje typy v generování reflexe a který je klíčem k používání těchto technologií.  
  
 <xref:System.Reflection>  
 Obsahuje spravované třídy používané k prozkoumání metadata a spravovaný kód.  
  
## <a name="related-sections"></a>Související oddíly  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Vysvětluje, jak prozkoumat metadata a spravovaný kód.  
  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Poskytuje přehled sestavení v implementace .NET.
