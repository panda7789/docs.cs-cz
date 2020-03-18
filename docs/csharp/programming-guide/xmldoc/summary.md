---
title: <summary> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789677"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="41d57-102">\<souhrnný> (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="41d57-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="41d57-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41d57-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="41d57-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="41d57-104">Parameters</span></span>

- `description`

  <span data-ttu-id="41d57-105">Souhrn objektu.</span><span class="sxs-lookup"><span data-stu-id="41d57-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="41d57-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41d57-106">Remarks</span></span>

<span data-ttu-id="41d57-107">Značka \<souhrnné> by měla být použita k popisu typu nebo člena typu.</span><span class="sxs-lookup"><span data-stu-id="41d57-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="41d57-108">Pomocí [ \<poznámek>](./remarks.md) přidejte doplňující informace k popisu typu.</span><span class="sxs-lookup"><span data-stu-id="41d57-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="41d57-109">Pomocí [atributu cref](./cref-attribute.md) povolte nástroje pro dokumentaci, jako jsou [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle,](https://github.com/EWSoftware/SHFB) k vytvoření interních hypertextových odkazů na stránky dokumentace pro prvky kódu.</span><span class="sxs-lookup"><span data-stu-id="41d57-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="41d57-110">Text souhrnné \<značky> je jediným zdrojem informací o typu v prostředí IntelliSense a zobrazuje se také v okně prohlížeče objektů.</span><span class="sxs-lookup"><span data-stu-id="41d57-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="41d57-111">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="41d57-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="41d57-112">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="41d57-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="41d57-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="41d57-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="41d57-114">V předchozím příkladu se vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="41d57-114">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            <seealso cref="M:TestClass.Main"/>
            </summary>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="41d57-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="41d57-115">Example</span></span>

<span data-ttu-id="41d57-116">Následující příklad ukazuje, jak `cref` vytvořit odkaz na obecný typ.</span><span class="sxs-lookup"><span data-stu-id="41d57-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="41d57-117">V předchozím příkladu se vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="41d57-117">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="41d57-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="41d57-118">See also</span></span>

- [<span data-ttu-id="41d57-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="41d57-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="41d57-120">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="41d57-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
