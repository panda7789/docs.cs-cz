---
title: Generování dynamických metod a sestavení
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180531"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Generování dynamických metod a sestavení

Tato část popisuje sadu spravovaných typů v oboru <xref:System.Reflection.Emit> názvů, které umožňují kompilátoru nebo nástroji vyzařovat metadata a zprostředkující jazyk Microsoft (MSIL) za běhu a volitelně generovat přenosný spustitelný soubor (PE) na disku. Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů. V této části funkce poskytované obor <xref:System.Reflection.Emit> názvů se označuje jako odraz emit.  
  
Reflexe vyzařují poskytuje následující funkce:  
  
- Definujte zjednodušené globální metody <xref:System.Reflection.Emit.DynamicMethod> za běhu pomocí třídy a spusťte je pomocí delegátů.  
  
- Definujte sestavení za běhu a pak je spusťte a/nebo je uložte na disk.  
  
- Definujte sestavení za běhu, spusťte je a pak je uvolněte a povolte uvolnění paměti pro uvolnění jejich prostředků.  
  
- Definujte moduly v nových sestaveních za běhu a potom je spusťte a/nebo je uložte na disk.  
  
- Definujte typy v modulech za běhu, vytvořte instance těchto typů a vyvolat jejich metody.  
  
- Definujte symbolické informace pro definované moduly, které mohou být použity nástroji, jako jsou ladicí programy a profilovací programy kódu.  
  
Kromě spravovaných typů <xref:System.Reflection.Emit> v oboru názvů existují nespravovaná metadata rozhraní, které jsou popsány v dokumentaci metadat [rozhraní](../unmanaged-api/metadata/metadata-interfaces.md) referenční. Spravovaný odraz emit poskytuje silnější sémantické kontroly chyb a vyšší úroveň abstrakce metadat než nespravované metadata rozhraní.  
  
Dalším užitečným zdrojem informací pro práci s metadaty a jazykem MSIL je dokumentace common language infrastructure (CLI), zejména "Partition II: Metadata Definition and Sémantics" a "Partition III: CIL Instruction Set". Dokumentace je k dispozici online na [webových stránkách společnosti Ecma](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="in-this-section"></a>V tomto oddílu
  
[Bezpečnostní otázky v reflexi vyzařují](security-issues-in-reflection-emit.md)  
Popisuje problémy se zabezpečením související s vytvářením dynamických sestavení pomocí odrazu vyzařovat.  

[Postup: Definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md) Ukazuje, jak provést jednoduchou dynamickou metodu a dynamickou metodu vázanou na instanci třídy.

[Postup: Definování obecného typu s odrazem emitují](how-to-define-a-generic-type-with-reflection-emit.md) Ukazuje, jak vytvořit jednoduchý obecný typ se dvěma parametry typu, jak použít třídu, rozhraní a speciální omezení parametrů typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.

[Postup: Definování obecné metody s odrazem vyzařovat](how-to-define-a-generic-method-with-reflection-emit.md) Ukazuje, jak vytvořit, vyzařovat a vyvolat jednoduchou obecnou metodu.

[Sběratelské sestavy pro dynamické generování typů](collectible-assemblies.md) Zavádí sběratelská sestavení, což jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byla vytvořena.
  
## <a name="reference"></a>Referenční informace  

<xref:System.Reflection.Emit.OpCodes>  
Katalogy kódy instrukcí MSIL, které můžete použít k sestavení těla metod.  
  
<xref:System.Reflection.Emit>  
Obsahuje spravované třídy používané k emitování dynamických metod, sestavení a typů.  
  
<xref:System.Type>  
Popisuje třídu, <xref:System.Type> která představuje typy ve spravované reflexe a odrazu vyzařovat a který je klíčem k použití těchto technologií.  
  
<xref:System.Reflection>  
Obsahuje spravované třídy používané k prozkoumání metadat a spravovaného kódu.  
  
## <a name="related-sections"></a>Související oddíly  

[Reflexe](reflection.md)  
Vysvětluje, jak prozkoumat metadata a spravovaný kód.  
  
[Sestavení v .NET](../../standard/assembly/index.md)  
Poskytuje přehled sestavení v implementacích rozhraní .NET.
