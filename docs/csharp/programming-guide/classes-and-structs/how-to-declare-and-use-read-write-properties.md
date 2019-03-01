---
title: 'Postupy: Deklarování a použití vlastností čtení/zápisu - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: b4dc9364e64f7ebfd495671b852b98d8f56c80b5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969025"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Postupy: Deklarování a použití vlastností čtení/zápisu (C# Průvodce programováním v)
Vlastnosti poskytují pohodlí veřejné datové členy bez rizika, které jsou součástí nechráněné, nekontrolovaného a neověřený přístup k datům objektu. To lze provést prostřednictvím *přistupující objekty*: speciální metody, které přiřadíte a načítat hodnoty ze základní datový člen. [Nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt umožňuje datové členy mají být přiřazeny a [získat](../../../csharp/language-reference/keywords/get.md) přistupující objekt načte hodnoty datových členů.  
  
 Tento příklad ukazuje `Person` třídu, která má dvě vlastnosti: `Name` (řetězec) a `Age` (int). Obě vlastnosti poskytují `get` a `set` přístupových objektů, takže jsou považovány za čtení a zápisu vlastnosti.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Robustní programování  
 V předchozím příkladu `Name` a `Age` vlastnosti jsou [veřejné](../../../csharp/language-reference/keywords/public.md) a oba `get` a `set` přistupujícího objektu. To umožňuje libovolný objekt pro čtení a zápis těchto vlastností. Ale je v některých případech žádoucí, vyloučit jeden přístupové objekty. Vynechání `set` přístupový objekt, například je vlastnost jen pro čtení:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternativně můžete veřejně zpřístupnit jeden přistupující objekt, ale jiné soukromé nebo chráněné. Další informace najdete v tématu [asymetrického přístupnosti přístupového objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Jakmile vlastnosti jsou deklarovány, můžete jako by byly pole třídy používá. To umožňuje velmi přirozené syntaxe při získávání i nastavování hodnoty vlastnosti, jako v následující příkazy:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Všimněte si, že ve vlastnosti `set` metoda a speciální `value` proměnná je k dispozici. Tato proměnná obsahuje hodnotu, kterou uživatel specifikoval, například:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Všimněte si, že čisté syntaxe se zvyšuje `Age` vlastnosti `Person` objektu:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Pokud samostatný `set` a `get` metodách, které byly použity k modelování vlastnosti, ekvivalentní kód může vypadat takto:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Je přepsána metoda v tomto příkladu:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Všimněte si, že `ToString` není použito explicitně v programu. Vyvolá se ve výchozím nastavení `WriteLine` volání.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
