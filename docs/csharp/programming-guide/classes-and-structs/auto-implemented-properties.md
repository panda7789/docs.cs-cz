---
title: "Automaticky implementované vlastnosti (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1aa923c6d8208c2d5451957c4112493d0acd561d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Automaticky implementované vlastnosti (Průvodce programováním v C#)
V jazyce C# 3.0 nebo novější automaticky implementované vlastnosti deklarace vlastnosti přesnější při provést žádné další logiku navíc je nutné v přístupových objektech vlastnosti. Umožňují také kód klienta k vytváření objektů. Když je deklarovat vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří privátní, anonymní základní pole, které je přístupné pouze prostřednictvím vlastnosti `get` a `set` přistupující objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý třídy, která má některé automaticky implementované vlastnosti:  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 V jazyce C# 6 nebo novější bude možné inicializovat automaticky implementované vlastnosti podobně jako na pole:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Třída, která se zobrazí v předchozím příkladu je měnitelný. Kód klienta můžete změnit hodnoty v objektech po jejich vytvoření. V komplexní tříd, které obsahují důležité chování (metody) a také data je často potřeba mít veřejné vlastnosti. Ale pro malé třídy nebo struktury, které právě zapouzdření sadu hodnot (data) a nemají žádné nebo téměř žádné chování, buď měli objekty neměnné deklarováním přistupující objekt set jako [privátní](../../../csharp/language-reference/keywords/private.md) (neměnné k příjemce), nebo deklarování pouze přistupující (neměnné everywhere kromě konstruktoru).  Další informace najdete v tématu [postupy: implementace třídy Lightweight vlastnostmi Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
 Atributy jsou povoleny na automaticky implementované vlastnosti ale samozřejmě není na pole Základní od těch, které nejsou přístupné z vašeho zdrojového kódu. Pokud je třeba použít atribut na pole základní vlastnosti, stačí vytvořte regulární vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
