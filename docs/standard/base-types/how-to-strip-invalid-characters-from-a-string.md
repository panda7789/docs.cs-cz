---
title: 'Postupy: Odstranění neplatných znaků z řetězce'
description: Přečtěte si příklad, který ukazuje, jak odstranit potenciálně škodlivé znaky z řetězce pomocí metody static Regex. Replace.
ms.date: 06/30/2020
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
ms.openlocfilehash: 5e0cd423df7fce03cdefb3da7bc192f3045e8f9c
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803986"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Postupy: Odstranění neplatných znaků z řetězce
Následující příklad používá statickou <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodu k odstranění neplatných znaků z řetězce.  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>Příklad  
 `CleanInput`Metodu definovanou v tomto příkladu můžete použít k odstranění potenciálně škodlivých znaků, které byly zadány do textového pole, které přijímá vstup uživatele. V tomto případě `CleanInput` vyčerpá všechny nealfanumerické znaky kromě teček (.), symbolů (@) a spojovníky (-) a vrátí zbývající řetězec. Můžete však upravit vzor regulárního výrazu tak, aby vyčerpal všechny znaky, které by neměly být zahrnuty ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Vzor regulárního výrazu `[^\w\.@-]` odpovídá jakémukoli znaku, který není znakem slova, tečku, symbolem @ nebo spojovníkem. Znak slova je jakékoli písmeno, desítkovou číslici nebo konektor interpunkce, například podtržítko. Libovolný znak, který odpovídá tomuto vzoru, je nahrazen <xref:System.String.Empty?displayProperty=nameWithType> řetězcem, což je řetězec definovaný vzorem pro nahrazení. Chcete-li v uživatelském vstupu připustit další znaky, přidejte tyto znaky do třídy znaků ve vzoru regulárního výrazu. Například vzor regulárního výrazu `[^\w\.@-\\%]` také umožňuje symbol procenta a zpětné lomítko ve vstupním řetězci.  
  
## <a name="see-also"></a>Viz také:

- [Regulární výrazy .NET](regular-expressions.md)
