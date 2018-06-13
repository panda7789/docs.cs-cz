---
title: 'Postupy: Inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: b8c44ebbdc89d72398c3380d708b45d0b7dfdad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324171"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Postupy: Inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)
A <xref:System.Collections.Generic.Dictionary`2> obsahuje kolekci dvojic klíč/hodnota. Jeho <xref:System.Collections.Generic.Dictionary`2.Add*> metoda přebírá dva parametry: jeden pro klíč a jeden pro hodnotu. K chybě při inicializaci <xref:System.Collections.Generic.Dictionary`2>, nebo jakoukoli kolekci, jejichž `Add` metoda přijímá několik parametrů, uzavřete každou sadu parametrů do složených závorek, jak je znázorněno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu <xref:System.Collections.Generic.Dictionary`2> je inicializovat pomocí instance typu `StudentName`.  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 Všimněte si dvě dvojice složených závorek v každý prvek kolekce. Nejvnitřnější složené závorky uzavřete inicializátoru objektu pro `StudentName`, a nejkrajnější složené závorky uzavřete inicializátoru pro dvojice klíč/hodnota, který bude přidán do `students` <xref:System.Collections.Generic.Dictionary`2>. Nakonec inicializátoru celou kolekci pro slovník je uzavřené do složených závorek.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud chcete spustit tento kód, zkopírujte a vložte třídy do Visual C# projektu konzolové aplikace vytvořené v sadě Visual Studio. Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a pomocí direktivy pro System.Linq. Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
