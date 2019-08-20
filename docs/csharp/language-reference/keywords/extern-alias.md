---
title: externí odkaz na C# alias
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 749386f08cb6ab6ab79896aca3c1eb1e98ca5472
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602176"
---
# <a name="extern-alias-c-reference"></a>externí alias (Referenční dokumentace jazyka C#)
Možná budete muset odkazovat na dvě verze sestavení, které mají stejné názvy plně kvalifikovaného typu. Například může být nutné použít dvě nebo více verzí sestavení ve stejné aplikaci. Pomocí externího aliasu sestavení lze obory názvů z každého sestavení zabalit do oborů názvů kořenové úrovně s názvem alias, což umožňuje jejich použití ve stejném souboru.  
  
> [!NOTE]
>  Klíčové slovo [extern](./extern.md) se používá také jako modifikátor metody a deklaruje metodu napsanou v nespravovaném kódu.  
  
 Chcete-li odkazovat na dvě sestavení se stejnými názvy plně kvalifikovaného typu, je nutné zadat alias na příkazovém řádku následujícím způsobem:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Tím se vytvoří externí `GridV1` aliasy `GridV2`a. Chcete-li tyto aliasy použít v rámci programu, odkažte je `extern` pomocí klíčového slova. Příklad:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Každá deklarace extern alias zavádí další obor názvů na úrovni root, který je souběžně (ale neleží v rámci) globálního oboru názvů. Typy z každého sestavení lze tedy odkazovat bez nejednoznačnosti pomocí jejich plně kvalifikovaného názvu, který je rootem v příslušném oboru názvů alias.  
  
 V předchozím příkladu `GridV1::Grid` by byl ovládací prvek mřížky z `grid.dll`a `GridV2::Grid` by byl ovládací prvek mřížky z `grid20.dll`.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [:: – operátor](../operators/namespace-alias-qualifier.md)
- [/Reference (C# možnosti kompilátoru)](../compiler-options/reference-compiler-option.md)
