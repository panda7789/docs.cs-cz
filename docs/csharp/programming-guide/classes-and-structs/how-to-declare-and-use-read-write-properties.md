---
title: "Postupy: deklarování a použití vlastností čtení zápisu (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17bdd05196f834b491c69f648bec0b7cb6e3cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Postupy: deklarování a použití vlastností čtení zápisu (C# Průvodce programováním)
Vlastnosti zajistí pohodlí veřejná data členů bez rizika, které jsou součástí nechráněné, neřízené a neověřených přístup k datům objektu. To se provádí prostřednictvím *přístupové objekty*: speciální metody, které přiřadit a načítání hodnot z základní datový člen. [Nastavit](../../../csharp/language-reference/keywords/set.md) přistupujícího objektu umožňuje členům data přiřazen a [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu načte data hodnoty členů.  
  
 Tento příklad ukazuje `Person` třídu, která má dvě vlastnosti: `Name` (string) a `Age` (int). Obě vlastnosti poskytují `get` a `set` přístupových objektů, takže je považována za čtení/zápisu vlastnosti.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 V předchozím příkladu `Name` a `Age` vlastnosti jsou [veřejné](../../../csharp/language-reference/keywords/public.md) a současně obsahovat `get` a `set` přistupujícího objektu. To umožňuje číst a zapisovat tyto vlastnosti libovolného objektu. Ale je někdy žádoucí, jeden přístupové objekty vyloučit. Vynechání `set` přistupujícího objektu, například umožňuje vlastnost jen pro čtení:  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 Alternativně můžete vystavit jednoho přístupového objektu veřejně, ale zkontrolujte další privátní nebo chráněný. Další informace najdete v tématu [asymetrické přístupnosti přistupujícího objektu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Jakmile jsou deklarované vlastnosti, můžete jako kdyby byly pole třídy použít. To umožňuje velmi přirozené syntaxe při získání a nastavení hodnoty vlastnosti, jako v následující příkazy:  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 Všimněte si, že se ve vlastnosti `set` metoda a zvláštní `value` proměnná je k dispozici. Tato proměnná obsahuje hodnotu, která uživatel zadal, například:  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 Všimněte si čistou syntaxe zvyšování `Age` vlastnost `Person` objektu:  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 Pokud samostatné `set` a `get` metody použité k jejich vlastnosti modelu, kód ekvivalentní může vypadat například takto:  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Je metoda potlačena v tomto příkladu:  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 Všimněte si, že `ToString` nepoužívá explicitně v programu. Vyvolá se ve výchozím nastavení `WriteLine` volání.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
