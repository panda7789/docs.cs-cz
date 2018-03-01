---
title: "Postupy: Změna obsahu řetězce (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b0810d5722c2c32f7884187bb2e3fc5a039825c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-string-contents-c-programming-guide"></a>Postupy: Změna obsahu řetězce (Průvodce programováním v C#)
Protože jsou řetězce *neměnné*, není možné (bez použití nezabezpečený kód) změnit hodnotu řetězce objektu po jeho vytvoření. Ale existuje mnoho způsobů můžete upravit hodnotu řetězce a uložit výsledek do nový objekt řetězce. <xref:System.String?displayProperty=nameWithType> Třída poskytuje metody, které působí na vstup řetězec a vrátí nový objekt řetězce. V mnoha případech můžete přiřadit nový objekt do proměnné, která uchovávat původního řetězce. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Třída poskytuje další metody, které pracují podobným způsobem. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Třída poskytuje znak vyrovnávací paměti, který můžete upravit "na místě." Volání <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metodu pro vytvoření nového objektu řetězce, který obsahuje obsah aktuální vyrovnávací paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby, jak nahradit nebo odebrat dílčích řetězců v zadaný řetězec.  
  
 [!code-csharp[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a>Příklad  
 Pro přístup k jednotlivé znaky v řetězci pomocí pole zápisu, můžete použít <xref:System.Text.StringBuilder> objekt, který přetížení `[]` operátor poskytnout přístup k jeho vnitřní znak vyrovnávací paměti. Také můžete převést řetězec na pole znaků pomocí <xref:System.String.ToCharArray%2A> metoda. Následující příklad používá `ToCharArray` vytvořte pole. Některé prvky tohoto pole lze poté upravit. Řetězec konstruktor, který přebírá char pole jako vstupní parametr je pak volat za účelem vytvoření nové řetězce.  
  
 [!code-csharp[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se poskytuje pro tyto velmi výjimečných případech, ve kterých můžete chtít změnit řetězec na místě v nezabezpečený kód v podobně jako při pole char stylu jazyka C. Příklad ukazuje, jak získat přístup k jednotlivé znaky "místní" pomocí fixed – klíčové slovo. Také ukazuje jeden možný vedlejším účinkem nebezpečné operace s řetězci která je výsledkem způsob kompilátor jazyka C# interně ukládá řetězce (učně). Obecně byste neměli používat tato technika, pokud to není nezbytně nutné.  
  
 [!code-csharp[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)
