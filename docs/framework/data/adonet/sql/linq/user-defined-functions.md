---
title: "Uživatelem definované funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 833ffbbccfb35fd51ddde5dbeb4e3de3d79923ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="user-defined-functions"></a><span data-ttu-id="d139f-102">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="d139f-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d139f-103">používá metody v objektovém modelu k reprezentaci uživatelsky definované funkce.</span><span class="sxs-lookup"><span data-stu-id="d139f-103"> uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="d139f-104">Jako funkce určíte použitím metody <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="d139f-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="d139f-105">Další informace najdete v tématu [technologii LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="d139f-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="d139f-106">Aby nedošlo <xref:System.InvalidOperationException>, uživatelsky definované funkce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být v jednom z následujících podob:</span><span class="sxs-lookup"><span data-stu-id="d139f-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
-   <span data-ttu-id="d139f-107">Zabalená funkce jako volání metody s atributy správné mapování.</span><span class="sxs-lookup"><span data-stu-id="d139f-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="d139f-108">Další informace najdete v tématu [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="d139f-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
-   <span data-ttu-id="d139f-109">Statickou metodu SQL specifické pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d139f-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
-   <span data-ttu-id="d139f-110">Funkce nepodporuje [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] metoda.</span><span class="sxs-lookup"><span data-stu-id="d139f-110">A function supported by a [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] method.</span></span>  
  
 <span data-ttu-id="d139f-111">Témata v této části ukazují, jak vytvořit a volání těchto metod ve vaší aplikaci můžete psát kód sami.</span><span class="sxs-lookup"><span data-stu-id="d139f-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="d139f-112">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] by obvykle použila [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapovat uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="d139f-112">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d139f-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d139f-113">In This Section</span></span>  
 [<span data-ttu-id="d139f-114">Postupy: Použití uživatelem definovaných funkcí se skalárními hodnotami</span><span class="sxs-lookup"><span data-stu-id="d139f-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="d139f-115">Popisuje, jak implementovat funkci, která vrátí skalárních hodnot.</span><span class="sxs-lookup"><span data-stu-id="d139f-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="d139f-116">Postupy: Použití uživatelem definovaných funkcí s tabulkovými hodnotami</span><span class="sxs-lookup"><span data-stu-id="d139f-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="d139f-117">Popisuje, jak implementovat funkci, která vrátí tabulku hodnot.</span><span class="sxs-lookup"><span data-stu-id="d139f-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="d139f-118">Postupy: Volání vložených funkcí definovaných uživatelem</span><span class="sxs-lookup"><span data-stu-id="d139f-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="d139f-119">Popisuje, jak provádět volání vnořené funkce a rozdíly ve zpracování při volání vnořené.</span><span class="sxs-lookup"><span data-stu-id="d139f-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
