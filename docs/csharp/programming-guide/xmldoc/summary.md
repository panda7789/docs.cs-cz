---
title: <summary> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 0e6408f1f45bb5f1406b4b1a7f6fe2cf543109e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493567"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="0053d-102">\<Souhrn > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="0053d-102">\<summary> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="0053d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0053d-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0053d-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0053d-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0053d-105">Přehled objektu.</span><span class="sxs-lookup"><span data-stu-id="0053d-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0053d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0053d-106">Remarks</span></span>  
 <span data-ttu-id="0053d-107">\<Summary > Značka by měla sloužit k popisu typu nebo člena typu.</span><span class="sxs-lookup"><span data-stu-id="0053d-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="0053d-108">Použití [ \<remarks >](../../../csharp/programming-guide/xmldoc/remarks.md) přidat doplňující informace pro popis typu.</span><span class="sxs-lookup"><span data-stu-id="0053d-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="0053d-109">Použití [cref – atribut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) umožňující dokumentace nástroje [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://github.com/EWSoftware/SHFB) k vytvoření interních hypertextových odkazů na stránky dokumentace prvků kódu.</span><span class="sxs-lookup"><span data-stu-id="0053d-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="0053d-110">Text \<summary > značky je jediný zdroj informací o typu v IntelliSense a také se zobrazí v okně prohlížeče objektů.</span><span class="sxs-lookup"><span data-stu-id="0053d-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="0053d-111">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="0053d-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="0053d-112">Chcete-li vytvořit finální dokumentaci na základě souboru generovaného kompilátorem, můžete vytvořit vlastní nástroj nebo použít nástroj, jako [DocFX](https://dotnet.github.io/docfx/) nebo [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="0053d-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0053d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0053d-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 <span data-ttu-id="0053d-114">Předchozí příklad vytváří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="0053d-114">The previous example produces the following XML file.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0053d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0053d-115">Example</span></span>  
 <span data-ttu-id="0053d-116">Následující příklad ukazuje, jak vytvořit `cref` odkaz na obecném typu.</span><span class="sxs-lookup"><span data-stu-id="0053d-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 <span data-ttu-id="0053d-117">Předchozí příklad vytváří následující soubor XML.</span><span class="sxs-lookup"><span data-stu-id="0053d-117">The previous example produces the following XML file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0053d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0053d-118">See also</span></span>

- [<span data-ttu-id="0053d-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0053d-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0053d-120">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="0053d-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
