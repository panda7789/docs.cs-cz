---
title: Přizpůsobení operací vložení, aktualizace a odstranění
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: 114447fd45806e567b4fde8e9e74138c096bff07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743568"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="18e5e-102">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="18e5e-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="18e5e-103">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL implementovat vložit, číst, aktualizovat a odstraňovat operace.</span><span class="sxs-lookup"><span data-stu-id="18e5e-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="18e5e-104">V praxi však obvykle přizpůsobíte aplikaci tak, aby vyhovovala vašim obchodním potřebám.</span><span class="sxs-lookup"><span data-stu-id="18e5e-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18e5e-105">Pokud používáte Visual Studio, můžete použít Návrháře relací objektů přizpůsobení vložení, aktualizace a odstranění akce.</span><span class="sxs-lookup"><span data-stu-id="18e5e-105">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="18e5e-106">Témata v této části popisuje techniky, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro přizpůsobení vkládání, čtení, aktualizace a odstranění operací ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="18e5e-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18e5e-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="18e5e-107">In This Section</span></span>  
 [<span data-ttu-id="18e5e-108">Přizpůsobení operací: Přehled</span><span class="sxs-lookup"><span data-stu-id="18e5e-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="18e5e-109">Popisuje různé postupy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro přizpůsobení vkládání, čtení, aktualizace a operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="18e5e-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="18e5e-110">Operace vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="18e5e-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="18e5e-111">Popisuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí procesy pro manipulaci dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="18e5e-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="18e5e-112">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="18e5e-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="18e5e-113">Popisuje role pro vývojáře v implementaci požadavků není vynucena [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18e5e-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="18e5e-114">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="18e5e-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="18e5e-115">Popisuje, jak používat částečné metody přepsání automaticky generované metody.</span><span class="sxs-lookup"><span data-stu-id="18e5e-115">Describes how to use partial methods to override autogenerated methods.</span></span>
