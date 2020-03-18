---
title: Jak poznat rozdíl mezi předáním struktury a předáním odkazu na třídu metody - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: a280a6df873d7c03c204bc5c86468e7e7298d723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673430"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Jak poznat rozdíl mezi předáním struktury a předáním odkazu na třídu na metodu (C# Programming Guide)
Následující příklad ukazuje, jak předávání [struktury](../../language-reference/builtin-types/struct.md) metodě se liší od předání instance [třídy](../../language-reference/keywords/class.md) metodě. V příkladu jsou oba argumenty (instance struktury a třídy) předány hodnotou a obě metody změní hodnotu jednoho pole argumentu. Výsledky těchto dvou metod však nejsou stejné, protože to, co je předáno při předání struktury se liší od toho, co je předáno při předání instance třídy.  
  
 Vzhledem k tomu, že struktura je [typ hodnoty](../../language-reference/builtin-types/value-types.md), při [předání struktury podle hodnoty](./passing-value-type-parameters.md) metodě metoda přijímá a pracuje s kopií argumentu struktury. Metoda nemá přístup k původní struktury v volající metody a proto nelze změnit žádným způsobem. Metoda může změnit pouze kopii.  
  
 Instance třídy je [typ odkazu](../../language-reference/keywords/reference-types.md), nikoli typ hodnoty. Když [je typ odkazu předán hodnotou](./passing-reference-type-parameters.md) metodě, metoda obdrží kopii odkazu na instanci třídy. To znamená, že volaná metoda obdrží kopii adresy instance a volající metoda zachová původní adresu instance. Instance třídy v volající metodě má adresu, parametr v volané metodě má kopii adresy a obě adresy odkazují na stejný objekt. Vzhledem k tomu, že parametr obsahuje pouze kopii adresy, volaná metoda nemůže změnit adresu instance třídy v metodě volání. Volaná metoda však může použít kopii adresy pro přístup k členům třídy, které mají původní adresu i kopii odkazu na adresu. Pokud volaná metoda změní člena třídy, změní se také původní instance třídy v metodě volání.  
  
 Výstup následujícípříklad ilustruje rozdíl. Hodnota `willIChange` pole instance třídy se změní metodou call `ClassTaker` to, protože metoda používá adresu v parametru k vyhledání zadaného pole instance třídy. Pole `willIChange` struktury v volající metodě se nezmění voláním `StructTaker` metody, protože hodnota argumentu je kopií samotné struktury, nikoli kopií jeho adresy. `StructTaker`změní kopii a kopie se po `StructTaker` dokončení volání ztratí.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy](./classes.md)
- [Typy struktur](../../language-reference/builtin-types/struct.md)
- [Předávání parametrů](./passing-parameters.md)
