---
title: Postup vytvoření nové metody pro výčet – Průvodce programováním v C#
description: Naučte se používat rozšiřující metody pro přidání funkce do výčtu v jazyce C#. Tento příklad ukazuje metodu rozšíření s názvem předání pro výčet s názvem třídy.
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 6c01a73476e98e8344a7a8dc35a5fd80384fc7a2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864485"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Postup vytvoření nové metody pro výčet (Průvodce programováním v C#)
Metody rozšíření lze použít k přidání funkcí specifických pro konkrétní typ výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Grades` výčet představuje možné známky, které může student získat ve třídě. Rozšiřující metoda s názvem `Passing` je přidána do `Grades` typu tak, že každá instance daného typu teď "ví", zda představuje třídu předání nebo ne.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Všimněte si, že `Extensions` Třída také obsahuje statickou proměnnou, která je dynamicky aktualizována a že návratová hodnota metody rozšíření odráží aktuální hodnotu této proměnné. To ukazuje, že na pozadí jsou metody rozšíření vyvolány přímo na statickou třídu, ve které jsou definovány.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Metody rozšíření](./extension-methods.md)
