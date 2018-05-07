---
title: Obecné parametry typu (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 35029b90fb7b905a87055596cf8dcd6a84ef9d36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="generic-type-parameters-c-programming-guide"></a>Obecné parametry typu (Průvodce programováním v C#)
Parametry typu v obecného typu nebo definici metody, je zástupný symbol pro konkrétního typu klienta Určuje, kdy se vytvořit instanci proměnné obecného typu. Obecný třídy, jako například `GenericList<T>` uvedené v [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md), nelze použít jako-je, protože není skutečně typu; se víc podobá plán, podle kterého typu. Chcete-li použít `GenericList<T>`, kód klienta musí deklarovat a vytvořit instanci typu vytvořený tak, že zadáte argument typu v závorkách úhlu. Argument typu pro tuto konkrétní třídu mohou být jakéhokoli typu rozpoznán překladačem. Libovolný počet instancí vytvořený typ lze vytvořit, každé z nich pomocí jiného typu argument, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 V každé z těchto instancí `GenericList<T>`, všechny výskyty řetězce `T` ve třídě, bude nahrazena v době spuštění s argumentem typu. Prostřednictvím této nahrazení jsme vytvořili tři samostatné bezpečnost typů a efektivní objekty pomocí definice jednu třídu. Další informace o tom, jak toto nahrazení provádí pomocí modulu CLR najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Parametr typu pokyny pro pojmenování  
  
-   **Proveďte** název parametry obecného typu pomocí popisných názvů, pokud se název jednoho písmeno je zcela vlastní vysvětlujícím a popisný název nebude přidejte hodnotu.  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **Vezměte v úvahu** pomocí T jako název typu parametru pro typy s jeden parametr typu jedním písmenem.  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **Proveďte** předpony typ popisné názvy parametrů s "T".  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **Vezměte v úvahu** označující omezení vztahujících se na parametr typu názvu parametru. Například parametr omezená na `ISession` může být volána `TSession`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
 [Rozdíly mezi šablonami C++ a obecnými typy C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
