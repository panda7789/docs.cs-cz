---
title: "Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na třídu metodě (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b989c3cefe72c6c17d10dd91005dcecbfc84e389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na třídu metodě (Průvodce programováním v C#)
Následující příklad ukazuje, jak předávání [struktura](../../../csharp/language-reference/keywords/struct.md) do metody se liší od předávání [třída](../../../csharp/language-reference/keywords/class.md) instance na metodu. V příkladu oba argumenty (struktura a třída instance) jsou předaná hodnota a obě metody změna hodnoty argumentu jedno pole. Ale výsledky ze dvou metod nejsou stejné vzhledem k tomu, co se předá, když je předat struktury se liší od co je předán při předání instance třídy.  
  
 Vzhledem k tomu, že je struktury [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md), když jste [předat struktury podle hodnoty](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) na metodu, metoda obdrží a funguje na kopii struktura argument. Metoda nemá přístup k původní struktura v metodě volání a proto nemůžete provést změnu žádným způsobem. Metodu lze změnit pouze kopie.  
  
 Je instance třídy [odkazují na typ](../../../csharp/language-reference/keywords/reference-types.md), typ hodnoty. Když [typu odkazu je předaná hodnota](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) na metodu metodu obdrží kopii odkaz na instanci třídy. To znamená metoda obdrží kopii adresu instance nelze zkopírovat instance sám sebe. Instance třídy u volání metody s adresou, parametr volané metody má kopii adresu a obě adresy odkazovat na stejný objekt. Vzhledem k tomu, že parametr obsahuje pouze kopie adresu, zavolat metodu nelze změnit na adresu instance třídy u volání metody. Vyvolání metody však můžete použít adresu přístup ke členům třídy, které odkazují na původní adrese a o kopírování. Pokud se zavolat metoda změní člena třídy, původní instance třídy v metodě volání se také změní.  
  
 Výstup následující příklad ukazuje rozdíl. Hodnota `willIChange` pole instance třídy se změní při volání metody `ClassTaker` vzhledem k tomu, že metoda používá adresu v parametru k nalezení zadané pole instance třídy. `willIChange` Pole struktura v metodě volání není při volání metody změnit `StructTaker` vzhledem k tomu, že je hodnota argumentu kopie struktura samostatně, není kopie jeho adresy. `StructTaker`změny kopie a o kopírování dojde ke ztrátě při zpracování volání `StructTaker` byla dokončena.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Předávání parametrů](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
