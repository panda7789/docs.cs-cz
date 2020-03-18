---
title: Automaticky implementované vlastnosti – průvodce programováním jazyka C#
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 791455c1eaef752da2b551e20187d390ca6c65e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170322"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Automaticky implementované vlastnosti (Průvodce programováním v C#)

V C# 3.0 a novější, automaticky implementované vlastnosti, aby deklarace vlastnosti stručnější, když není vyžadována žádná další logika v přístupové objekty vlastnosti. Umožňují také klientský kód k vytváření objektů. Když deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří `get` soukromé `set` anonymní doprovodné pole, ke kterému lze přistupovat pouze prostřednictvím přístupových objektů vlastnosti a přístupových objektů.
  
## <a name="example"></a>Příklad

Následující příklad ukazuje jednoduchou třídu, která má některé automaticky implementované vlastnosti:  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

V rozhraních nelze deklarovat automaticky implementované vlastnosti. Automaticky implementované vlastnosti deklarují pole pro zálohování privátní instance a rozhraní nesmí deklarovat pole instancí. Deklarování vlastnost v rozhraní bez definování těla deklaruje vlastnost s přístupové objekty, které musí být implementovány každý typ, který implementuje toto rozhraní.

V C# 6 a novějších můžete inicializovat automaticky implementované vlastnosti podobně jako pole:  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

Třída, která je zobrazena v předchozím příkladu je proměnlivá. Kód klienta můžete změnit hodnoty v objektech po vytvoření. Ve složitých třídách, které obsahují významné chování (metody) i data, je často nutné mít veřejné vlastnosti. Však pro malé třídy nebo struktury, které právě zapouzdřují sadu hodnot (data) a mají malé nebo žádné chování, měli byste buď objekty neměnné deklarováním set přistupujícího objektu jako [soukromé](../../language-reference/keywords/private.md) (neměnné pro spotřebitele) nebo deklarováním pouze get přistupujícího objektu (neměnné všude kromě konstruktoru).  Další informace naleznete v [tématu Jak implementovat zjednodušenou třídu s automaticky implementovanými vlastnostmi](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).

## <a name="see-also"></a>Viz také

- [Vlastnosti](./properties.md)
- [Modifikátory](/dotnet/csharp/language-reference/keywords)
