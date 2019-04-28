---
title: Obecní delegáti - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 2806eadd2d3f8a4c3e8f001b02b28d35a60daaec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679658"
---
# <a name="generic-delegates-c-programming-guide"></a>Obecní delegáti (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) můžete definovat vlastní parametry typu. Kód, že odkazy obecného delegátu možné zadat argument typu k vytvoření uzavřený konstruovaný typ., stejně jako při vytvoření instance generické třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C# verze 2.0 obsahuje novou funkci s názvem metody skupiny převod, který se vztahuje na typy konkrétní, jakož i obecných delegátů a umožňuje zapisovat na předchozí řádek s této zjednodušenou syntaxi:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Delegáti definované v rámci obecné třídy můžete použít parametry typu obecné třídy v stejným způsobem jako metody třídy.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Argument typu obsahující třídy, musíte zadat kód, který odkazuje na delegáta následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Obecní delegáti jsou zvláště užitečné při definování události založen na typické návrhový vzor, protože argument odesílatele, mohou být silného typu a už musí být převeden do a z <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [Obecné metody](../../../csharp/programming-guide/generics/generic-methods.md)
- [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)
- [Obecná rozhraní](../../../csharp/programming-guide/generics/generic-interfaces.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
- [Obecné typy](~/docs/standard/generics/index.md)
