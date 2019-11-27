---
title: Čistě funkční transformace XML
ms.date: 07/20/2015
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
ms.openlocfilehash: cccc1321d934dca5563a1e9e52af9352231bd558
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346604"
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="9a978-102">Čistě funkční transformace jazyka XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a978-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="9a978-103">V této části najdete návod k funkční transformaci XML.</span><span class="sxs-lookup"><span data-stu-id="9a978-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="9a978-104">To zahrnuje Vysvětlení hlavních konceptů a konstrukcí jazyka, které je nutné pochopit pro použití funkčních transformací, a příklady použití funkcí transformace k manipulaci s dokumentem XML.</span><span class="sxs-lookup"><span data-stu-id="9a978-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="9a978-105">I když tento kurz poskytuje LINQ to XML příklady kódu, všechny základní koncepty platí i pro jiné technologie LINQ.</span><span class="sxs-lookup"><span data-stu-id="9a978-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="9a978-106">[Kurz: manipulace s obsahem v kurzu WordprocessingML dokumentu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) poskytuje řadu příkladů, které každá sestaví na předchozí straně.</span><span class="sxs-lookup"><span data-stu-id="9a978-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="9a978-107">Tyto příklady ukazují čistě funkční transformační přístup k manipulaci s XML.</span><span class="sxs-lookup"><span data-stu-id="9a978-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="9a978-108">Tento kurz předpokládá praktickou znalost Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9a978-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="9a978-109">Podrobné sémantiky jazykových konstrukcí nejsou v tomto kurzu k dispozici, ale odkazy jsou k dispozici v příslušné jazykové dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="9a978-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="9a978-110">Předpokládá se i praktické znalosti základních konceptů počítačové vědy a XML, včetně oborů názvů XML.</span><span class="sxs-lookup"><span data-stu-id="9a978-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a978-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9a978-111">In This Section</span></span>  
  
|<span data-ttu-id="9a978-112">Téma</span><span class="sxs-lookup"><span data-stu-id="9a978-112">Topic</span></span>|<span data-ttu-id="9a978-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9a978-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9a978-114">Úvod do čistě funkční transformace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a978-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="9a978-115">Popisuje funkční transformace a definuje relevantní terminologie.</span><span class="sxs-lookup"><span data-stu-id="9a978-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="9a978-116">Kurz: odložené provádění (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a978-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)|<span data-ttu-id="9a978-117">Popisuje opožděné vyhodnocení a odložené provádění podrobněji.</span><span class="sxs-lookup"><span data-stu-id="9a978-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="9a978-118">Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a978-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="9a978-119">Kurz, který demonstruje funkční transformaci.</span><span class="sxs-lookup"><span data-stu-id="9a978-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a978-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a978-120">See also</span></span>

- [<span data-ttu-id="9a978-121">Dotazování na stromy XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a978-121">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
