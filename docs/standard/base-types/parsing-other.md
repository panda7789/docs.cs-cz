---
title: Analýza jiných řetězců v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85bb6dcdaa198b6b038cc80e1e38fa7d11123678
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086378"
---
# <a name="parsing-other-strings-in-net"></a>Analýza jiných řetězců v .NET
Kromě číselné a <xref:System.DateTime> řetězce, můžete také analyzovat řetězců, které představují typy <xref:System.Char>, <xref:System.Boolean>, a <xref:System.Enum> do datových typů.  
  
## <a name="char"></a>Char  
 Statické analýzy metodu spojenou s **Char** datový typ je vhodný pro převod řetězce, který obsahuje jeden znak na jeho hodnotu Unicode. Následující příklad analyzuje řetězec do znaku Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boolean  
 **Logická** obsahuje datový typ **analyzovat** metodu, která můžete použít k převodu řetězec, který představuje logickou hodnotu do skutečný **logická** typu. Tato metoda není velká a malá písmena a lze úspěšnou analýzu řetězce obsahující "True" nebo "False". **Analyzovat** metodu spojenou s **logická** typu můžete také analyzovat řetězce, které jsou uzavřeny v prázdné znaky. Pokud je předán jiný řetězec, <xref:System.FormatException> je vyvolána výjimka.  
  
 Následující příklad kódu používá **analyzovat** způsobů, jak převést řetězec na hodnotu typu Boolean.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Výčet  
 Můžete použít statické **analyzovat** metody k inicializaci typu výčtu na hodnotu řetězce. Tato metoda přijímá typ výčtu, která analyzujete, řetězec určený k analýze a volitelný příznak logické hodnoty označující, jestli je parsování malá a velká písmena. Řetězec, který se analýza může obsahovat několik hodnot oddělených čárkami, které mohou být předcházen nebo následován mezerami nejmíň jeden prázdný (také nazývané prázdné znaky). Pokud řetězec obsahuje více hodnot, hodnota vráceného objektu je hodnota všechny zadané hodnoty v kombinaci s bitová operace OR.  
  
 V následujícím příkladu **analyzovat** způsobů, jak převést řetězcové vyjádření na hodnotu výčtu. <xref:System.DayOfWeek> Výčtu je inicializován na **čtvrtek** z řetězce.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)  
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
- [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
