---
title: <summary> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 4a509c002bb6a55b4751712925ae7cc613911af2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587616"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="4cfae-102">\<souhrnný > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4cfae-102">\<summary> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="4cfae-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cfae-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cfae-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cfae-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="4cfae-105">Souhrn objektu.</span><span class="sxs-lookup"><span data-stu-id="4cfae-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cfae-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cfae-106">Remarks</span></span>  
 <span data-ttu-id="4cfae-107">Značka \<> souhrnu by měla být použita k popisu typu nebo člena typu.</span><span class="sxs-lookup"><span data-stu-id="4cfae-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="4cfae-108">K přidání doplňujících informací do popisu typu použijte [ \<poznámky >](./remarks.md) .</span><span class="sxs-lookup"><span data-stu-id="4cfae-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="4cfae-109">Pomocí [atributu cref](./cref-attribute.md) můžete povolit nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , a vytvářet interní hypertextové odkazy na stránky dokumentace pro prvky kódu.</span><span class="sxs-lookup"><span data-stu-id="4cfae-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="4cfae-110">Text pro \<značku Summary > je jediným zdrojem informací o typu v technologii IntelliSense a je také zobrazen v okně Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="4cfae-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="4cfae-111">Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="4cfae-111">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="4cfae-112">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="4cfae-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cfae-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cfae-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 <span data-ttu-id="4cfae-114">Předchozí příklad vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="4cfae-114">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="4cfae-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cfae-115">Example</span></span>  
 <span data-ttu-id="4cfae-116">Následující příklad ukazuje, jak vytvořit `cref` odkaz na obecný typ.</span><span class="sxs-lookup"><span data-stu-id="4cfae-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 <span data-ttu-id="4cfae-117">Předchozí příklad vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="4cfae-117">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cfae-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cfae-118">See also</span></span>

- [<span data-ttu-id="4cfae-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4cfae-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4cfae-120">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4cfae-120">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
