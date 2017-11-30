---
title: Struktury (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic]
- user-defined data types [Visual Basic], structures
- user-defined types [Visual Basic], about user-defined types
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], about user-defined data types
- types [Visual Basic], user-defined
ms.assetid: 55e86462-5e99-4d33-8018-6d097ca491b2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de99d67ee31d8fb8e92e0a351142b30f622bf5f0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="structures-visual-basic"></a><span data-ttu-id="b44d7-102">Struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b44d7-102">Structures (Visual Basic)</span></span>
<span data-ttu-id="b44d7-103">A *struktura* je generalizaci uživatelem definovaný typ (UDT) podporované v předchozích verzích nástroje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b44d7-103">A *structure* is a generalization of the user-defined type (UDT) supported by previous versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="b44d7-104">Kromě polí můžou zpřístupnit struktury vlastnosti, metod a události.</span><span class="sxs-lookup"><span data-stu-id="b44d7-104">In addition to fields, structures can expose properties, methods, and events.</span></span> <span data-ttu-id="b44d7-105">Struktury můžete implementovat jednu nebo více rozhraní, a můžou deklarovat individuální úrovně přístupu pro každé pole.</span><span class="sxs-lookup"><span data-stu-id="b44d7-105">A structure can implement one or more interfaces, and you can declare individual access levels for each field.</span></span>  
  
 <span data-ttu-id="b44d7-106">Můžete kombinovat datovými položkami různých typů vytvořit strukturu.</span><span class="sxs-lookup"><span data-stu-id="b44d7-106">You can combine data items of different types to create a structure.</span></span> <span data-ttu-id="b44d7-107">Struktury přidružuje jednu nebo více *elementy* mezi sebou a se strukturou sám sebe.</span><span class="sxs-lookup"><span data-stu-id="b44d7-107">A structure associates one or more *elements* with each other and with the structure itself.</span></span> <span data-ttu-id="b44d7-108">Když jste definice struktury, stane se *složeného datového typu*, a můžou deklarovat proměnné daného typu.</span><span class="sxs-lookup"><span data-stu-id="b44d7-108">When you declare a structure, it becomes a *composite data type*, and you can declare variables of that type.</span></span>  
  
 <span data-ttu-id="b44d7-109">Struktury jsou užitečné, pokud chcete jednu proměnnou pro uložení několik souvisejících informací.</span><span class="sxs-lookup"><span data-stu-id="b44d7-109">Structures are useful when you want a single variable to hold several related pieces of information.</span></span> <span data-ttu-id="b44d7-110">Například můžete chtít zachovat název zaměstnance, telefonní číslo a mzda společně.</span><span class="sxs-lookup"><span data-stu-id="b44d7-110">For example, you might want to keep an employee's name, telephone extension, and salary together.</span></span> <span data-ttu-id="b44d7-111">Tyto informace můžete použít několik proměnné, nebo může definovat strukturu a použít jej pro proměnnou jediného zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="b44d7-111">You could use several variables for this information, or you could define a structure and use it for a single employee variable.</span></span> <span data-ttu-id="b44d7-112">Výhodou strukturu vyvstává zřejmá, pokud máte mnoho pracovníků a proto velký počet instancí proměnné.</span><span class="sxs-lookup"><span data-stu-id="b44d7-112">The advantage of the structure becomes apparent when you have many employees and therefore many instances of the variable.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b44d7-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b44d7-113">In This Section</span></span>  
 [<span data-ttu-id="b44d7-114">Postupy: definice struktury</span><span class="sxs-lookup"><span data-stu-id="b44d7-114">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 <span data-ttu-id="b44d7-115">Ukazuje, jak deklarace struktury a jejích elementů.</span><span class="sxs-lookup"><span data-stu-id="b44d7-115">Shows how to declare a structure and its elements.</span></span>  
  
 [<span data-ttu-id="b44d7-116">Proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="b44d7-116">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 <span data-ttu-id="b44d7-117">Zahrnuje přiřazení do struktury proměnné a přístup k jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="b44d7-117">Covers assigning a structure to a variable and accessing its elements.</span></span>  
  
 [<span data-ttu-id="b44d7-118">Struktury a ostatní programovací elementy</span><span class="sxs-lookup"><span data-stu-id="b44d7-118">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 <span data-ttu-id="b44d7-119">Shrnuje, jak struktury komunikovat s pole, objekty, postupy a navzájem.</span><span class="sxs-lookup"><span data-stu-id="b44d7-119">Summarizes how structures interact with arrays, objects, procedures, and each other.</span></span>  
  
 [<span data-ttu-id="b44d7-120">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="b44d7-120">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 <span data-ttu-id="b44d7-121">Popisuje podobnosti a rozdíly mezi struktury a třídy.</span><span class="sxs-lookup"><span data-stu-id="b44d7-121">Describes the similarities and differences between structures and classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b44d7-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b44d7-122">Related Sections</span></span>  
 [<span data-ttu-id="b44d7-123">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b44d7-123">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="b44d7-124">Zavádí [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy dat a popisuje, jak je používat.</span><span class="sxs-lookup"><span data-stu-id="b44d7-124">Introduces the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="b44d7-125">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b44d7-125">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="b44d7-126">Uvádí základní datové typy poskytl [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b44d7-126">Lists the elementary data types supplied by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>
