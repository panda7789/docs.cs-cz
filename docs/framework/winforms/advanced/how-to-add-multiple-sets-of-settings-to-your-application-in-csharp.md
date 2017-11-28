---
title: "Postupy: Přidání více množin nastavení do vaší aplikace v C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec541a8f83990eec79226be7fb4880ef8dda639d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="590bf-102">Postupy: Přidání více množin nastavení do vaší aplikace v C#</span><span class="sxs-lookup"><span data-stu-id="590bf-102">How To: Add Multiple Sets of Settings To Your Application in C#</span></span> #
<span data-ttu-id="590bf-103">V některých případech můžete chtít mít více sad nastavení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="590bf-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="590bf-104">Například pokud vyvíjíte aplikace kde je očekávána určité skupiny nastavení, chcete-li změnit často, může být vhodné k oddělení všechny do jednoho souboru tak, aby soubor můžete nahradit velkoobchodních, a další nastavení neovlivní.</span><span class="sxs-lookup"><span data-stu-id="590bf-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="590bf-105">Visual Studio můžete k přidání více množin nastavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="590bf-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="590bf-106">Další sad nastavení je možné přistupovat prostřednictvím objektu Properties.Settings.</span><span class="sxs-lookup"><span data-stu-id="590bf-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="590bf-107">Chcete-li přidat další sadu nastavení do vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="590bf-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="590bf-108">Z **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="590bf-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="590bf-109">**Přidat novou položku** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="590bf-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="590bf-110">V **přidat novou položku** dialogové okno, vyberte **soubor nastavení**, zadejte název souboru a klikněte na tlačítko **přidat** přidat nový soubor nastavení vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="590bf-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="590bf-111">V **Průzkumníku řešení**, přetáhněte ji do nový soubor s nastaveními **vlastnosti** složky.</span><span class="sxs-lookup"><span data-stu-id="590bf-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="590bf-112">To umožňuje nové nastavení k dispozici v kódu.</span><span class="sxs-lookup"><span data-stu-id="590bf-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="590bf-113">Přidat a používat nastavení v tomto souboru, stejně jako jakýkoli jiný soubor nastavení.</span><span class="sxs-lookup"><span data-stu-id="590bf-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="590bf-114">Tato skupina nastavení prostřednictvím objektu Properties.Settings můžete přistupovat.</span><span class="sxs-lookup"><span data-stu-id="590bf-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590bf-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="590bf-115">See Also</span></span>  
 [<span data-ttu-id="590bf-116">Použití nastavení aplikace a nastavení uživatele</span><span class="sxs-lookup"><span data-stu-id="590bf-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="590bf-117">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="590bf-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
