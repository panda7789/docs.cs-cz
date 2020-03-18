---
title: Jak vytvořit novou metodu pro výčet - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705649"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Jak vytvořit novou metodu pro výčet (C# Programovací průvodce)
Metody rozšíření můžete použít k přidání funkce specifické pro konkrétní typ výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Grades` představuje výčet možné známky písmen, které může student obdržet ve třídě. Metoda rozšíření `Passing` s názvem `Grades` je přidána do typu tak, aby každá instance tohoto typu nyní "ví", zda představuje absolvování stupně nebo ne.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Všimněte `Extensions` si, že třída také obsahuje statickou proměnnou, která je dynamicky aktualizována a že vrácená hodnota metody rozšíření odráží aktuální hodnotu této proměnné. To ukazuje, že na pozadí rozšíření metody jsou vyvolány přímo na statickou třídu, ve které jsou definovány.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Metody rozšíření](./extension-methods.md)
