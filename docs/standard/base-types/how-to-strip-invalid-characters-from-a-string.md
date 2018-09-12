---
title: 'Postupy: Odstranění neplatných znaků z řetězce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3bbd25e40607bd316f1bbab974174fe5433770f
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44510753"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Postupy: Odstranění neplatných znaků z řetězce
Následující příklad používá statickou <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodu k odstranění neplatných znaků z řetězce.  
  
## <a name="example"></a>Příklad  
 Můžete použít `CleanInput` metody definované v tomto příkladu pro odstranění potenciálně nebezpečné znaky zadané do textového pole, která přijímá vstup uživatele. V takovém případě `CleanInput` odstraní všechny nealfanumerické znaky s výjimkou tečky (.), symbolů (@), spojovníky (-) a vrátí zbývající řetězec. Vzor regulárního výrazu, ale můžete upravit tak, aby se odstraní všechny znaky, které by neměly být obsažené ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Vzor regulárního výrazu `[^\w\.@-]` odpovídá jakémukoli znaku, který není znakem slova, tečky, symbolu @ nebo pomlčkou. Znak slova je libovolný písmeno, desítková číslice nebo interpunkční znaménka konektoru, jako je například podtržítko. Libovolný znak, který odpovídá tomuto vzoru nahrazuje <xref:System.String.Empty?displayProperty=nameWithType>, což je řetězec určené vzor pro nahrazení. Povolit další znaky ve vstupu uživatele, přidejte do třídy znak ve vzorku regulárního výrazu znaky. Například vzor regulárního výrazu `[^\w\.@-\\%]` také umožňuje symbol procenta a zpětné lomítko ve vstupním řetězci.  
  
## <a name="see-also"></a>Viz také:

- [Regulárních výrazů .NET](../../../docs/standard/base-types/regular-expressions.md)
