---
title: Doména usnadnění – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713838"
---
# <a name="accessibility-domain-c-reference"></a>Doména přístupnosti (Referenční dokumentace jazyka C#)
Doména usnadnění člena určuje, ve kterých oddílech programu lze na člena odkazovat. Pokud je člen vnořen do jiného typu, jeho doména usnadnění je určena [jak úrovní usnadnění](./accessibility-levels.md) člena, tak doménou usnadnění typu bezprostředně obsahujícího typ.  
  
 Doména usnadnění typu nejvyšší úrovně je alespoň text programu projektu, ve které je deklarován. To znamená, že doména obsahuje všechny zdrojové soubory tohoto projektu. Doména usnadnění vnořeného typu je alespoň text programu typu, ve kterém je deklarována. To znamená, že doména je tělo typu, který zahrnuje všechny vnořené typy. Doména usnadnění vnořeného typu nikdy nepřekročí doménu obsahujícího typu. Tyto koncepty jsou demonstrovány v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje typ nejvyšší `T1`úrovně a dvě `M1` vnořené třídy a `M2`. Třídy obsahují pole, která mají různé deklarované přístupnosti. V `Main` metodě komentář následuje každý příkaz k označení domény usnadnění každého člena. Všimněte si, že příkazy, které se pokoušejí odkazovat na nepřístupné členy, jsou zakomentovány. Pokud chcete zobrazit chyby kompilátoru způsobené odkazováním na nepřístupný člen, odeberte komentáře po jednom.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Úrovně přístupnosti](./accessibility-levels.md)
- [Omezení používání úrovní přístupu](./restrictions-on-using-accessibility-levels.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Veřejné](./public.md)
- [Soukromé](./private.md)
- [protected](./protected.md)
- [Vnitřní](./internal.md)
