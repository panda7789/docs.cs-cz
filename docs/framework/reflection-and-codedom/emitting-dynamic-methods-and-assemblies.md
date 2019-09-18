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
ms.openlocfilehash: d8e2b9aeb8c632efcbf8c506da4da7c6e7b408e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046089"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Generování dynamických metod a sestavení

Tato část popisuje sadu spravovaných typů v <xref:System.Reflection.Emit> oboru názvů, které umožňují kompilátorům nebo nástrojům generovat metadata a jazyk MSIL (Microsoft Intermediate Language) za běhu a volitelně vygenerovat soubor přenositelného spustitelného souboru (PE) na disku. Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů. V této části je funkce poskytovaná <xref:System.Reflection.Emit> oborem názvů označována jako vygenerování reflexe.  
  
Vygenerování reflexe poskytuje následující možnosti:  
  
- Definujte zjednodušené globální metody za běhu, pomocí <xref:System.Reflection.Emit.DynamicMethod> třídy a spusťte je pomocí delegátů.  
  
- Definujte sestavení v době běhu a pak je spusťte nebo uložte na disk.  
  
- Definujte sestavení za běhu, spusťte je a pak je uvolněte a umožněte uvolnění paměti, aby bylo možné znovu získat své prostředky.  
  
- Definujte moduly v nových sestaveních za běhu a pak je spusťte nebo uložte na disk.  
  
- Definujte typy v modulech v době běhu, vytvořte instance těchto typů a volejte jejich metody.  
  
- Definujte symbolické informace pro definované moduly, které mohou být používány nástroji, jako jsou ladicí programy a profilery kódu.  
  
Kromě spravovaných typů v <xref:System.Reflection.Emit> oboru názvů existují nespravovaná rozhraní metadat, která jsou popsána v referenční dokumentaci [rozhraní metadat](../unmanaged-api/metadata/metadata-interfaces.md) . Spravované reflexe Emit poskytuje silnější sémantickou kontrolu chyb a vyšší úroveň abstrakce metadat než nespravované rozhraní metadat.  
  
Dalším užitečným prostředkem pro práci s metadaty a jazykem MSIL je dokumentace k Common Language Infrastructure (CLI), obzvláště "partition II: Definice metadat a sémantika "a" partition III: Sada instrukcí CIL Dokumentace je k dispozici online na webu [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) a na webu [ECMA](https://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>V tomto oddílu
  
[Problémy se zabezpečením v generování reflexe](security-issues-in-reflection-emit.md)  
Popisuje problémy se zabezpečením související s vytvářením dynamických sestavení pomocí generování reflexe.  

[Postupy: Definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md)   
Ukazuje, jak spustit jednoduchou dynamickou metodu a dynamickou metodu svázanou s instancí třídy.

[Postupy: Definování obecného typu pomocí generování reflexe](how-to-define-a-generic-type-with-reflection-emit.md)   
Ukazuje, jak vytvořit jednoduchý obecný typ se dvěma parametry typu, jak použít třídu, rozhraní a speciální omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.

[Postupy: Definování obecné metody pomocí generování reflexe](how-to-define-a-generic-method-with-reflection-emit.md)   
Ukazuje, jak vytvořit, vygenerovat a vyvolat jednoduchou obecnou metodu.

[Kolekční sestavení pro generování dynamického typu](collectible-assemblies.md)   
Zavádí kolekční sestavení, která jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byly vytvořeny.
  
## <a name="reference"></a>Reference  

<xref:System.Reflection.Emit.OpCodes>  
Zařadí do katalogu kódy instrukcí jazyka MSIL, které můžete použít k sestavení těla metody.  
  
<xref:System.Reflection.Emit>  
Obsahuje spravované třídy používané k vygenerování dynamických metod, sestavení a typů.  
  
<xref:System.Type>  
<xref:System.Type> Popisuje třídu, která představuje typy v spravovaných reflexích a reflexi Emit a který je klíčem k používání těchto technologií.  
  
<xref:System.Reflection>  
Obsahuje spravované třídy používané k prozkoumávání metadat a spravovaného kódu.  
  
## <a name="related-sections"></a>Související oddíly  

[Reflexe](reflection.md)  
Vysvětluje, jak prozkoumat metadata a spravovaný kód.  
  
[Sestavení v .NET](../../standard/assembly/index.md)  
Poskytuje přehled o sestaveních v implementacích rozhraní .NET.
