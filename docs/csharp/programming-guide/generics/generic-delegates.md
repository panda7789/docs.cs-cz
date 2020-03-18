---
title: Obecné delegáty – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 4e57256328fc81a485670b47fcf8fd1c38e26fac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712218"
---
# <a name="generic-delegates-c-programming-guide"></a>Obecní delegáti (Průvodce programováním v C#)
[Delegát](../../language-reference/builtin-types/reference-types.md) může definovat vlastní parametry typu. Kód, který odkazuje na obecný delegát můžete zadat argument typu k vytvoření uzavřeného konstruovaného typu, stejně jako při vytváření instancí obecné třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C# verze 2.0 má novou funkci nazvanou převod skupiny metod, která se vztahuje na konkrétní i obecné typy delegátů a umožňuje napsat předchozí řádek s touto zjednodušenou syntaxí:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Delegáti definovaní v rámci obecné třídy můžete použít parametry typu obecné třídy stejným způsobem jako metody třídy.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Kód, který odkazuje delegát musí určit typ argument obsahující třídy, takto:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Obecné delegáty jsou užitečné zejména při definování událostí na základě typického návrhového vzoru, protože argument odesílatele <xref:System.Object>může být silně zadán a již nemusí být přetypován do a z .  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Programovací příručka jazyka C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné metody](./generic-methods.md)
- [Obecné třídy](./generic-classes.md)
- [Obecná rozhraní](./generic-interfaces.md)
- [Delegáty](../delegates/index.md)
- [Obecné typy](../../../standard/generics/index.md)
