---
title: externí alias - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: d2ecd566731c3d2d472034ecb6412432af24c847
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422054"
---
# <a name="extern-alias-c-reference"></a>externí alias (Referenční dokumentace jazyka C#)
Budete muset odkazovat na dvě verze sestavení, která mají stejné názvy plně kvalifikovaných typů. Například budete muset použít dvě nebo více verzí sestavení ve stejné aplikaci. Obory názvů v každé sestavení dá zabalit pomocí alias externího sestavení v úrovni kořenového adresáře obory názvů s názvem podle aliasu, odkud můžou použít ve stejném souboru.  
  
> [!NOTE]
>  [Extern](../../../csharp/language-reference/keywords/extern.md) – klíčové slovo se také používá jako metodu modifikátoru deklarace metody napsanou v nespravovaném kódu.  
  
 Odkazování na dvou sestavení se stejnými názvy plně kvalifikovaný typ, je nutné zadat alias příkazového řádku, následujícím způsobem:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Tím se vytvoří externí aliasy `GridV1` a `GridV2`. Pokud chcete použít tyto aliasy z v rámci programu, je odkazovat pomocí `extern` – klíčové slovo. Příklad:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Zavádí další úrovni pro kořenový obor názvů služby, která parallels (ale neleží v) každé externí deklarace aliasu globálního oboru názvů. Proto typy z každé sestavení lze odkazovat na bez nejednoznačnost pomocí jejich plně kvalifikovaný název v příslušné aliasu oboru názvů root.  
  
 V předchozím příkladu `GridV1::Grid` bude ovládací prvek mřížky z `grid.dll`, a `GridV2::Grid` bude ovládací prvek mřížky z `grid20.dll`.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [:: – operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [/ Reference (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
