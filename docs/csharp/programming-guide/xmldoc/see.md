---
title: Průvodce C# programováním <see>
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 995b67362bccbc3527f44e5a1d6b659f330e3afd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711711"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="d649e-102">\<najdete v >C# (Průvodce programováním).</span><span class="sxs-lookup"><span data-stu-id="d649e-102">\<see> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d649e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d649e-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d649e-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d649e-104">Parameters</span></span>  
 <span data-ttu-id="d649e-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="d649e-105">cref = " `member`"</span></span>  
 <span data-ttu-id="d649e-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="d649e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d649e-107">Kompilátor zkontroluje, zda daný prvek kódu existuje a předá `member` k názvu elementu ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="d649e-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="d649e-108">Umístit *člena* v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="d649e-108">Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d649e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d649e-109">Remarks</span></span>  
 <span data-ttu-id="d649e-110">\<Zobrazit značku > umožňuje zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="d649e-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="d649e-111">Použijte [\<seealso >](./seealso.md) k označení toho, že text by měl být umístěn v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="d649e-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="d649e-112">Pomocí [atributu cref](./cref-attribute.md) můžete vytvořit interní hypertextové odkazy na stránky dokumentace pro prvky kódu.</span><span class="sxs-lookup"><span data-stu-id="d649e-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="d649e-113">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="d649e-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="d649e-114">Následující příklad ukazuje \<zobrazení značky > v rámci oddílu Summary.</span><span class="sxs-lookup"><span data-stu-id="d649e-114">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a><span data-ttu-id="d649e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d649e-115">See also</span></span>

- [<span data-ttu-id="d649e-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d649e-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d649e-117">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="d649e-117">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
