---
title: Přizpůsobení vložit, aktualizovat a odstraňovat operací
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 410385d1689a9fd15a1399411f601e407d590830
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="84d96-102">Přizpůsobení vložit, aktualizovat a odstraňovat operací</span><span class="sxs-lookup"><span data-stu-id="84d96-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="84d96-103">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamické SQL implementovat vložení, číst, aktualizovat a operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="84d96-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="84d96-104">V praxi však obvykle přizpůsobit tak, aby vyhovovala vašim obchodním potřebám vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="84d96-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84d96-105">Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Pokud chcete přizpůsobit vložení, aktualizace a odstranění akcí.</span><span class="sxs-lookup"><span data-stu-id="84d96-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="84d96-106">Témata v této části popisuje techniky, které [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro přizpůsobení vložení, čtení, aktualizace a operace odstranění ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="84d96-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84d96-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="84d96-107">In This Section</span></span>  
 [<span data-ttu-id="84d96-108">Přizpůsobení operací: Přehled</span><span class="sxs-lookup"><span data-stu-id="84d96-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="84d96-109">Popisuje různé postupy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje pro přizpůsobení vložení, čtení, aktualizaci a operace odstranění.</span><span class="sxs-lookup"><span data-stu-id="84d96-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="84d96-110">Operace vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="84d96-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="84d96-111">Popisuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí procesy pro manipulaci s dat databáze.</span><span class="sxs-lookup"><span data-stu-id="84d96-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="84d96-112">Odpovědnosti vývojáře při přepisu výchozího chování</span><span class="sxs-lookup"><span data-stu-id="84d96-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="84d96-113">Popisuje roli vývojáře v implementaci požadavků není vynucováno [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84d96-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="84d96-114">Přidání obchodní logiky pomocí částečných metod</span><span class="sxs-lookup"><span data-stu-id="84d96-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="84d96-115">Popisuje, jak použít částečný metody přepsat automaticky vygenerovanou metody.</span><span class="sxs-lookup"><span data-stu-id="84d96-115">Describes how to use partial methods to override autogenerated methods.</span></span>
