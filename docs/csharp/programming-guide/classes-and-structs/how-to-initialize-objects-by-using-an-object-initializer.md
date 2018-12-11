---
title: 'Postupy: Inicializace objektů pomocí objektu inicializátoru - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 82efa751ad70fd2741ec2e306f56f2be06abad11
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244987"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Postupy: Inicializace objektů pomocí inicializátoru objektů (C# Průvodce programováním v)
Inicializátory objektů můžete použít třeba inicializovat objekty typu bez explicitní volání konstruktoru pro typ deklarativní způsobem.  
  
 Následující příklady ukazují, jak používat inicializátory objektů s pojmenovaných objektů. Procesy, které kompilátor inicializátorech objektu tak, že první přístup k výchozí konstruktor instance a potom zpracování inicializace člena. Proto pokud výchozí konstruktor je deklarován jako `private` ve třídě, se nezdaří inicializátory objektů, které vyžadují přístup public.  
  
 Pokud definujete anonymního typu je nutné použít inicializátor objektu. Další informace najdete v tématu [jak: Vrácení podmnožin vlastností elementu v dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob inicializace nového `StudentName` typu pomocí inicializátory objektů.  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob inicializace kolekce `StudentName` typy pomocí inicializátoru kolekce. Všimněte si, že inicializátoru kolekce je řada inicializátory objektů s hodnotami oddělenými čárkou.  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód spustit, zkopírujte a vložte třídy v jazyce Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
