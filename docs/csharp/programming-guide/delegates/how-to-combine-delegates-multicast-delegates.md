---
title: Postup kombinování delegátů (Delegáti vícesměrového vysílání) – Průvodce programováním v C#
description: Naučte se kombinovat delegáty a vytvořit delegáty vícesměrového vysílání. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d23ea758c9da2c3399f5d98e81360cc250b428a1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302734"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Jak kombinovat delegáty (vícesměrové delegáty) (Průvodce programováním v C#)
Tento příklad ukazuje, jak vytvořit delegáty vícesměrového vysílání. Užitečnou vlastností objektů [delegáta](../../language-reference/builtin-types/reference-types.md) je, že více objektů lze přiřadit k jedné instanci delegáta pomocí `+` operátoru. Delegát vícesměrového vysílání obsahuje seznam přiřazených delegátů. Při volání delegáta vícesměrového vysílání vyvolá delegáty v seznamu v pořadí. Kombinovat lze pouze delegáty stejného typu.  
  
 `-`Operátor lze použít k odebrání delegáta komponenty z delegáta vícesměrového vysílání.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.MulticastDelegate>
- [Průvodce programováním v C#](../index.md)
- [Události](../events/index.md)
