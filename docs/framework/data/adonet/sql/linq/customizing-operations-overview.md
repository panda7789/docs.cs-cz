---
title: 'Přizpůsobení operací: Přehled'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 48116887471709c60c9666f68c7ebdd0e6d128a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247515"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="d3ef6-102">Přizpůsobení operací: Přehled</span><span class="sxs-lookup"><span data-stu-id="d3ef6-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="d3ef6-103">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL pro operace vložení, aktualizace a odstranění na základě mapování.</span><span class="sxs-lookup"><span data-stu-id="d3ef6-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="d3ef6-104">V praxi však obvykle budete chtít přidat vlastní obchodní logiku pro zajištění zabezpečení, ověřování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d3ef6-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d3ef6-105">mezi techniky přizpůsobení těchto operací patří následující.</span><span class="sxs-lookup"><span data-stu-id="d3ef6-105">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="d3ef6-106">Možnosti načítání</span><span class="sxs-lookup"><span data-stu-id="d3ef6-106">Loading Options</span></span>  
 <span data-ttu-id="d3ef6-107">V dotazech můžete určit, kolik dat souvisejících s vaším hlavním cílem bude načteno při připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="d3ef6-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="d3ef6-108">Tato funkce je implementována převážně pomocí <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="d3ef6-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="d3ef6-109">Další informace najdete v tématu [odložené porovnání a okamžité načítání](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="d3ef6-109">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="d3ef6-110">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="d3ef6-110">Partial Methods</span></span>  
 <span data-ttu-id="d3ef6-111">V jeho výchozím mapování poskytuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] částečné metody, které vám pomůžou s implementací obchodní logiky.</span><span class="sxs-lookup"><span data-stu-id="d3ef6-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="d3ef6-112">Další informace najdete v tématu [Přidání obchodní logiky pomocí částečných metod](adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d3ef6-112">For more information, see [Adding Business Logic By Using Partial Methods](adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="d3ef6-113">Uložené procedury a uživatelsky definované funkce</span><span class="sxs-lookup"><span data-stu-id="d3ef6-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d3ef6-114">podporuje použití uložených procedur a uživatelsky definovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="d3ef6-114">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="d3ef6-115">Uložené procedury se často používají k přizpůsobení operací.</span><span class="sxs-lookup"><span data-stu-id="d3ef6-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="d3ef6-116">Další informace najdete v tématu [uložené procedury](stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d3ef6-116">For more information, see [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ef6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3ef6-117">See also</span></span>

- [<span data-ttu-id="d3ef6-118">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="d3ef6-118">Customizing Insert, Update, and Delete Operations</span></span>](customizing-insert-update-and-delete-operations.md)
