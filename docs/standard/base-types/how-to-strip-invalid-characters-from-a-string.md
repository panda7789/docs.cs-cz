---
title: 'Postupy: Odstranění neplatných znaků z řetězce'
description: Přečtěte si příklad, který ukazuje, jak odstranit potenciálně škodlivé znaky z řetězce pomocí metody static Regex. Replace.
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
ms.openlocfilehash: f9d671587d174a1eb2bb6a5dac24bdd0220be3dd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600825"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Postupy: Odstranění neplatných znaků z řetězce
Následující příklad používá statickou <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodu k odstranění neplatných znaků z řetězce.  
  
## <a name="example"></a>Příklad  
 `CleanInput`Metodu definovanou v tomto příkladu můžete použít k odstranění potenciálně škodlivých znaků, které byly zadány do textového pole, které přijímá vstup uživatele. V tomto případě `CleanInput` vyčerpá všechny nealfanumerické znaky kromě teček (.), symbolů (@) a spojovníky (-) a vrátí zbývající řetězec. Můžete však upravit vzor regulárního výrazu tak, aby vyčerpal všechny znaky, které by neměly být zahrnuty ve vstupním řetězci.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Vzor regulárního výrazu `[^\w\.@-]` odpovídá jakémukoli znaku, který není znakem slova, tečku, symbolem @ nebo spojovníkem. Znak slova je jakékoli písmeno, desítkovou číslici nebo konektor interpunkce, například podtržítko. Libovolný znak, který odpovídá tomuto vzoru, je nahrazen <xref:System.String.Empty?displayProperty=nameWithType> řetězcem, což je řetězec definovaný vzorem pro nahrazení. Chcete-li v uživatelském vstupu připustit další znaky, přidejte tyto znaky do třídy znaků ve vzoru regulárního výrazu. Například vzor regulárního výrazu `[^\w\.@-\\%]` také umožňuje symbol procenta a zpětné lomítko ve vstupním řetězci.  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy .NET](regular-expressions.md)
