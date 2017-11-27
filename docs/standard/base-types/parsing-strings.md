---
title: "Analýza řetězců v rozhraní .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 811db42e04e73d7acbc03e303297b19fdf643384
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-strings-in-net"></a>Analýza řetězců v rozhraní .NET
Operaci analýzy převede řetězec, který představuje základní typ rozhraní .NET do základního typu. Operaci analýzy se například používá převést řetězec na číslo s plovoucí desetinnou čárkou nebo na hodnotu data a času. Metoda nejčastěji používaná k provedení analýzy operace je `Parse` metoda. Protože analýza je reverzní operace formátování (která zahrnuje převodu základní typ jeho řetězcovou reprezentaci), řadu stejné pravidla a pravidla týkající se použití. Jenom jako formátování používá objekt, který implementuje <xref:System.IFormatProvider> poskytovat informace formátování jazykové verzi, analýza také používá objekt, který implementuje rozhraní <xref:System.IFormatProvider> rozhraní určit, jak interpretovat reprezentaci řetězce . Další informace najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Analýza číselných řetězců](../../../docs/standard/base-types/parsing-numeric.md)  
 Popisuje, jak převést řetězce na číselné typy .NET.  
  
 [Analýza řetězců data a času](../../../docs/standard/base-types/parsing-datetime.md)  
 Popisuje, jak převést řetězce na rozhraní .NET **data a času** typy.  
  
 [Analýza jiných řetězců](../../../docs/standard/base-types/parsing-other.md)  
 Popisuje, jak převést do řetězce **Char**, **Boolean**, a **výčtu** typy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 Popisuje základní principy formátování jako specifikátory formátu a zprostředkovatelé formátu.  
  
 [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)  
 Popisuje, jak pro převod typů.  
  
 [Základní typy](../../../docs/standard/base-types/index.md)  
 Popisuje běžné operace, které můžete provádět na základní typy .NET.
