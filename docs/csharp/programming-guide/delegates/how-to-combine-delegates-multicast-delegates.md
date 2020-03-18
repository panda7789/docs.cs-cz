---
title: Jak kombinovat delegáty (vícesměrové delegáty) – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705376"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Jak kombinovat delegáty (vícesměrové delegáty) (Průvodce programováním v C#)
Tento příklad ukazuje, jak vytvořit delegáty vícesměrového vysílání. Užitečnou vlastností [objektů delegáta](../../language-reference/builtin-types/reference-types.md) je, že pomocí operátoru `+` lze přiřadit více objektů jedné instanci delegáta. Delegát vícesměrového vysílání obsahuje seznam přiřazených delegátů. Při volání delegáta vícesměrového vysílání vyvolá delegáty v seznamu v pořadí. Lze kombinovat pouze delegáty stejného typu.  
  
 Operátor `-` lze odebrat delegáta komponenty z delegáta vícesměrového vysílání.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.MulticastDelegate>
- [Programovací příručka jazyka C#](../index.md)
- [Akce](../events/index.md)
