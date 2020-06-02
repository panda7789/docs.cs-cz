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
ms.openlocfilehash: a3503e0e499c6010fcc3d8669fa5c1eaf2dbf570
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277541"
---
# <a name="parsing-other-strings-in-net"></a>Analýza jiných řetězců v .NET
Kromě čísel a <xref:System.DateTime> řetězců můžete také analyzovat řetězce, které reprezentují typy <xref:System.Char> , <xref:System.Boolean> a <xref:System.Enum> do datových typů.  
  
## <a name="char"></a>Char  
 Statická metoda Parse spojená s datovým typem **char** je užitečná pro převod řetězce, který obsahuje jeden znak na jeho hodnotu Unicode. Následující příklad kódu analyzuje řetězec na znak Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Logická hodnota  
 Datový typ **Boolean** obsahuje metodu **Parse** , kterou můžete použít k převodu řetězce reprezentujícího logickou hodnotu na skutečný typ **Boolean** . Tato metoda nerozlišuje velká a malá písmena a může úspěšně analyzovat řetězec obsahující "true" nebo "false". Metoda **Parse** přidružená k typu **Boolean** může také analyzovat řetězce, které jsou obklopeny prázdnými znaky. Pokud je předán jakýkoli jiný řetězec, <xref:System.FormatException> je vyvolána výjimka.  
  
 Následující příklad kódu používá metodu **Parse** pro převod řetězce na logickou hodnotu.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Výčet  
 Metodu statické **analýzy** lze použít k inicializaci typu výčtu na hodnotu řetězce. Tato metoda přijímá typ výčtu, který analyzujete, řetězec k analýze a volitelný logický příznak označující, zda se při analýze rozlišují velká a malá písmena. Řetězec, který analyzujete, může obsahovat několik hodnot oddělených čárkami, které mohou být uvozeny nebo následovány jedním nebo více prázdnými mezerami (označují se také jako prázdné znaky). Pokud řetězec obsahuje více hodnot, hodnota vráceného objektu je hodnota všech zadaných hodnot v kombinaci s bitovou operací nebo.  
  
 Následující příklad používá metodu **Parse** pro převod řetězcové reprezentace na hodnotu výčtu. <xref:System.DayOfWeek>Výčet je inicializován pro **čtvrtek** z řetězce.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [Analýza řetězců](parsing-strings.md)
- [Typy formátování](formatting-types.md)
- [Převod typu v .NET](type-conversion.md)
