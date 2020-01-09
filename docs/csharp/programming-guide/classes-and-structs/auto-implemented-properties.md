---
title: Automaticky implementované vlastnosti – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 76f16a66fbc01a6a69d91136cfbfe5805b91aea3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705636"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Automaticky implementované vlastnosti (Průvodce programováním v C#)
V C# 3,0 a novějších se automaticky implementované vlastnosti přizpůsobují deklarace vlastnost, pokud se v přístupových parametrech vlastnosti nepožaduje žádná další logika. Také umožňují, aby kód klienta vytvářel objekty. Pokud deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří soukromé, anonymní zálohovací pole, které je přístupné pouze prostřednictvím `get` vlastností a přístupových objektů `set`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchou třídu, která má některé automaticky implementované vlastnosti:  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 V C# 6 a novějších verzích můžete inicializovat automaticky implementované vlastnosti podobně jako pole:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Třída, která je zobrazena v předchozím příkladu, je proměnlivá. Kód klienta může změnit hodnoty v objektech poté, co byly vytvořeny. V komplexních třídách, které obsahují významné chování (metody) a také data, je často nutné mít veřejné vlastnosti. Pro malé třídy nebo struktury, které pouze zapouzdřují sadu hodnot (data) a mají malé nebo žádné chování, byste však měli objekty nastavit jako neměnné deklarováním přístupového objektu set jako [soukromého](../../language-reference/keywords/private.md) (neproměnlivé pro příjemce) nebo deklarováním pouze přístupového objektu Get (neproměnlivé všude kromě konstruktoru).  Další informace naleznete v tématu [jak implementovat odlehčenou třídu s automaticky implementovanými vlastnostmi](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
  
## <a name="see-also"></a>Viz také:

- [Vlastnosti](./properties.md)
- [Modifikátory](/dotnet/csharp/language-reference/keywords)
