---
title: "Uložené procedury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cff3103595ccb782e2e51313d427259c0191105d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="stored-procedures"></a><span data-ttu-id="741d7-102">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="741d7-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="741d7-103">používá metody v objektovém modelu k reprezentaci uložené procedury v databázi.</span><span class="sxs-lookup"><span data-stu-id="741d7-103"> uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="741d7-104">Určíte jako uložené procedury pro metody s použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="741d7-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="741d7-105">Další informace najdete v tématu [technologii LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="741d7-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="741d7-106">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] by obvykle použila [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapovat uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="741d7-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map stored procedures.</span></span> <span data-ttu-id="741d7-107">Témata v této části ukazují, jak vytvořit a volání těchto metod ve vaší aplikaci můžete psát kód sami.</span><span class="sxs-lookup"><span data-stu-id="741d7-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="741d7-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="741d7-108">In This Section</span></span>  
 [<span data-ttu-id="741d7-109">Postupy: Vrácení sad řádků</span><span class="sxs-lookup"><span data-stu-id="741d7-109">How to: Return Rowsets</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 <span data-ttu-id="741d7-110">Popisuje, jak vrátit řádky dat a ukazuje, jak používat vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="741d7-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="741d7-111">Postupy: Převzetí parametrů pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="741d7-111">How to: Use Stored Procedures that Take Parameters</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="741d7-112">Popisuje, jak používat vstupní a výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="741d7-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="741d7-113">Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků</span><span class="sxs-lookup"><span data-stu-id="741d7-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="741d7-114">Popisuje, jak zajistit pro vrátí více obrazců ve stejné uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="741d7-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="741d7-115">Postupy: Použití uložených procedur mapovaných pro sekvenční tvary výsledků</span><span class="sxs-lookup"><span data-stu-id="741d7-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="741d7-116">Popisuje, jak zajistit pro více tvarů, kde je známý návratový pořadí.</span><span class="sxs-lookup"><span data-stu-id="741d7-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="741d7-117">Přizpůsobení operací pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="741d7-117">Customizing Operations By Using Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="741d7-118">Popisuje, jak pomocí uložených procedur implementace insert, update a operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="741d7-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="741d7-119">Přizpůsobení operací výhradně pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="741d7-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="741d7-120">Popisuje způsob použití nic ale uložené procedury pro implementace insert, update a operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="741d7-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="741d7-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="741d7-121">Related Sections</span></span>  
 [<span data-ttu-id="741d7-122">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="741d7-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="741d7-123">Poskytuje informace o tom, jak vytvořit a používat vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="741d7-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="741d7-124">Návod: Použití jen uložených procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="741d7-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="741d7-125">Obsahuje postupy, které ukazují, jak pomocí uložené procedury v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="741d7-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="741d7-126">Návod: Použití jen uložených procedur (C#)</span><span class="sxs-lookup"><span data-stu-id="741d7-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="741d7-127">Obsahuje postupy, které ukazují, jak pomocí uložené procedury v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="741d7-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
