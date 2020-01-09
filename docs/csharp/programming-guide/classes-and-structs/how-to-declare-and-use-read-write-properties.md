---
title: Jak deklarovat a používat vlastnosti pro čtení a zápis C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 5b880cfc3ace197a3bad2f707cf55543dbe7b78e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714921"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Postup deklarace a použití vlastností čtení a zápisu (C# Průvodce programováním)
Vlastnosti poskytují pohodlí pro veřejné datové členy, aniž by došlo k rizikům, která jsou součástí nechráněného, nekontrolovaného a neověřeného přístupu k datům objektu. To se provádí prostřednictvím *přístupových objektů*: speciální metody, které přiřazují a načítají hodnoty z podkladového datového člena. Přistupující objekt [set](../../language-reference/keywords/set.md) umožňuje přiřadit datové členy a přistupující objekt [Get](../../language-reference/keywords/get.md) načte hodnoty datových členů.  
  
 Tato ukázka ukazuje třídu `Person`, která má dvě vlastnosti: `Name` (String) a `Age` (int). Obě vlastnosti poskytují přístupové objekty `get` a `set`, takže se považují za vlastnosti pro čtení a zápis.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Robustní programování  
 V předchozím příkladu jsou vlastnosti `Name` a `Age` [veřejné](../../language-reference/keywords/public.md) a zahrnují `get` i přistupující objekt `set`. To umožňuje všem objektům číst a zapisovat tyto vlastnosti. Někdy je však žádoucí, aby jeden z přístupových objektů vyloučil. Vynechání přístupového objektu `set` například nastaví vlastnost jen pro čtení:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternativně můžete zveřejnit jeden přistupující objekt veřejně, ale nastavit ho jako privátní nebo chráněný. Další informace najdete v tématu [přístupnost asymetrického přístupového objektu](./restricting-accessor-accessibility.md).  
  
 Jakmile jsou vlastnosti deklarovány, mohou být použity, jako kdyby byly polem třídy. To umožňuje velmi přirozenou syntaxi při získávání a nastavování hodnoty vlastnosti, jako v následujících příkazech:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Všimněte si, že ve vlastnosti `set` metoda je k dispozici speciální `value` proměnná. Tato proměnná obsahuje hodnotu zadanou uživatelem, například:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Všimněte si čisté syntaxe pro zvýšení `Age` vlastnosti u objektu `Person`:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Pokud byly pro vlastnosti modelu použity samostatné metody `set` a `get`, podobný kód by mohl vypadat takto:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 Metoda `ToString` je v tomto příkladu přepsána:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Všimněte si, že `ToString` není explicitně použit v programu. Je vyvolána ve výchozím nastavení voláním `WriteLine`.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Vlastnosti](./properties.md)
- [Třídy a struktury](./index.md)
