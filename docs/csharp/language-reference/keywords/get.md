---
title: získat C# odkaz
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: d6c0452a7890a6ade480054115c1383199a3f91c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713496"
---
# <a name="get-c-reference"></a>get (Referenční dokumentace jazyka C#)

Klíčové slovo `get` definuje metodu *přistupujícího objektu* ve vlastnosti nebo indexeru, která vrací hodnotu vlastnosti nebo prvek indexeru. Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../programming-guide/indexers/index.md).  
  
Následující příklad definuje `get` a přístupový objekt `set` pro vlastnost s názvem `Seconds`. Pro zálohu hodnoty vlastnosti používá soukromé pole s názvem `_seconds`.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Přístupový objekt `get` se často skládá z jediného příkazu, který vrací hodnotu, stejně jako v předchozím příkladu. Počínaje C# 7,0 můžete implementovat přistupující objekt `get` jako člena Expression-těle. Následující příklad implementuje `get` a přístupový objekt `set` jako členy Expression-těle.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Pro jednoduché případy, kdy `get` a přistupující objekty `set` neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu C# kompilátoru pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>C# – jazyková specifikace

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)
