---
title: <summary> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 63c65e11a274779015cf99859b7fa67bb536529d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711685"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="66b10-102">> \<souhrnuC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="66b10-102">\<summary> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="66b10-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66b10-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="66b10-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="66b10-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="66b10-105">Souhrn objektu.</span><span class="sxs-lookup"><span data-stu-id="66b10-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66b10-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66b10-106">Remarks</span></span>  
 <span data-ttu-id="66b10-107">K popisu typu nebo členu typu by měla být použita značka \<Summary >.</span><span class="sxs-lookup"><span data-stu-id="66b10-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="66b10-108">Pomocí [\<poznámky >](./remarks.md) přidat doplňující informace k popisu typu.</span><span class="sxs-lookup"><span data-stu-id="66b10-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="66b10-109">Pomocí [atributu cref](./cref-attribute.md) můžete povolit nástroje dokumentace, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) , a vytvářet interní hypertextové odkazy na stránky dokumentace pro prvky kódu.</span><span class="sxs-lookup"><span data-stu-id="66b10-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="66b10-110">Text > Značka \<Summary je jediným zdrojem informací o typu v technologii IntelliSense a je také zobrazen v okně Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="66b10-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="66b10-111">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="66b10-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="66b10-112">Chcete-li vytvořit konečnou dokumentaci založenou na souboru generovaném kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako je [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="66b10-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66b10-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="66b10-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 <span data-ttu-id="66b10-114">Předchozí příklad vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="66b10-114">The previous example produces the following XML file.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="66b10-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="66b10-115">Example</span></span>  
 <span data-ttu-id="66b10-116">Následující příklad ukazuje, jak vytvořit `cref` odkaz na obecný typ.</span><span class="sxs-lookup"><span data-stu-id="66b10-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 <span data-ttu-id="66b10-117">Předchozí příklad vytvoří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="66b10-117">The previous example produces the following XML file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66b10-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66b10-118">See also</span></span>

- [<span data-ttu-id="66b10-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="66b10-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="66b10-120">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="66b10-120">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
