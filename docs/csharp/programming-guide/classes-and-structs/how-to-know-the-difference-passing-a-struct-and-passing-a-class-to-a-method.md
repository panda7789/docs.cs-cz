---
title: Jak zjistit rozdíl mezi předáním struktury a předáním odkazu na třídu metodě – Průvodce programováním v C#
description: Předání struktury do metody se liší od předání instance třídy metodě v jazyce C#. V tomto příkladu se zobrazuje struktura a instance třídy předané hodnotou.
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: ee4e6adf5c01cea786219407c1c0ffdb73f21b2a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865018"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Jak zjistit rozdíl mezi předáním struktury a předáním odkazu na třídu metodě (Průvodce programováním v C#)
Následující příklad ukazuje, jak se předávání [struktury](../../language-reference/builtin-types/struct.md) do metody liší od předání instance [třídy](../../language-reference/keywords/class.md) metodě. V příkladu jsou oba argumenty (struktura a instance třídy) předány hodnotou a obě metody mění hodnotu jednoho pole argumentu. Nicméně výsledky těchto dvou metod nejsou stejné, protože to, co je předáno při předávání struktury, se liší od toho, co je předáno při předání instance třídy.  
  
 Vzhledem k tomu, že struktura je [typ hodnoty](../../language-reference/builtin-types/value-types.md), při [předání struktury hodnotou](./passing-value-type-parameters.md) metody, metoda přijímá a pracuje na kopii argumentu struktury. Metoda nemá přístup k původní struktuře v volající metodě, takže ji nemůže nijak změnit. Metoda může změnit pouze kopii.  
  
 Instance třídy je [odkazový typ](../../language-reference/keywords/reference-types.md), nikoli hodnotový typ. Pokud [je odkazový typ předán pomocí hodnoty](./passing-reference-type-parameters.md) metodě, metoda obdrží kopii odkazu na instanci třídy. To znamená, že volaná metoda obdrží kopii adresy instance a metoda volání zachová původní adresu instance. Instance třídy v metodě volání má adresu, parametr v volané metodě má kopii adresy a obě adresy odkazují na stejný objekt. Protože parametr obsahuje pouze kopii adresy, volaná metoda nemůže změnit adresu instance třídy v volání metody. Volaná metoda však může použít kopii adresy pro přístup ke členům třídy, které mají původní adresu i kopii odkazu na adresu. Pokud volaná metoda změní člen třídy, změní se také instance původní třídy v volající metodě.  
  
 Výstup následujícího příkladu ukazuje rozdíl. Hodnota `willIChange` pole instance třídy je změněna voláním metody, `ClassTaker` protože metoda používá adresu v parametru k nalezení zadaného pole instance třídy. `willIChange`Pole struktury v volající metodě není změněno voláním metody `StructTaker` , protože hodnota argumentu je kopie samotné struktury, nikoli kopie její adresy. `StructTaker`změní kopii a kopie je ztracena po `StructTaker` dokončení volání.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy](./classes.md)
- [Typy struktur](../../language-reference/builtin-types/struct.md)
- [Předávání parametrů](./passing-parameters.md)
