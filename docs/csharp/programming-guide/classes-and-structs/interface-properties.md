---
title: Vlastnosti rozhraní – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: cdd425970442e284d6fd6488bbb13394c12e939a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596449"
---
# <a name="interface-properties-c-programming-guide"></a>Vlastnosti rozhraní (Průvodce programováním v C#)
Vlastnosti lze deklarovat v [rozhraní](../../language-reference/keywords/interface.md). Následuje příklad přistupujícího objektu vlastnosti rozhraní:  
  
 [!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]  
  
 Přistupující objekt vlastnosti rozhraní nemá tělo. Proto je účel přístupových objektů indikován, zda je vlastnost určena pro čtení i zápis, jen pro čtení nebo jen pro zápis.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu má rozhraní `IEmployee` `Name`vlastnost pro čtení i zápis, a vlastnost `Counter`určenou jen pro čtení. `Employee` Třída`IEmployee` implementuje rozhraní a používá tyto dvě vlastnosti. Program přečte název nového zaměstnance a aktuální počet zaměstnanců a zobrazí název zaměstnance a vypočtené číslo zaměstnance.  
  
 Můžete použít plně kvalifikovaný název vlastnosti, který odkazuje na rozhraní, ve kterém je člen deklarován. Příklad:  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 To se označuje jako [explicitní implementace rozhraní](../interfaces/explicit-interface-implementation.md). Například pokud třída `Employee` implementuje dvě rozhraní `ICitizen` a `IEmployee` a obě rozhraní mají `Name` vlastnost, bude nutná implementace explicitního člena rozhraní. To znamená, že následující deklarace vlastnosti:  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 `Name` implementuje vlastnost`IEmployee` na rozhraní a následující deklaraci:  
  
 [!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]  
  
 `Name` implementuje vlastnost`ICitizen` na rozhraní.  
  
 [!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Vzorový výstup  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Vlastnosti](./properties.md)
- [Použití vlastností](./using-properties.md)
- [Porovnání mezi vlastnostmi a indexery](../indexers/comparison-between-properties-and-indexers.md)
- [Indexery](../indexers/index.md)
- [Rozhraní](../interfaces/index.md)
