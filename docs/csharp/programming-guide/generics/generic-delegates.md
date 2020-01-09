---
title: Obecní delegáti C# – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 4e57256328fc81a485670b47fcf8fd1c38e26fac
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712218"
---
# <a name="generic-delegates-c-programming-guide"></a>Obecní delegáti (Průvodce programováním v C#)
[Delegát](../../language-reference/builtin-types/reference-types.md) může definovat své vlastní parametry typu. Kód, který odkazuje na obecného delegáta, může zadat argument typu pro vytvoření uzavřeného konstruovaného typu, stejně jako při vytváření instancí obecné třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C#verze 2,0 obsahuje novou funkci nazvanou převod skupiny metod, která se vztahuje na konkrétní a také na obecné typy delegátů, a umožňuje napsat předchozí řádek pomocí této zjednodušené syntaxe:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Delegáti, kteří jsou definováni v rámci obecné třídy, mohou použít parametry typu obecné třídy stejným způsobem jako metody třídy.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Kód, který odkazuje na delegáta musí specifikovat typ argumentu obsahující třídy, jak je znázorněno níže:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Obecné Delegáti jsou zvláště užitečné při definování událostí na základě typického vzoru návrhu, protože argument odesílatele může být silného typu a již nesmí být přetypování na <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné metody](./generic-methods.md)
- [Obecné třídy](./generic-classes.md)
- [Obecná rozhraní](./generic-interfaces.md)
- [Delegáti](../delegates/index.md)
- [Obecné typy](../../../standard/generics/index.md)
