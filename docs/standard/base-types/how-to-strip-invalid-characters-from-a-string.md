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
ms.openlocfilehash: cc90e6609f9335b7e2f08271e5540b182901e8c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127656"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Postupy: Odstranění neplatných znaků z řetězce
Následující příklad používá <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> statickou metodu k odstranění neplatných znaků z řetězce.  
  
## <a name="example"></a>Příklad  
 Metodu definovanou `CleanInput` v tomto příkladu můžete použít k odstranění potenciálně škodlivých znaků, které byly zadány do textového pole, které přijímá vstup uživatele. V tomto `CleanInput` případě odstraní všechny nealfanumerické znaky kromě tečky (.), na symboly (@) a pomlčky (-) a vrátí zbývající řetězec. Vzor regulárního výrazu však můžete upravit tak, aby odstraňul všechny znaky, které by neměly být zahrnuty do vstupního řetězce.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Vzor regulárního výrazu `[^\w\.@-]` odpovídá libovolnému znaku, který není znakem slova, tečkou, symbolem @ nebo pomlčkou. Znak slova je libovolné písmeno, desetinná číslice nebo interpunkční spojnice, například podtržítko. Libovolný znak, který odpovídá tomuto vzoru, je nahrazen řetězcem <xref:System.String.Empty?displayProperty=nameWithType>definovaným náhradním vzorem. Chcete-li povolit další znaky v uživatelském vstupu, přidejte tyto znaky do třídy znaků ve vzoru regulárního výrazu. Například vzor `[^\w\.@-\\%]` regulárního výrazu také umožňuje symbol procenta a zpětné lomítko ve vstupním řetězci.  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
