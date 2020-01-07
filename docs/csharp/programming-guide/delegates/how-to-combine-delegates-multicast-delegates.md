---
title: Postup kombinování delegátů (Delegáti vícesměrového vysílání) – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 1a552c0203a4307994b80a1d3d37d12f577c02c4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346388"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Postup kombinování delegátů (Delegáti vícesměrového vysílání) (C# Průvodce programováním)
Tento příklad ukazuje, jak vytvořit delegáty vícesměrového vysílání. Užitečnou vlastností objektů [delegáta](../../language-reference/builtin-types/reference-types.md) je, že více objektů lze přiřadit k jedné instanci delegáta pomocí operátoru `+`. Delegát vícesměrového vysílání obsahuje seznam přiřazených delegátů. Při volání delegáta vícesměrového vysílání vyvolá delegáty v seznamu v pořadí. Kombinovat lze pouze delegáty stejného typu.  
  
 Operátor `-` lze použít k odebrání delegáta komponenty z delegáta vícesměrového vysílání.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.MulticastDelegate>
- [Průvodce programováním v jazyce C#](../index.md)
- [Události](../events/index.md)
