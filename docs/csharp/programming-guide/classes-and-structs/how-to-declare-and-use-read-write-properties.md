---
title: Jak deklarovat a používat vlastnosti zápisu pro čtení - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 4b9db5f15746ab9a1f42239150c6783154723371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170283"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Jak deklarovat a používat vlastnosti zápisu pro čtení (Průvodce programováním jazyka C#)
Vlastnosti poskytují pohodlí veřejných datových členů bez rizik, která přicházejí s nechráněným, nekontrolovaným a neověřeným přístupem k datům objektu. Toho lze dosáhnout prostřednictvím *přístupových objektů*: speciální metody, které přiřazují a načítají hodnoty z podkladového datového člena. Přistupující [přístupový odkaz set](../../language-reference/keywords/set.md) umožňuje přiřazení datových členů a [get](../../language-reference/keywords/get.md) accessor načte hodnoty datových členů.  
  
 Tato ukázka `Person` ukazuje třídu, `Name` která má `Age` dvě vlastnosti: (řetězec) a (int). Obě vlastnosti poskytují `get` a `set` přistupující objekty, takže jsou považovány za vlastnosti čtení a zápisu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Robustní programování  
 V předchozím příkladu `Name` `Age` a vlastnosti jsou `get` [veřejné](../../language-reference/keywords/public.md) a zahrnují jak a a přistupující objekt. `set` To umožňuje libovolný objekt číst a zapisovat tyto vlastnosti. Někdy je však žádoucí vyloučit jeden z přistupujících. Vynechání matného objektu `set` například způsobí, že vlastnost je jen pro čtení:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternativně můžete vystavit jeden přístupový odkaz veřejně, ale jiné soukromé nebo chráněné. Další informace naleznete [v tématu Asymetrické přístupové připojení přístupkovou informací](./restricting-accessor-accessibility.md).  
  
 Jakmile jsou vlastnosti deklarovány, mohou být použity, jako by byly pole třídy. To umožňuje velmi přirozenou syntaxi při získávání a nastavování hodnoty vlastnosti, jako v následujících příkazech:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Všimněte si, `set` že `value` v metodě vlastnosti je k dispozici speciální proměnná. Tato proměnná obsahuje hodnotu, kterou uživatel zadal, například:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Všimněte si čisté syntaxe `Age` pro zvýšení `Person` vlastnosti na objekt:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Pokud `set` samostatné `get` a metody byly použity k modelování vlastností, ekvivalentní kód může vypadat takto:  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 Metoda `ToString` je přepsána v tomto příkladu:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Všimněte `ToString` si, že není explicitně použit v programu. Je vyvolána ve výchozím `WriteLine` nastavení volání.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Vlastnosti](./properties.md)
- [Třídy a struky](./index.md)
