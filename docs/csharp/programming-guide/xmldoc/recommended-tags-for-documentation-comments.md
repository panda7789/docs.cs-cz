---
title: Doporučené značky pro komentáře k dokumentaci – průvodce programováním jazyka C#
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789729"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Doporučené značky pro komentáře k dokumentaci (průvodce programováním jazyka C#)

Kompilátor Jazyka C# zpracovává komentáře dokumentace ve vašem kódu a formátuje je jako XML v souboru, jehož název zadáte v možnosti příkazového řádku **/doc.** Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).

Značky jsou zpracovány na konstrukce kódu, jako jsou typy a členy typu.

> [!NOTE]
> Komentáře dokumentace nelze použít v oboru názvů.  
  
 Kompilátor zpracuje všechny značky, které jsou platné XML. Následující značky poskytují obecně používané funkce v uživatelské dokumentaci.  
  
## <a name="tags"></a>Značky  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<viz>](./see.md)*|[\<hodnota>](./value.md)  
|[\<kód>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<příklad>](./example.md)|[\<paramref>](./paramref.md)|[\<souhrnný>](./summary.md)|  
|[\<výjimka>](./exception.md)*|[\<>oprávnění](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<patří>](./include.md)*|[\<poznámky>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<seznam>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<vrátí>](./returns.md)|
  
(\* označuje, že kompilátor ověřuje syntaxi.)

Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly `<` `>` úhlové `&lt;` `&gt;` závorky, použijte kódování HTML a které je a v uvedeném pořadí. Toto kódování je uvedeno v následujícím příkladu.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [-doc (možnosti kompilátoru Jazyka C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentáře dokumentace XML](./index.md)
