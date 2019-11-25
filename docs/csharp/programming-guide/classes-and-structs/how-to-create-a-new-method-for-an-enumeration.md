---
title: Postup vytvoření nové metody pro C# programový průvodce vytvářením výčtu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 02af55c851392ce5dde4c83fd32d18b927950a3f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971034"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Postup vytvoření nové metody pro výčet (C# Průvodce programováním)
Metody rozšíření lze použít k přidání funkcí specifických pro konkrétní typ výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu výčet `Grades` představuje možné známky, které může student získat ve třídě. Rozšiřující metoda s názvem `Passing` je přidána do typu `Grades` tak, že každá instance daného typu teď "ví", zda představuje třídu předání nebo ne.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Všimněte si, že třída `Extensions` obsahuje také statickou proměnnou, která je dynamicky aktualizována a že návratová hodnota metody rozšíření odráží aktuální hodnotu této proměnné. To ukazuje, že na pozadí jsou metody rozšíření vyvolány přímo na statickou třídu, ve které jsou definovány.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Rozšiřující metody](./extension-methods.md)
