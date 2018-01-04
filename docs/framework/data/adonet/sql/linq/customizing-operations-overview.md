---
title: "Přizpůsobení Operations: Přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9776daa28b0a7ffcd3b721f004f5b9a44dd09f48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="35e29-102">Přizpůsobení Operations: Přehled</span><span class="sxs-lookup"><span data-stu-id="35e29-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="35e29-103">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL pro příkaz insert, update a operace odstranění na základě mapování.</span><span class="sxs-lookup"><span data-stu-id="35e29-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="35e29-104">Nicméně v praxi obvykle chcete přidat vlastní obchodní logiku zajistit pro zabezpečení, ověřování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="35e29-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="35e29-105">techniky pro přizpůsobení tyto operace jsou následující.</span><span class="sxs-lookup"><span data-stu-id="35e29-105"> techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="35e29-106">Načítání možnosti</span><span class="sxs-lookup"><span data-stu-id="35e29-106">Loading Options</span></span>  
 <span data-ttu-id="35e29-107">V dotazech můžete určit, kolik dat souvisejících s vaší hlavní cíl se načítají, když jste připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="35e29-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="35e29-108">Tato funkce je implementována do značné míry pomocí <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="35e29-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="35e29-109">Další informace najdete v tématu [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="35e29-109">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="35e29-110">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="35e29-110">Partial Methods</span></span>  
 <span data-ttu-id="35e29-111">V jeho výchozí mapování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje částečné metody, která vám pomůže implementovat obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="35e29-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="35e29-112">Další informace najdete v tématu [přidání obchodní logiku podle pomocí částečné metody](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="35e29-112">For more information, see [Adding Business Logic By Using Partial Methods](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="35e29-113">Uložené procedury a funkce definované uživatelem</span><span class="sxs-lookup"><span data-stu-id="35e29-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="35e29-114">podporuje použití uložených procedur a uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="35e29-114"> supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="35e29-115">K úpravě operací se často používají uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="35e29-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="35e29-116">Další informace najdete v tématu [uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="35e29-116">For more information, see [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e29-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="35e29-117">See Also</span></span>  
 [<span data-ttu-id="35e29-118">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="35e29-118">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
