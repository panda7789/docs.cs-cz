---
title: Obecní delegáti C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 46ceca257777455824b6900f3e49999536d6bcad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589737"
---
# <a name="generic-delegates-c-programming-guide"></a>Obecní delegáti (Průvodce programováním v C#)
[Delegát](../../language-reference/keywords/delegate.md) může definovat své vlastní parametry typu. Kód, který odkazuje na obecného delegáta, může zadat argument typu pro vytvoření uzavřeného konstruovaného typu, stejně jako při vytváření instancí obecné třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C#verze 2,0 obsahuje novou funkci nazvanou převod skupiny metod, která se vztahuje na konkrétní a také na obecné typy delegátů, a umožňuje napsat předchozí řádek pomocí této zjednodušené syntaxe:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Delegáti, kteří jsou definováni v rámci obecné třídy, mohou použít parametry typu obecné třídy stejným způsobem jako metody třídy.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Kód, který odkazuje na delegáta musí specifikovat typ argumentu obsahující třídy, jak je znázorněno níže:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Obecné Delegáti jsou zvláště užitečné při definování událostí na základě typického vzoru návrhu, protože argument odesílatele může být silného typu a již není nutné jej přetypování <xref:System.Object>na a z.  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné metody](./generic-methods.md)
- [Obecné třídy](./generic-classes.md)
- [Obecná rozhraní](./generic-interfaces.md)
- [Delegáti](../delegates/index.md)
- [Obecné typy](~/docs/standard/generics/index.md)
