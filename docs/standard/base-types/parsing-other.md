---
title: Analýza jiných řetězců v rozhraní .NET
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
ms.openlocfilehash: 08e891501bbefcf8b32eff10dd7294af9d81adac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127576"
---
# <a name="parsing-other-strings-in-net"></a>Analýza jiných řetězců v rozhraní .NET
Kromě číselných <xref:System.DateTime> řetězců a řetězců můžete také analyzovat řetězce, <xref:System.Char> <xref:System.Boolean>které <xref:System.Enum> představují typy , a do datových typů.  
  
## <a name="char"></a>Char  
 Metoda statické analýzy přidružená k datovému typu **Char** je užitečná pro převod řetězce, který obsahuje jeden znak, na jeho hodnotu Unicode. Následující příklad kódu analyzuje řetězec do znaku Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Logická hodnota  
 **Logický** datový typ obsahuje metodu **Parse,** kterou můžete použít k převodu řetězce, který představuje logickou hodnotu na skutečný **logický** typ. Tato metoda není malá a velká písmena a můžete úspěšně analyzovat řetězec obsahující "True" nebo "False." Metoda **Parse** přidružená k **logickému** typu může také analyzovat řetězce, které jsou obklopeny bílými mezerami. Pokud je předán jiný <xref:System.FormatException> řetězec, je vyvolána.  
  
 Následující příklad kódu používá metodu **Parse** k převodu řetězce na logickou hodnotu.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Výčet  
 **StaticParse** metodu můžete použít k inicializaci typu výčtu na hodnotu řetězce. Tato metoda přijímá typ výčtu, který analyzujete, řetězec analyzovat a volitelný logický příznak označující, zda je analýza rozlišována malá a velká písmena. Řetězec, který analyzujete, může obsahovat několik hodnot oddělených čárkami, kterým může předcházet nebo za ním následovat jedna nebo více prázdných mezer (také nazývaných prázdné mezery). Pokud řetězec obsahuje více hodnot, hodnota vráceného objektu je hodnota všech zadaných hodnot v kombinaci s bitovou operací OR.  
  
 Následující příklad používá **Metodu Parse** k převodu řetězcové reprezentace na hodnotu výčtu. Výčet <xref:System.DayOfWeek> je inicializován na **čtvrtek** z řetězce.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Převod typu v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
