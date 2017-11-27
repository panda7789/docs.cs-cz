---
title: "Obecní delegáti (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1377723f18d6dd0e984538b530acbc7aa8d52feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generic-delegates-c-programming-guide"></a>Obecní delegáti (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) můžete definovat vlastní parametry typu. Kód, aby odkazy – obecný delegát typ argumentu zadat vytvoření uzavřené sestavené typu, stejně jako při vytvoření instance obecné třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 C# verze 2.0 má novou funkci s názvem skupiny převod metoda, která se vztahují na konkrétní, jakož i obecný delegát typy a umožňuje zapsat předchozí řádek zjednodušenou syntaxí:  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 Delegáti definované v rámci obecné třídy můžete použít parametry typu obecné třídy v stejným způsobem jako metody třídy.  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 Argument typu obsahující třídy, musíte zadat kód, který odkazuje na delegát následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 Obecní delegáti jsou zvláště užitečné při definování události podle typické návrhový vzor, protože argument odesílatele může být silného typu a již má být přetypovat do a z <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Obecné metody](../../../csharp/programming-guide/generics/generic-methods.md)  
 [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)  
 [Obecná rozhraní](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Obecné typy](~/docs/standard/generics/index.md)
