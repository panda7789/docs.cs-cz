---
title: <typeparam> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: e5e0d7be46e02bd30799b54246db729ae63ca300
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523284"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="1fe36-102">> \<typeparam (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="1fe36-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1fe36-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fe36-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fe36-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fe36-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1fe36-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1fe36-105">The name of the type parameter.</span></span> <span data-ttu-id="1fe36-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="1fe36-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="1fe36-107">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1fe36-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fe36-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fe36-108">Remarks</span></span>  
 <span data-ttu-id="1fe36-109">Značka `<typeparam>` by měla být použita v komentáři pro obecný typ nebo deklaraci metody pro popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1fe36-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="1fe36-110">Přidejte značku pro každý parametr typu obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="1fe36-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="1fe36-111">Další informace najdete v tématu [Obecné typy](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="1fe36-111">For more information, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="1fe36-112">Text značky `<typeparam>` bude zobrazen v IntelliSense, Webová sestava komentáře kódu [Prohlížeč objektů Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) .</span><span class="sxs-lookup"><span data-stu-id="1fe36-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="1fe36-113">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="1fe36-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fe36-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fe36-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="1fe36-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fe36-115">See also</span></span>

- [<span data-ttu-id="1fe36-116">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="1fe36-116">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="1fe36-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1fe36-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1fe36-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="1fe36-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
