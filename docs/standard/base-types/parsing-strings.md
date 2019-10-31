---
title: Analýza řetězců v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084318"
---
# <a name="parsing-strings-in-net"></a>Analýza řetězců v .NET
Operace analýzy převede řetězec, který představuje základní typ .NET, do tohoto základního typu. Například operace analýzy slouží k převodu řetězce na číslo s plovoucí desetinnou čárkou nebo na hodnotu data a času. Metoda, která se nejčastěji používá k provedení operace analýzy, je `Parse` metoda. Vzhledem k tomu, že analýza je reverzní operace formátování (která zahrnuje převod základního typu na jeho řetězcové vyjádření), platí celá řada stejných pravidel a konvencí. Stejně jako formátování používá objekt, který implementuje rozhraní <xref:System.IFormatProvider> k poskytnutí informací o formátování zohledňující jazykovou verzi, analýza také používá objekt, který implementuje rozhraní <xref:System.IFormatProvider> k určení toho, jak interpretovat řetězcovou reprezentaci. Další informace najdete v tématu [formátování typů](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Analýza číselných řetězců](../../../docs/standard/base-types/parsing-numeric.md)  
 Popisuje, jak převést řetězce na číselné typy .NET.  
  
 [Analýza řetězců data a času](../../../docs/standard/base-types/parsing-datetime.md)  
 Popisuje, jak převést řetězce na typy **DateTime** .NET.  
  
 [Analýza jiných řetězců](../../../docs/standard/base-types/parsing-other.md)  
 Popisuje, jak převést řetězce na typy **char**, **Boolean**a **Enum** .  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 Popisuje základní koncepty formátování, jako jsou specifikátory formátu a poskytovatelé formátu.  
  
 [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)  
 Popisuje, jak převést typy.  
  
 [Základní typy](../../../docs/standard/base-types/index.md)  
 Popisuje běžné operace, které lze provádět na základních typech .NET.
