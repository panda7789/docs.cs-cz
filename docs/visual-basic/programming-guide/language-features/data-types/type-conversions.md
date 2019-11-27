---
title: Převody typu
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: fbf0c9877cf9a9b4364c8c058c61e847ad7bf049
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348713"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="f67fa-102">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f67fa-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="f67fa-103">Proces změny hodnoty z jednoho datového typu na jiný typ se nazývá *Převod*.</span><span class="sxs-lookup"><span data-stu-id="f67fa-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="f67fa-104">Převody jsou buď *rozšiřující* nebo *zúžené*, v závislosti na datových přenosech souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="f67fa-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="f67fa-105">Jsou také *implicitní* nebo *explicitní*v závislosti na syntaxi ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="f67fa-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f67fa-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f67fa-106">In This Section</span></span>  
 [<span data-ttu-id="f67fa-107">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="f67fa-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="f67fa-108">Vysvětluje převody klasifikované podle toho, zda cílový typ může uchovávat data.</span><span class="sxs-lookup"><span data-stu-id="f67fa-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="f67fa-109">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="f67fa-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="f67fa-110">Popisuje převody klasifikované podle toho, zda je Visual Basic provádí automaticky.</span><span class="sxs-lookup"><span data-stu-id="f67fa-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="f67fa-111">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="f67fa-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="f67fa-112">Ukazuje převod mezi řetězci a číselnými, `Boolean`mi nebo hodnotami data a času.</span><span class="sxs-lookup"><span data-stu-id="f67fa-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="f67fa-113">Postupy: převod objektu na jiný typ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f67fa-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="f67fa-114">Ukazuje, jak převést `Object` proměnnou na jakýkoli jiný datový typ.</span><span class="sxs-lookup"><span data-stu-id="f67fa-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="f67fa-115">Převody polí</span><span class="sxs-lookup"><span data-stu-id="f67fa-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="f67fa-116">Provede kroky převodu mezi poli různých datových typů.</span><span class="sxs-lookup"><span data-stu-id="f67fa-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f67fa-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f67fa-117">Related Sections</span></span>  
 [<span data-ttu-id="f67fa-118">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f67fa-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="f67fa-119">Zavádí Visual Basic datových typů a popisuje, jak je používat.</span><span class="sxs-lookup"><span data-stu-id="f67fa-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="f67fa-120">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f67fa-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="f67fa-121">Uvádí základní datové typy, které poskytuje Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f67fa-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="f67fa-122">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="f67fa-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="f67fa-123">Popisuje některé běžné problémy, které mohou nastat při práci s datovými typy.</span><span class="sxs-lookup"><span data-stu-id="f67fa-123">Discusses some common problems that can arise when working with data types.</span></span>
