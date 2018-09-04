---
title: typeof (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 2493e78fd0782eebee17afd979e1c429339d0a3f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529205"
---
# <a name="typeof-c-reference"></a>typeof (Referenční dokumentace jazyka C#)
Používá k získání `System.Type` pro typ objektu. A `typeof` výrazu má následující podobu:  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete získat run-time typu výrazu, můžete použít metodu rozhraní .NET Framework <xref:System.Object.GetType%2A>, jako v následujícím příkladu:  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 `typeof` Operátor nelze přetížit.  
  
 `typeof` Operátor můžete použít také u otevřených obecných typů. Typy s více než jeden parametr typu musí mít odpovídající počet čárek ve specifikaci. Následující příklad ukazuje, jak zjistit, jestli návratový typ metody je obecný <xref:System.Collections.Generic.IEnumerable%601>. <xref:System.Type.GetInterface%2A?displayProperty=nameWithType> Vrátí `null` návratový typ není-li <xref:System.Collections.Generic.IEnumerable%601> obecného typu.
  
 [!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]   
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Object.GetType%2A> metodu pro určení typu, který se používá pro jiné výsledek číselné výpočtu. To závisí na požadavky na úložiště z výsledné číslo.  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Type?displayProperty=nameWithType>  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [is](../../../csharp/language-reference/keywords/is.md)  
- [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)
