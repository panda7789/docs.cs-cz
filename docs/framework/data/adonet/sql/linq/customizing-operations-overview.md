---
title: 'Přizpůsobení operací: Přehled'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 29fb75271b7bc324d462078e94e4a28534986fba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038081"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="80991-102">Přizpůsobení operací: Přehled</span><span class="sxs-lookup"><span data-stu-id="80991-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="80991-103">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL pro vložení, aktualizace nebo odstranění operace založené na mapování.</span><span class="sxs-lookup"><span data-stu-id="80991-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="80991-104">Nicméně v praxi obvykle chcete přidat vlastní obchodní logikou poskytnout zabezpečení, ověřování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="80991-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="80991-105">techniky pro přizpůsobení tyto operace patří.</span><span class="sxs-lookup"><span data-stu-id="80991-105">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="80991-106">Možnosti načítání</span><span class="sxs-lookup"><span data-stu-id="80991-106">Loading Options</span></span>  
 <span data-ttu-id="80991-107">V dotazech můžete určit, kolik data související s hlavním cílem je načten při připojení k databázi.</span><span class="sxs-lookup"><span data-stu-id="80991-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="80991-108">Tato funkce je implementována do značné míry pomocí <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="80991-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="80991-109">Další informace najdete v tématu [odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="80991-109">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="80991-110">Částečné metody</span><span class="sxs-lookup"><span data-stu-id="80991-110">Partial Methods</span></span>  
 <span data-ttu-id="80991-111">V jeho výchozí mapování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje částečným metodám, aby vám pomohly implementovat obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="80991-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="80991-112">Další informace najdete v tématu [přidání obchodní logiky pomocí částečné metody](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="80991-112">For more information, see [Adding Business Logic By Using Partial Methods](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="80991-113">Uložených procedur a uživatelem definovaných funkcí</span><span class="sxs-lookup"><span data-stu-id="80991-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="80991-114">podporuje použití uložených procedur a uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="80991-114">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="80991-115">Uložené procedury se často používají k přizpůsobení operací.</span><span class="sxs-lookup"><span data-stu-id="80991-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="80991-116">Další informace najdete v tématu [uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="80991-116">For more information, see [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80991-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80991-117">See also</span></span>

- [<span data-ttu-id="80991-118">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="80991-118">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
