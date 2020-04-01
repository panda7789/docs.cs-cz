---
title: Analýza řetězců v rozhraní .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 717022e5d2e292c1624e6155bd7571e4daa997b9
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523806"
---
# <a name="parsing-strings-in-net"></a>Analýza řetězců v rozhraní .NET
Operace analýzy převede řetězec, který představuje základní typ .NET na tento základní typ. Například operace analýzy se používá k převodu řetězce na číslo s plovoucí desetinnou tácem nebo na hodnotu data a času. Metoda nejčastěji používaná k provedení operace analýzy je `Parse` metoda. Vzhledem k tomu, že analýza je reverzní operace formátování (která zahrnuje převod základního typu na jeho řetězcovou reprezentaci), platí mnoho stejných pravidel a konvencí. Stejně jako formátování používá objekt, <xref:System.IFormatProvider> který implementuje rozhraní k poskytování informací o formátování citlivé na <xref:System.IFormatProvider> jazykovou verzi, analýza také používá objekt, který implementuje rozhraní k určení, jak interpretovat reprezentaci řetězce. Další informace najdete v článku o [typech formátování](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Analýza číselných řetězců](../../../docs/standard/base-types/parsing-numeric.md)  
 Popisuje převod řetězců na číselné typy rozhraní .NET.  
  
 [Analýza řetězců data a času](../../../docs/standard/base-types/parsing-datetime.md)  
 Popisuje, jak převést řetězce na typy .NET **DateTime.**  
  
 [Analýza jiných řetězců](../../../docs/standard/base-types/parsing-other.md)  
 Popisuje, jak převést řetězce na **typy Char**, **Boolean**a **Enum.**  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 Popisuje základní koncepty formátování, jako jsou specifikátory formátu a zprostředkovatelé formátů.  
  
 [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)  
 Popisuje, jak převést typy.
