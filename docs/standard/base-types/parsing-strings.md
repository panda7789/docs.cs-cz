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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e0e7e69affd93320ec3f3d73e6254befaf6ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765996"
---
# <a name="parsing-strings-in-net"></a>Analýza řetězců v .NET
Operace analýzy převede řetězec, který představuje základní typ formátu .NET do základního typu. Například operace analýzy slouží k převedení řetězce na číslo s plovoucí desetinnou čárkou nebo na hodnotu data a času. Metoda nejčastěji používá k provedení operace analýzy je `Parse` metody. Protože je analýza reverzní operaci formátování (který zahrnuje převod základního typu na jeho řetězcovou reprezentaci), řadu stejných pravidel a konvence použít. Stejně jako formátování používá objekt, který implementuje <xref:System.IFormatProvider> poskytovat informace formátování zohledňující jazykovou verzi, analýze také používá objekt, který implementuje rozhraní <xref:System.IFormatProvider> rozhraní zjistěte, jak interpretovat řetězcové vyjádření . Další informace najdete v tématu [Formatting Types](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Analýza číselných řetězců](../../../docs/standard/base-types/parsing-numeric.md)  
 Popisuje, jak převod řetězců na numerické typy .NET.  
  
 [Analýza řetězců data a času](../../../docs/standard/base-types/parsing-datetime.md)  
 Popisuje, jak převod řetězců na .NET **data a času** typy.  
  
 [Analýza jiných řetězců](../../../docs/standard/base-types/parsing-other.md)  
 Popisuje, jak převést řetězců do **Char**, **logická**, a **výčtu** typy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 Popisuje základní principy formátování jako specifikátory formátu a poskytovatelů formátu.  
  
 [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)  
 Popisuje, jak převod typů.  
  
 [Základní typy](../../../docs/standard/base-types/index.md)  
 Popisuje běžné operace, které můžete provádět na základní typy .NET.
