---
title: Převody typů v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1487d98f37e7ef00982de365d0d164435f84567
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="4b2c5-102">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b2c5-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="4b2c5-103">Proces změny hodnoty z jednoho datového typu na jiný typ se nazývá *převod*.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="4b2c5-104">Převody jsou buď *rozšiřující* nebo *zužující*, v závislosti na data kapacitou typy související se situací.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="4b2c5-105">Jsou i *implicitní* nebo *explicitní*, v závislosti na syntaxi ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b2c5-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4b2c5-106">In This Section</span></span>  
 [<span data-ttu-id="4b2c5-107">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="4b2c5-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="4b2c5-108">Vysvětluje převody klasifikovaný sloupcem jestli typ cíle může obsahovat data.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="4b2c5-109">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="4b2c5-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="4b2c5-110">Popisuje převody klasifikovaný sloupcem jestli jazyka Visual Basic provádí je automaticky.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="4b2c5-111">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="4b2c5-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="4b2c5-112">Znázorňuje převádění mezi řetězci a číselné literály, `Boolean`, nebo hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="4b2c5-113">Postupy: převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b2c5-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="4b2c5-114">Ukazuje, jak převést `Object` proměnnou ostatních typů dat.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="4b2c5-115">Převody polí</span><span class="sxs-lookup"><span data-stu-id="4b2c5-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="4b2c5-116">Vás provede procesem převodu mezi poli s různými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4b2c5-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4b2c5-117">Related Sections</span></span>  
 [<span data-ttu-id="4b2c5-118">Datové typy</span><span class="sxs-lookup"><span data-stu-id="4b2c5-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="4b2c5-119">Představuje Visual Basic – datové typy a popisuje jejich použití.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="4b2c5-120">Datové typy</span><span class="sxs-lookup"><span data-stu-id="4b2c5-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="4b2c5-121">Uvádí základní datové typy poskytl jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="4b2c5-122">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="4b2c5-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="4b2c5-123">Popisuje některé běžné problémy, které mohou nastat při práci s datovými typy.</span><span class="sxs-lookup"><span data-stu-id="4b2c5-123">Discusses some common problems that can arise when working with data types.</span></span>
