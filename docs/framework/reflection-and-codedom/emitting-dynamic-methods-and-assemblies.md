---
title: Generování dynamických metod a sestavení
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 578851bed188921324e3c25e533b3466068dee3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446781"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Generování dynamických metod a sestavení

Tato část popisuje sadu spravovaných typů v oboru názvů <xref:System.Reflection.Emit>, který umožňuje kompilátorům nebo nástrojům generovat metadata a jazyk MSIL (Microsoft Intermediate Language) v době běhu a volitelně vygenerovat přenosný spustitelný soubor (PE) na disku. Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů. V této části je funkce poskytovaná oborem názvů <xref:System.Reflection.Emit> označována jako vygenerování reflexe.  
  
Vygenerování reflexe poskytuje následující možnosti:  
  
- Definujte zjednodušené globální metody za běhu, pomocí třídy <xref:System.Reflection.Emit.DynamicMethod> a spusťte je pomocí delegátů.  
  
- Definujte sestavení v době běhu a pak je spusťte nebo uložte na disk.  
  
- Definujte sestavení za běhu, spusťte je a pak je uvolněte a umožněte uvolnění paměti, aby bylo možné znovu získat své prostředky.  
  
- Definujte moduly v nových sestaveních za běhu a pak je spusťte nebo uložte na disk.  
  
- Definujte typy v modulech v době běhu, vytvořte instance těchto typů a volejte jejich metody.  
  
- Definujte symbolické informace pro definované moduly, které mohou být používány nástroji, jako jsou ladicí programy a profilery kódu.  
  
Kromě spravovaných typů v oboru názvů <xref:System.Reflection.Emit> existují nespravovaná rozhraní metadat, která jsou popsána v referenční dokumentaci [rozhraní metadat](../unmanaged-api/metadata/metadata-interfaces.md) . Spravované reflexe Emit poskytuje silnější sémantickou kontrolu chyb a vyšší úroveň abstrakce metadat než nespravované rozhraní metadat.  
  
Dalším užitečným prostředkem pro práci s metadaty a jazykem MSIL je dokumentace Common Language Infrastructure (CLI), zejména oddíl II: definice metadat a sémantika a oddíl III: sada instrukcí CIL. Dokumentace je k dispozici online na webu [ECMA](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="in-this-section"></a>V tomto oddílu
  
[Problémy se zabezpečením v generování reflexe](security-issues-in-reflection-emit.md)  
Popisuje problémy se zabezpečením související s vytvářením dynamických sestavení pomocí generování reflexe.  

[Postupy: definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md)   
Ukazuje, jak spustit jednoduchou dynamickou metodu a dynamickou metodu svázanou s instancí třídy.

[Postupy: definování obecného typu pomocí generování reflexe](how-to-define-a-generic-type-with-reflection-emit.md)   
Ukazuje, jak vytvořit jednoduchý obecný typ se dvěma parametry typu, jak použít třídu, rozhraní a speciální omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.

[Postupy: definování obecné metody pomocí generování reflexe](how-to-define-a-generic-method-with-reflection-emit.md)   
Ukazuje, jak vytvořit, vygenerovat a vyvolat jednoduchou obecnou metodu.

[Kolekční sestavení pro generování dynamického typu](collectible-assemblies.md)   
Zavádí kolekční sestavení, která jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byly vytvořeny.
  
## <a name="reference"></a>Odkaz  

<xref:System.Reflection.Emit.OpCodes>  
Zařadí do katalogu kódy instrukcí jazyka MSIL, které můžete použít k sestavení těla metody.  
  
<xref:System.Reflection.Emit>  
Obsahuje spravované třídy používané k vygenerování dynamických metod, sestavení a typů.  
  
<xref:System.Type>  
Popisuje třídu <xref:System.Type>, která představuje typy v spravované reflexi a vyřazení reflexe a který je klíčem k použití těchto technologií.  
  
<xref:System.Reflection>  
Obsahuje spravované třídy používané k prozkoumávání metadat a spravovaného kódu.  
  
## <a name="related-sections"></a>Související oddíly  

[Reflexe](reflection.md)  
Vysvětluje, jak prozkoumat metadata a spravovaný kód.  
  
[Sestavení v .NET](../../standard/assembly/index.md)  
Poskytuje přehled o sestaveních v implementacích rozhraní .NET.
