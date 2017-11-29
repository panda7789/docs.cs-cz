---
title: "Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)
Následující příklad používá ukazatele kopírování bajtů z jednoho pole do jiné.  
  
 Tento příklad používá [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo, které vám umožní použít ukazatele v `Copy` metoda. [Pevné](../../../csharp/language-reference/keywords/fixed-statement.md) příkaz se používá k deklaraci ukazatele na zdrojové a cílové pole. To *PIN* umístění zdrojové a cílové maticových v paměti, aby nebude možné přesunout podle uvolňování paměti. Bloky paměti pro pole jsou Odepnout, kdy `fixed` blok dokončení. Protože `Copy` metoda v tomto příkladu používá `unsafe` – klíčové slovo, se musí být zkompilovány s **/ unsafe** – možnost kompilátoru. Pokud chcete nastavit možnost v sadě Visual Studio, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**. Na **sestavení** vyberte **povolit nezabezpečený kód**.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [/ unsafe (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [Uvolňování paměti](../../../standard/garbage-collection/index.md)
