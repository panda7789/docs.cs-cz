---
title: Struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic]
- user-defined data types [Visual Basic], structures
- user-defined types [Visual Basic], about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
ms.openlocfilehash: ebfc82665bb18d96c83db8f29a6c206a9a71fd7f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925783"
---
# <a name="structures-visual-basic"></a><span data-ttu-id="45f87-102">Struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45f87-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="45f87-103">A *struktura* je generalizace uživatelem definovaný typ (UDT) podporované v předchozích verzích jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="45f87-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of Visual Basic.</span></span> <span data-ttu-id="45f87-104">Kromě polí můžete zveřejnit struktury vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="45f87-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="45f87-105">Struktura může implementovat jedno nebo více rozhraní a je možné deklarovat individuální úrovně přístupu pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="45f87-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="45f87-106">Můžete kombinovat data položky různých typů vytvořit strukturu.</span><span class="sxs-lookup"><span data-stu-id="45f87-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="45f87-107">Struktura přidružuje jednu nebo více *prvky* mezi sebou a s struktury samotné.</span><span class="sxs-lookup"><span data-stu-id="45f87-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="45f87-108">Když je deklarovat strukturu, stane se *složené datový typ*, a můžete deklarovat proměnné tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="45f87-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="45f87-109">Struktury jsou užitečné, pokud chcete jednu proměnnou pro uchování několik související údaje.</span><span class="sxs-lookup"><span data-stu-id="45f87-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="45f87-110">Například můžete chtít zachovat název zaměstnance, telefonní číslo a salary společně.</span><span class="sxs-lookup"><span data-stu-id="45f87-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="45f87-111">Tyto informace můžete použít několik proměnných, nebo může definovat strukturu a použít ji pro proměnnou jednoho zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="45f87-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="45f87-112">Výhodou struktury pocítíte, když máte mnoho zaměstnanců a proto velký počet instancí proměnné.</span><span class="sxs-lookup"><span data-stu-id="45f87-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45f87-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="45f87-113">In This Section</span></span>  
 [<span data-ttu-id="45f87-114">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="45f87-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="45f87-115">Ukazuje, jak deklarovat strukturu a jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="45f87-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="45f87-116">Proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="45f87-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="45f87-117">Popisuje strukturu přiřadí proměnné a přístup k jeho prvkům.</span><span class="sxs-lookup"><span data-stu-id="45f87-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="45f87-118">Struktury a ostatní programovací elementy</span><span class="sxs-lookup"><span data-stu-id="45f87-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="45f87-119">Shrnuje interakci struktury s poli, objekty, postupy a mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="45f87-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="45f87-120">Struktury a třídy</span><span class="sxs-lookup"><span data-stu-id="45f87-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="45f87-121">Popisuje podobnosti a rozdíly mezi strukturami a třídami.</span><span class="sxs-lookup"><span data-stu-id="45f87-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="45f87-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="45f87-122">Related Sections</span></span>  
 [<span data-ttu-id="45f87-123">Datové typy</span><span class="sxs-lookup"><span data-stu-id="45f87-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="45f87-124">Představuje datové typy jazyka Visual Basic a popisuje, jak je používat.</span><span class="sxs-lookup"><span data-stu-id="45f87-124">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="45f87-125">Datové typy</span><span class="sxs-lookup"><span data-stu-id="45f87-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="45f87-126">Seznam základních datových typů poskytnutých jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="45f87-126">Lists the elementary data types supplied by Visual Basic.</span></span>
