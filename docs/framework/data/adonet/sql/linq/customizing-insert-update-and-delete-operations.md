---
title: Přizpůsobení operací vložení, aktualizace a odstranění
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: f75f4b4caf6b72076a83bde2f2c659aab4c9707d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912569"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="d563d-102">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="d563d-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="d563d-103">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL pro implementaci operací vložení, čtení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="d563d-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="d563d-104">V praxi ale obvykle vlastníte aplikaci tak, aby vyhovovala vašim obchodním potřebám.</span><span class="sxs-lookup"><span data-stu-id="d563d-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d563d-105">Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k přizpůsobení akcí vložení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="d563d-105">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="d563d-106">Tato část témat popisuje techniky, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umožňují přizpůsobení operací vložení, čtení, aktualizace a odstranění ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d563d-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d563d-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d563d-107">In This Section</span></span>  
 [<span data-ttu-id="d563d-108">Přizpůsobení operací: Přehled</span><span class="sxs-lookup"><span data-stu-id="d563d-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="d563d-109">V této části najdete [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] popis různých postupů pro přizpůsobení operací vložení, čtení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="d563d-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="d563d-110">Operace vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="d563d-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="d563d-111">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Popisuje výchozí procesy pro práci s daty databáze.</span><span class="sxs-lookup"><span data-stu-id="d563d-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="d563d-112">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="d563d-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="d563d-113">Popisuje roli vývojáře při implementaci požadavků, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nejsou vynutily.</span><span class="sxs-lookup"><span data-stu-id="d563d-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="d563d-114">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="d563d-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="d563d-115">Popisuje, jak použít částečné metody k přepsání automaticky generovaných metod.</span><span class="sxs-lookup"><span data-stu-id="d563d-115">Describes how to use partial methods to override autogenerated methods.</span></span>
