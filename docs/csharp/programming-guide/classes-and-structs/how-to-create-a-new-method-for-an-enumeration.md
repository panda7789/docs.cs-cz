---
title: 'Postupy: Vytvoření nové metody pro výčet (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 3e153dbbe80ed850705ddaea4a9a3d5aba570fe0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508944"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Postupy: Vytvoření nové metody pro výčet (Průvodce programováním v C#)
Rozšiřující metody slouží k přidání funkce specifické pro typ konkrétní výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Grades` výčet představuje možné písmeno tříd, které student může zobrazit ve třídě. Rozšiřující metody s názvem `Passing` se přidá do `Grades` tak, aby každá instance daného typu nyní "ví", zda představuje na podnikové úrovni předávání nebo ne.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Všimněte si, `Extensions` třída také obsahuje statickou proměnnou, která se dynamicky aktualizuje a že návratová hodnota metody rozšíření odpovídá aktuální hodnotě proměnné. Tento příklad ukazuje, že na pozadí jsou rozšiřující metody vyvolány přímo u statické třídy, ve kterém jsou definovány.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód spustit, zkopírujte a vložte ho do jazyka Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio. Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a `using` směrnice pro System.Linq. Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
