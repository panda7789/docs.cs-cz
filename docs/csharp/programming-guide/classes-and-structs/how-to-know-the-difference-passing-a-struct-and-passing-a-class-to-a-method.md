---
title: 'Postupy: Znát rozdíl mezi předáním struktury a předáním odkazu na třídu do průvodce C# programováním metod'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 09b40a1ee8ab57a4b8a641acae49ab31a14d3d5b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893141"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Postupy: Znát rozdíl mezi předáním struktury a předáním odkazu na třídu metodě (C# Průvodce programováním)
Následující příklad ukazuje, jak se předávání [struktury](../../language-reference/keywords/struct.md) do metody liší od předání instance [třídy](../../language-reference/keywords/class.md) metodě. V příkladu jsou oba argumenty (struktura a instance třídy) předány hodnotou a obě metody mění hodnotu jednoho pole argumentu. Nicméně výsledky těchto dvou metod nejsou stejné, protože to, co je předáno při předávání struktury, se liší od toho, co je předáno při předání instance třídy.  
  
 Vzhledem k tomu, že struktura je [typ hodnoty](../../language-reference/keywords/value-types.md), při [předání struktury hodnotou](./passing-value-type-parameters.md) metody, metoda přijímá a pracuje na kopii argumentu struktury. Metoda nemá přístup k původní struktuře v volající metodě, takže ji nemůže nijak změnit. Metoda může změnit pouze kopii.  
  
 Instance třídy je [odkazový typ](../../language-reference/keywords/reference-types.md), nikoli hodnotový typ. Pokud [je odkazový typ předán pomocí hodnoty](./passing-reference-type-parameters.md) metodě, metoda obdrží kopii odkazu na instanci třídy. To znamená, že volaná metoda obdrží kopii adresy instance a metoda volání zachová původní adresu instance. Instance třídy v metodě volání má adresu, parametr v volané metodě má kopii adresy a obě adresy odkazují na stejný objekt. Protože parametr obsahuje pouze kopii adresy, volaná metoda nemůže změnit adresu instance třídy v volání metody. Volaná metoda však může použít kopii adresy pro přístup ke členům třídy, které mají původní adresu i kopii odkazu na adresu. Pokud volaná metoda změní člen třídy, změní se také instance původní třídy v volající metodě.  
  
 Výstup následujícího příkladu ukazuje rozdíl. Hodnota `willIChange` pole instance třídy je změněna voláním metody `ClassTaker` , protože metoda používá adresu v parametru k nalezení zadaného pole instance třídy. Pole struktury v volající metodě není změněno voláním metody `StructTaker` , protože hodnota argumentu je kopie samotné struktury, nikoli kopie její adresy. `willIChange` `StructTaker`změní kopii a kopie je ztracena po dokončení volání `StructTaker` .  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy](./classes.md)
- [Struktury](./structs.md)
- [Předávání parametrů](./passing-parameters.md)
