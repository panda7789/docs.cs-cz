---
title: Přizpůsobení operací vložení, aktualizace a odstranění
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: b4578a030300872bf4e0bab30b8daf12544be0cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032766"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="8885a-102">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="8885a-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="8885a-103">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL implementovat vložit, číst, aktualizovat a odstraňovat operace.</span><span class="sxs-lookup"><span data-stu-id="8885a-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="8885a-104">V praxi však obvykle přizpůsobíte aplikaci tak, aby vyhovovala vašim obchodním potřebám.</span><span class="sxs-lookup"><span data-stu-id="8885a-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8885a-105">Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] přizpůsobení vložit, aktualizovat a odstranit některé akce.</span><span class="sxs-lookup"><span data-stu-id="8885a-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="8885a-106">Témata v této části popisuje techniky, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro přizpůsobení vkládání, čtení, aktualizace a odstranění operací ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8885a-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8885a-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8885a-107">In This Section</span></span>  
 [<span data-ttu-id="8885a-108">Přizpůsobení operací: Přehled</span><span class="sxs-lookup"><span data-stu-id="8885a-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="8885a-109">Popisuje různé postupy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro přizpůsobení vkládání, čtení, aktualizace a operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="8885a-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="8885a-110">Operace vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="8885a-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="8885a-111">Popisuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí procesy pro manipulaci dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="8885a-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="8885a-112">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="8885a-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="8885a-113">Popisuje role pro vývojáře v implementaci požadavků není vynucena [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8885a-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="8885a-114">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="8885a-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="8885a-115">Popisuje, jak používat částečné metody přepsání automaticky generované metody.</span><span class="sxs-lookup"><span data-stu-id="8885a-115">Describes how to use partial methods to override autogenerated methods.</span></span>
