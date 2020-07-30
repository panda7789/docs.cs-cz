---
title: extern alias – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 891e56b064f8a327abe28293223a85b9d95e8fd3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301811"
---
# <a name="extern-alias-c-reference"></a>externí alias (Referenční dokumentace jazyka C#)
Možná budete muset odkazovat na dvě verze sestavení, které mají stejné názvy plně kvalifikovaného typu. Například může být nutné použít dvě nebo více verzí sestavení ve stejné aplikaci. Pomocí externího aliasu sestavení lze obory názvů z každého sestavení zabalit do oborů názvů kořenové úrovně s názvem alias, což umožňuje jejich použití ve stejném souboru.  
  
> [!NOTE]
> Klíčové slovo [extern](./extern.md) se používá také jako modifikátor metody a deklaruje metodu napsanou v nespravovaném kódu.  
  
 Chcete-li odkazovat na dvě sestavení se stejnými názvy plně kvalifikovaného typu, je nutné zadat alias na příkazovém řádku následujícím způsobem:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Tím se vytvoří externí aliasy `GridV1` a `GridV2` . Chcete-li tyto aliasy použít v rámci programu, odkažte je pomocí `extern` klíčového slova. Příklad:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Každá deklarace extern alias zavádí další obor názvů na úrovni root, který je souběžně (ale neleží v rámci) globálního oboru názvů. Typy z každého sestavení lze tedy odkazovat bez nejednoznačnosti pomocí jejich plně kvalifikovaného názvu, který je rootem v příslušném oboru názvů alias.  
  
 V předchozím příkladu by byl `GridV1::Grid` ovládací prvek mřížky z `grid.dll` a `GridV2::Grid` by byl ovládací prvek mřížky z `grid20.dll` .  
  
## <a name="using-visual-studio"></a>Pomocí sady Visual Studio

Pokud používáte aplikaci Visual Studio, mohou být aliasy poskytovány podobným způsobem.

Přidejte odkaz na *grid.dll* a *grid20.dll* do projektu v aplikaci Visual Studio. Otevřete kartu vlastnost a změňte aliasy z Global na GridV1 a GridV2.

Používat tyto aliasy stejným způsobem jako výše

```csharp
 extern alias GridV1;  
  
 extern alias GridV2;  
```

Nyní můžete vytvořit alias pro obor názvů nebo typ *pomocí direktivy alias*. Další informace najdete v tématu [použití direktivy](using-directive.md).

```csharp
using Class1V1 = GridV1::Namespace.Class1;

using Class1V2 = GridV2::Namespace.Class1;
```

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [:: – Operátor](../operators/namespace-alias-qualifier.md)
- [-Reference (možnosti kompilátoru C#)](../compiler-options/reference-compiler-option.md)
