---
title: Přizpůsobení vložit, aktualizovat a odstraňovat operací
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: b4578a030300872bf4e0bab30b8daf12544be0cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361637"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="c0189-102">Přizpůsobení vložit, aktualizovat a odstraňovat operací</span><span class="sxs-lookup"><span data-stu-id="c0189-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="c0189-103">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL implementovat vložení, číst, aktualizovat a operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="c0189-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="c0189-104">V praxi však obvykle přizpůsobit tak, aby vyhovovala vašim obchodním potřebám vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0189-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0189-105">Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Pokud chcete přizpůsobit vložení, aktualizace a odstranění akcí.</span><span class="sxs-lookup"><span data-stu-id="c0189-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="c0189-106">Témata v této části popisuje techniky, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro přizpůsobení vložení, čtení, aktualizace a operace odstranění ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c0189-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0189-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c0189-107">In This Section</span></span>  
 [<span data-ttu-id="c0189-108">Přizpůsobení operací: Přehled</span><span class="sxs-lookup"><span data-stu-id="c0189-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="c0189-109">Popisuje různé postupy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro přizpůsobení vložení, čtení, aktualizaci a operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="c0189-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="c0189-110">Operace vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="c0189-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="c0189-111">Popisuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí procesy pro manipulaci s dat databáze.</span><span class="sxs-lookup"><span data-stu-id="c0189-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="c0189-112">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="c0189-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="c0189-113">Popisuje roli vývojáře v implementaci požadavků není vynucováno [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0189-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="c0189-114">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="c0189-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="c0189-115">Popisuje, jak použít částečný metody přepsat automaticky vygenerovanou metody.</span><span class="sxs-lookup"><span data-stu-id="c0189-115">Describes how to use partial methods to override autogenerated methods.</span></span>
