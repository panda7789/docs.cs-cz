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
ms.openlocfilehash: 7becf993db866e24381fe9013c82d74dd91ee9a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568027"
---
# <a name="parsing-other-strings-in-net"></a>Analýza jiných řetězců v .NET
Kromě číselný a <xref:System.DateTime> řetězce, můžete také analyzovat řetězců, které představují typy <xref:System.Char>, <xref:System.Boolean>, a <xref:System.Enum> do datových typů.  
  
## <a name="char"></a>Char  
 Přidružená metoda statické analýzy **Char** datový typ je vhodný pro převod řetězce, který obsahuje jediný znak na jeho hodnotu Unicode. Následující příklad kódu analyzuje řetězec do znak Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boolean  
 **Boolean** obsahuje datový typ **analyzovat** metodu, kterou můžete použít se převést řetězec, který představuje logickou hodnotu na skutečné třídě **Boolean** typu. Tato metoda není velká a malá písmena a mohou úspěšně analyzovat řetězec obsahující "True" nebo "Nepravda". **Analyzovat** přidružená metoda **Boolean** typ může také analyzovat řetězce, které jsou ohraničeny prázdnými znaky. Pokud je předán jakýkoli jiný řetězec, <xref:System.FormatException> je vyvolána výjimka.  
  
 Následující příklad kódu používá **analyzovat** metoda převést řetězec na logickou hodnotu.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Výčet  
 Můžete použít statickou **analyzovat** metoda pro inicializaci typ výčtu na hodnotu řetězce. Tato metoda přijímá typ výčtu, který analyzujete, řetězec, který má analyzovat a volitelný logický příznak, která udává, zda je analýzy malá a velká písmena. Řetězec, který analyzujete může obsahovat několik hodnot oddělených čárkami, které mohou být před nebo za nímž následuje jeden nebo více prázdný mezery (také nazývané prázdné znaky). Pokud řetězec obsahuje více hodnot, hodnota vráceného objektu je hodnota všech zadaných hodnot v kombinaci s bitové operace OR.  
  
 Následující příklad používá **analyzovat** způsobů, jak převést řetězcovou reprezentaci na hodnotu výčtu. <xref:System.DayOfWeek> Výčtu je inicializováno **čtvrtek** z řetězce.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
