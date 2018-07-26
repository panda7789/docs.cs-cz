---
title: 'Postupy: Inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: b8c44ebbdc89d72398c3380d708b45d0b7dfdad3
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198455"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Postupy: Inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)
A <xref:System.Collections.Generic.Dictionary`2> obsahuje kolekci dvojic klíč/hodnota. Jeho <xref:System.Collections.Generic.Dictionary`2.Add*> metoda přebírá dva parametry, jeden pro klíč a jeden pro hodnotu. Inicializace <xref:System.Collections.Generic.Dictionary`2>, nebo jakoukoli kolekci jehož `Add` metoda přijímá několik parametrů, uzavřete do složených závorek každou sadu parametrů, jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu <xref:System.Collections.Generic.Dictionary`2> je inicializován pomocí instance typu `StudentName`.  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 Všimněte si dvě dvojice složených závorek v jednotlivých prvcích objektu kolekce. Vnitřní závorky uzavřete inicializátor objektu pro `StudentName`, a uzavřete inicializátor pro dvojice klíč/hodnota, která se přidá do vnějšího složené závorky `students` <xref:System.Collections.Generic.Dictionary`2>. Nakonec celé kolekce inicializátor slovníku uzavřen ve složených závorkách.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód spustit, zkopírujte a vložte třídy v jazyce Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio. Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a using pro System.Linq. Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
