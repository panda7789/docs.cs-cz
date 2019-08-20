---
title: získat C# odkaz
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 783814a575e95fc9deb5c9cdef235a5636f5f529
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602143"
---
# <a name="get-c-reference"></a>get (Referenční dokumentace jazyka C#)

Klíčové slovo definuje metodu přístupového objektu ve vlastnosti nebo indexeru, který vrací hodnotu vlastnosti nebo prvek indexeru. `get` Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../programming-guide/indexers/index.md).  
  
Následující příklad definuje jak `get` `set` a přístup k vlastnosti s názvem `Seconds`. K zálohování hodnoty vlastnosti používá soukromé `_seconds` pole s názvem.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
`get` Přistupující objekt se často skládá z jediného příkazu, který vrací hodnotu, stejně jako v předchozím příkladu. Počínaje C# 7,0 můžete implementovat `get` přistupující objekt jako člena Expression-těle. Následující příklad implementuje rozhraní `get` `set` a přístup jako členy Expression-těle.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Pro jednoduché případy, kdy přístup k vlastnosti `get` a `set` přistupující objekty neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu C# kompilátoru pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)
