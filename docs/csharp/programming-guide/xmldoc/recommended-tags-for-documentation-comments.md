---
title: Doporučené značky pro dokumentační komentáře – C# Průvodce programováním
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789729"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Doporučené značky pro dokumentační komentáře (C# Průvodce programováním)

C# Kompilátor zpracovává dokumentační komentáře ve vašem kódu a formátuje je jako XML v souboru, jehož název zadáte v parametru příkazového řádku **/doc** . Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).

Značky jsou zpracovávány na konstrukcích kódu, jako jsou typy a členy typu.

> [!NOTE]
> Komentáře k dokumentaci nelze použít pro obor názvů.  
  
 Kompilátor zpracuje všechny značky, které jsou platné XML. Následující značky poskytují všeobecně používané funkce v dokumentaci uživatele.  
  
## <a name="tags"></a>Značky  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[kód \<](./code.md)|[\<param](./param.md)*|[\<seealso >](./seealso.md)*|  
|[\<příklad >](./example.md)|[\<paramref >](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[> oprávnění\<](./permission.md)*|[\<typeparam >](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref >](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc >](./inheritdoc.md)|[\<returns>](./returns.md)|
  
(\* označuje, že kompilátor ověřuje syntaxi.)

Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte kódování HTML `<` a `>`, které `&lt;` a `&gt;`. Toto kódování je znázorněno v následujícím příkladu.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Viz také:

- [C#Průvodce programováním](../index.md)
- [-doc (C# možnosti kompilátoru)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Dokumentační komentáře XML](./index.md)
