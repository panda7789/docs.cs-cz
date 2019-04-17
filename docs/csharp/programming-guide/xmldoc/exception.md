---
title: <exception> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 639e3a345fc8ed3d348461718f73ead6167158db
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610909"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="03bef-102">\<Výjimka > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="03bef-102">\<exception> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="03bef-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03bef-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="03bef-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="03bef-104">Parameters</span></span>  
 <span data-ttu-id="03bef-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="03bef-105">cref = " `member`"</span></span>  
 <span data-ttu-id="03bef-106">Odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="03bef-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="03bef-107">Kompilátor kontroluje, zda existuje výjimka a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="03bef-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="03bef-108">`member` musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="03bef-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="03bef-109">Další informace o tom, jak formátovat `member` Pokud chcete odkazovat na obecný typ, přečtěte si téma [zpracování souboru XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="03bef-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>
  
 `description`  
 <span data-ttu-id="03bef-110">Popis výjimky.</span><span class="sxs-lookup"><span data-stu-id="03bef-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03bef-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03bef-111">Remarks</span></span>  
 <span data-ttu-id="03bef-112">\<Výjimky > značky umožňuje určit, jaké výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="03bef-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="03bef-113">Toto klíčové slovo lze použít pro definice pro metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="03bef-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="03bef-114">Kompilovat s [/doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="03bef-114">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="03bef-115">Další informace o zpracování výjimek naleznete v tématu [výjimek a zpracování výjimek](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="03bef-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03bef-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="03bef-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="03bef-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03bef-117">See also</span></span>

- [<span data-ttu-id="03bef-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="03bef-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="03bef-119">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="03bef-119">Recommended Tags for Documentation Comments</span></span>](recommended-tags-for-documentation-comments.md)
