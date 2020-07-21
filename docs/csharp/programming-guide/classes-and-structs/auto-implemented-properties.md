---
title: Automaticky implementované vlastnosti – Průvodce programováním v C#
description: Pro automaticky implementované vlastnosti v jazyce C# vytvoří complier soukromé, anonymní zálohovací pole přístupné pouze prostřednictvím přístupových objektů Get a set vlastnosti.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: f58f9a23f26bde7e80d834528d94e38af1231e7b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474472"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Automaticky implementované vlastnosti (Průvodce programováním v C#)

V C# 3,0 a novějších, automaticky implementované vlastnosti umožňují deklarace vlastností výstižnější, pokud v přístupových parametrech vlastností není žádná další logika. Také umožňují, aby kód klienta vytvářel objekty. Pokud deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří soukromé, anonymní zálohovací pole, které je přístupné pouze prostřednictvím vlastností `get` a `set` přístupových objektů.
  
## <a name="example"></a>Příklad

Následující příklad ukazuje jednoduchou třídu, která má některé automaticky implementované vlastnosti:  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

V rozhraních nemůžete deklarovat automaticky implementované vlastnosti. Automaticky implementované vlastnosti deklarující pole pro zálohování privátní instance a rozhraní nedeklarují pole instance. Deklarace vlastnosti v rozhraní bez definování těla deklaruje vlastnost s přístupovými objekty, které musí být implementovány pomocí každého typu, který toto rozhraní implementuje.

V C# 6 a novějších můžete inicializovat automaticky implementované vlastnosti podobně jako pole:  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

Třída, která je zobrazena v předchozím příkladu, je proměnlivá. Kód klienta může po vytvoření změnit hodnoty v objektech. V komplexních třídách, které obsahují významné chování (metody) a také data, je často nutné mít veřejné vlastnosti. Pro malé třídy nebo struktury, které pouze zapouzdřují sadu hodnot (data) a mají malé nebo žádné chování, byste však měli objekty nastavit jako neměnné deklarováním přístupového objektu set jako [soukromého](../../language-reference/keywords/private.md) (neproměnlivé pro příjemce) nebo deklarováním pouze přístupového objektu Get (neproměnlivé všude kromě konstruktoru).  Další informace naleznete v tématu [jak implementovat odlehčenou třídu s automaticky implementovanými vlastnostmi](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).

## <a name="see-also"></a>Viz také

- [Vlastnosti](./properties.md)
- [Modifikátory](/dotnet/csharp/language-reference/keywords)
