---
title: Uložené procedury
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 80ea105eef33ebb2a0e52d91a631258400ea3dff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792489"
---
# <a name="stored-procedures"></a><span data-ttu-id="be4c3-102">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="be4c3-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="be4c3-103">používá metody v objektovém modelu k vyjádření uložených procedur v databázi.</span><span class="sxs-lookup"><span data-stu-id="be4c3-103">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="be4c3-104">Metody jako uložené procedury určíte použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atributu a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="be4c3-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="be4c3-105">Další informace najdete v tématu [model objektu LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="be4c3-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="be4c3-106">Vývojáři, kteří používají Visual Studio, by obvykle používali Návrhář relací objektů k mapování uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="be4c3-106">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="be4c3-107">Témata v této části ukazují, jak vytvořit a volat tyto metody v aplikaci, pokud píšete kód sami.</span><span class="sxs-lookup"><span data-stu-id="be4c3-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be4c3-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="be4c3-108">In This Section</span></span>  
 [<span data-ttu-id="be4c3-109">Postupy: Vrátit sady řádků</span><span class="sxs-lookup"><span data-stu-id="be4c3-109">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="be4c3-110">Popisuje, jak vracet řádky dat a ukazuje, jak použít vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="be4c3-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="be4c3-111">Postupy: Použití uložených procedur, které přijímají parametry</span><span class="sxs-lookup"><span data-stu-id="be4c3-111">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="be4c3-112">Popisuje, jak používat vstupní a výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="be4c3-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="be4c3-113">Postupy: Použití uložených procedur mapovaných pro více obrazců výsledků</span><span class="sxs-lookup"><span data-stu-id="be4c3-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="be4c3-114">Popisuje, jak poskytnout pro vrácení více tvarů ve stejné uložené proceduře.</span><span class="sxs-lookup"><span data-stu-id="be4c3-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="be4c3-115">Postupy: Použití uložených procedur mapovaných pro obrazce sekvenčních výsledků</span><span class="sxs-lookup"><span data-stu-id="be4c3-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="be4c3-116">Popisuje, jak poskytnout více obrazcům, kde je známá sekvence vrácení.</span><span class="sxs-lookup"><span data-stu-id="be4c3-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="be4c3-117">Přizpůsobení operací pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="be4c3-117">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="be4c3-118">Popisuje způsob použití uložených procedur k implementaci operací vložení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="be4c3-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="be4c3-119">Přizpůsobení operací výhradně pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="be4c3-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="be4c3-120">Popisuje, jak použít Nothing, ale uložené procedury k implementaci operací vložení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="be4c3-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="be4c3-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="be4c3-121">Related Sections</span></span>  
 [<span data-ttu-id="be4c3-122">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="be4c3-122">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="be4c3-123">Poskytuje informace o tom, jak vytvořit a použít [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="be4c3-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="be4c3-124">Návod: Použití pouze uložených procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be4c3-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="be4c3-125">Obsahuje postupy, které ilustrují použití uložených procedur v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="be4c3-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="be4c3-126">Návod: Použití pouze uložených procedur (C#)</span><span class="sxs-lookup"><span data-stu-id="be4c3-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="be4c3-127">Obsahuje postupy, které ilustrují použití uložených procedur v C#.</span><span class="sxs-lookup"><span data-stu-id="be4c3-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
