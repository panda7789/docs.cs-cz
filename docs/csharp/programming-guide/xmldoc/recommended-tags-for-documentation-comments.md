---
title: Doporučené značky pro dokumentační komentáře – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 4506402c85096ae0ae11b28ad03646c7fa215e5a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587813"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)
C# Kompilátor zpracovává dokumentační komentáře ve vašem kódu a formátuje je jako XML v souboru, jehož název zadáte v parametru příkazového řádku **/doc** . Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Značky jsou zpracovávány na konstrukcích kódu, jako jsou typy a členy typu.  
  
> [!NOTE]
>  Komentáře k dokumentaci nelze použít pro obor názvů.  
  
 Kompilátor zpracuje všechny značky, které jsou platné XML. Následující značky poskytují všeobecně používané funkce v dokumentaci uživatele.  
  
## <a name="tags"></a>Značky  
  
||||  
|---|---|---|  
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|  
|[\<> kódu](./code.md)|[\<> param](./param.md)*|[\<SeeAlso >](./seealso.md)*|  
|[\<Příklad >](./example.md)|[\<paramref >](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<> oprávnění](./permission.md)*|[\<typeparam >](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref >](./typeparamref.md)|  
|[\<list>](./list.md)|[\<returns>](./returns.md)|[\<value>](./value.md)|  
  
 (* označuje, že kompilátor ověřuje syntaxi.)  
  
 Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, `<` použijte kódování `>` HTML, které je `&lt;` a `&gt;` v uvedeném pořadí. Toto kódování je znázorněno v následujícím příkladu:
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [/doc (C# možnosti kompilátoru)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Dokumentační komentáře XML](./index.md)
