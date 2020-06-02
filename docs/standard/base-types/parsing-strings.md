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
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277411"
---
# <a name="parsing-strings-in-net"></a>Analýza řetězců v .NET
Operace analýzy převede řetězec, který představuje základní typ .NET, do tohoto základního typu. Například operace analýzy slouží k převodu řetězce na číslo s plovoucí desetinnou čárkou nebo na hodnotu data a času. Metoda, která se nejčastěji používá k provedení operace analýzy, je `Parse` metoda. Vzhledem k tomu, že analýza je reverzní operace formátování (která zahrnuje převod základního typu na jeho řetězcové vyjádření), platí celá řada stejných pravidel a konvencí. Stejně jako formátování používá objekt, který implementuje <xref:System.IFormatProvider> rozhraní k poskytnutí informací o formátování zohledňující jazykovou verzi, analýza také používá objekt, který implementuje <xref:System.IFormatProvider> rozhraní k určení, jak interpretovat řetězcovou reprezentaci. Další informace najdete v článku o [typech formátování](formatting-types.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Analýza číselných řetězců](parsing-numeric.md)  
 Popisuje, jak převést řetězce na číselné typy .NET.  
  
 [Analýza řetězců data a času](parsing-datetime.md)  
 Popisuje, jak převést řetězce na typy **DateTime** .NET.  
  
 [Analýza jiných řetězců](parsing-other.md)  
 Popisuje, jak převést řetězce na typy **char**, **Boolean**a **Enum** .  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy formátování](formatting-types.md)  
 Popisuje základní koncepty formátování, jako jsou specifikátory formátu a poskytovatelé formátu.  
  
 [Převod typu v .NET](type-conversion.md)  
 Popisuje, jak převést typy.
