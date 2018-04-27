---
title: 'Postupy: Inicializace objektů pomocí inicializátoru objektů (Průvodce programováním v C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8e9130983aabe991660ff4cca90b33609f86c158
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Postupy: Inicializace objektů pomocí inicializátoru objektů (Průvodce programováním v C#)
Inicializátory objektů můžete použít třeba inicializovat objekty typu deklarativní způsobem bez explicitně vyvolání konstruktor pro typ.  
  
 Následující příklady ukazují, jak pomocí pojmenovaných objektů inicializátory objektů. Procesy kompilátoru objekt inicializátory první přístup k výchozí konstruktor instance a pak zpracování inicializacích člen. Proto pokud výchozí konstruktor je deklarován jako `private` ve třídě, se nezdaří inicializátory objektů, které vyžadují veřejný přístup.  
  
 Pokud definujete anonymního typu, je nutné použít inicializátoru objektu. Další informace najdete v tématu [postupy: vrácení podmnožin z vlastností elementů v dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k chybě při inicializaci novou `StudentName` typu pomocí inicializátory objektů.  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k chybě při inicializaci kolekce `StudentName` typy pomocí inicializátoru kolekce. Všimněte si, že inicializátoru kolekce řadu inicializátory objektů oddělených čárkami.  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud chcete spustit tento kód, zkopírujte a vložte třídy do Visual C# projektu konzolové aplikace vytvořené v sadě Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
