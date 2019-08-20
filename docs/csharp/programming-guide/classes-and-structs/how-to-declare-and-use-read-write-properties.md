---
title: 'Postupy: Deklarace a použití vlastností čtení a zápisu C# – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 010c3d4c1ae976091b5382f00a982400746f6436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596925"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Postupy: Deklarace a použití vlastností čtení a zápisuC# (Průvodce programováním)
Vlastnosti poskytují pohodlí pro veřejné datové členy, aniž by došlo k rizikům, která jsou součástí nechráněného, nekontrolovaného a neověřeného přístupu k datům objektu. To se provádí prostřednictvím *přístupových objektů*: speciální metody, které přiřazují a načítají hodnoty z podkladového datového člena. Přistupující objekt [set](../../language-reference/keywords/set.md) umožňuje přiřadit datové členy a přistupující objekt [Get](../../language-reference/keywords/get.md) načte hodnoty datových členů.  
  
 Tato ukázka ukazuje `Person` třídu, která má dvě vlastnosti: `Name` (String) a `Age` (int). Obě vlastnosti poskytují `get` a `set` přistupující objekty, takže se považují za vlastnosti pro čtení i zápis.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Robustní programování  
 V předchozím `Name` příkladu jsou vlastnosti a `get` `Age` [veřejné](../../language-reference/keywords/public.md) a zahrnují i `set` přistupující objekt a. To umožňuje všem objektům číst a zapisovat tyto vlastnosti. Někdy je však žádoucí, aby jeden z přístupových objektů vyloučil. Vynechání `set` přístupového objektu například nastaví vlastnost jen pro čtení:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternativně můžete zveřejnit jeden přistupující objekt veřejně, ale nastavit ho jako privátní nebo chráněný. Další informace najdete v tématu [přístupnost asymetrického přístupového objektu](./restricting-accessor-accessibility.md).  
  
 Jakmile jsou vlastnosti deklarovány, mohou být použity, jako kdyby byly polem třídy. To umožňuje velmi přirozenou syntaxi při získávání a nastavování hodnoty vlastnosti, jako v následujících příkazech:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Všimněte si, že v `set` metodě vlastnosti je `value` k dispozici speciální proměnná. Tato proměnná obsahuje hodnotu zadanou uživatelem, například:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Všimněte si čisté syntaxe pro zvýšení hodnoty `Age` vlastnosti `Person` objektu:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Pokud se `set` pro `get` vlastnosti modelu použily samostatné metody a, může podobný kód vypadat takto:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Metoda je přepsána v tomto příkladu:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Všimněte si `ToString` , že se v programu explicitně nepoužívá. Je vyvolána ve výchozím nastavení `WriteLine` voláními.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Vlastnosti](./properties.md)
- [Třídy a struktury](./index.md)
