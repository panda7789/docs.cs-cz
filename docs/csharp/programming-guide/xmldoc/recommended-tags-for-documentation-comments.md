---
title: Doporučené značky pro dokumentační komentáře – Průvodce programováním v C#
description: Přečtěte si o doporučených značkách pro dokumentační komentáře. Podívejte se na seznam doporučených značek a zobrazte další dostupné prostředky.
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 65bca6f979c5ffd91507b571a4f049377315192d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381512"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)

Kompilátor jazyka C# zpracovává dokumentační komentáře ve vašem kódu a formátuje je jako XML v souboru, jehož název zadáte v parametru příkazového řádku **/doc** . Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).

Značky jsou zpracovávány na konstrukcích kódu, jako jsou typy a členy typu.

> [!NOTE]
> Komentáře k dokumentaci nelze použít pro obor názvů.  
  
 Kompilátor zpracuje všechny značky, které jsou platné XML. Následující značky poskytují všeobecně používané funkce v dokumentaci uživatele.  
  
## <a name="tags"></a>Značky  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
( \* označuje, že kompilátor ověřuje syntaxi.)

Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte kódování HTML `<` , `>` které je `&lt;` a `&gt;` v uvedeném pořadí. Toto kódování je znázorněno v následujícím příkladu.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [-doc (možnosti kompilátoru C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentáře dokumentace XML](./index.md)
