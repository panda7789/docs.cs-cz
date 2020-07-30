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
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="8393d-104">Doporučené značky pro dokumentační komentáře (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8393d-104">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="8393d-105">Kompilátor jazyka C# zpracovává dokumentační komentáře ve vašem kódu a formátuje je jako XML v souboru, jehož název zadáte v parametru příkazového řádku **/doc** .</span><span class="sxs-lookup"><span data-stu-id="8393d-105">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="8393d-106">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="8393d-106">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="8393d-107">Značky jsou zpracovávány na konstrukcích kódu, jako jsou typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="8393d-107">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="8393d-108">Komentáře k dokumentaci nelze použít pro obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8393d-108">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="8393d-109">Kompilátor zpracuje všechny značky, které jsou platné XML.</span><span class="sxs-lookup"><span data-stu-id="8393d-109">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="8393d-110">Následující značky poskytují všeobecně používané funkce v dokumentaci uživatele.</span><span class="sxs-lookup"><span data-stu-id="8393d-110">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="8393d-111">Značky</span><span class="sxs-lookup"><span data-stu-id="8393d-111">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
<span data-ttu-id="8393d-112">( \* označuje, že kompilátor ověřuje syntaxi.)</span><span class="sxs-lookup"><span data-stu-id="8393d-112">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="8393d-113">Pokud chcete, aby se v textu komentáře k dokumentaci zobrazovaly lomené závorky, použijte kódování HTML `<` , `>` které je `&lt;` a `&gt;` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8393d-113">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="8393d-114">Toto kódování je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8393d-114">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="8393d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8393d-115">See also</span></span>

- [<span data-ttu-id="8393d-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8393d-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8393d-117">-doc (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="8393d-117">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="8393d-118">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="8393d-118">XML documentation comments</span></span>](./index.md)
