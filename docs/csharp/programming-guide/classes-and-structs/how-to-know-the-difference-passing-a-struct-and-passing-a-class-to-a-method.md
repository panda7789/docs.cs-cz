---
title: 'Postupy: Zjištění rozdílu mezi předáním struktury a předáním třídu odkaz na metodu - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: c5963f45ee233f4413c4281a063c9c3d2a4c2a93
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245451"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na metodu třídu (C# Průvodce programováním v)
Následující příklad ukazuje, jak předávání [struktura](../../../csharp/language-reference/keywords/struct.md) metody se liší od předávání [třídy](../../../csharp/language-reference/keywords/class.md) instanci metody. V tomto příkladu obou argumentů (instance struktury a třídy) jsou předávány hodnotou a obě metody změňte hodnotu argumentu jedno pole. Ale výsledky ze dvou způsobů nejsou stejné vzhledem k tomu, co je předána, když je předat strukturu se liší od, co je předané při předání instance třídy.  
  
 Protože je struktura [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md), když jste [předat strukturu hodnotu](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) metody, metoda přijímá a funguje na kopii struktury argument. Metoda nemá přístup k původní struktury ve volání metody a proto ho nemůže změnit žádným způsobem. Metoda může změnit pouze kopie.  
  
 Instance třídy [odkazovat na typ](../../../csharp/language-reference/keywords/reference-types.md), typ hodnoty. Když [typem odkazu je předán podle hodnoty](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) metody, metoda obdrží kopii odkaz na instanci třídy. To znamená, že metoda obdrží kopii adresa instance, není kopie samotné instanci. Instance třídy ve volání metody s adresou, parametr v metodě volané má kopii adresu a obě adresy odkazují na stejný objekt. Vzhledem k tomu, že parametr obsahuje pouze kopie adresu, volané metody nelze změnit adresu instance třídy ve volání metody. Volané metody však můžete použít adresu přístup ke členům třídy, které odkazují na původní adrese a o kopírování. Pokud se volané metody změní člena třídy, změní se také původní instance třídy ve volání metody.  
  
 Následující příklad výstupu ukazuje rozdíl. Hodnota `willIChange` pole instance třídy, je změnit pomocí volání metody `ClassTaker` vzhledem k tomu metoda používá adresu v parametru najít zadané pole instance třídy. `willIChange` Pole struktury ve volání metody není změněno pomocí volání metody `StructTaker` vzhledem k tomu, že hodnota argumentu je kopii struktury samotné, ne kopie adresy. `StructTaker` změny kopie a o kopírování je ztracena při volání `StructTaker` je dokončena.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [Předávání parametrů](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
