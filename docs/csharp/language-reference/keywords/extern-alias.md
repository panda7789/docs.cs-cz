---
title: extern alias - C# Reference
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713551"
---
# <a name="extern-alias-c-reference"></a>externí alias (Referenční dokumentace jazyka C#)
Je možné, že budete muset odkazovat na dvě verze sestavení, které mají stejné plně kvalifikované názvy typů. Například může být možné použít dvě nebo více verzí sestavení ve stejné aplikaci. Pomocí aliasu externího sestavení mohou být obory názvů z každého sestavení zabaleny do oborů názvů kořenové úrovně pojmenovaných aliasem, což umožňuje jejich použití ve stejném souboru.  
  
> [!NOTE]
> Klíčové slovo [extern](./extern.md) se také používá jako modifikátor metody, deklarující metodu napsanou v nespravovaném kódu.  
  
 Chcete-li odkazovat na dvě sestavení se stejnými plně kvalifikovanými názvy typů, musí být na příkazovém řádku zadán alias takto:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Tím se vytvoří `GridV1` externí `GridV2`aliasy a . Chcete-li použít tyto aliasy z programu, `extern` odkazovat na ně pomocí klíčového slova. Například:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Každá deklarace aliasu extern zavádí další obor názvů na kořenové úrovni, který paraleluje (ale neleží uvnitř) globálního oboru názvů. Typy z každého sestavení tedy mohou být odkazovány bez nejednoznačnosti pomocí jejich plně kvalifikovaný název, zakořeněné v příslušném alias oboru názvů.  
  
 V předchozím `GridV1::Grid` příkladu by bylo `grid.dll`řízení `GridV2::Grid` mřížky z , `grid20.dll`a bude řídicí mřížky z .  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [:: Operátor](../operators/namespace-alias-qualifier.md)
- [-reference (Možnosti kompilátoru Jazyka C#)](../compiler-options/reference-compiler-option.md)
