---
title: "Postupy: Čtení uživatelských nastavení při běhu pomocí C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c23fd88d33ff4ca480c435f2058f4c568320578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="5cb79-102">Postupy: Čtení uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="5cb79-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="5cb79-103">Nastavení brány obor aplikace a nastavení uživatele si můžete přečíst v době běhu prostřednictvím vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="5cb79-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="5cb79-104">Objekt vlastností zpřístupní všechna výchozí nastavení pro projekt prostřednictvím Properties.Settings.Default člena.</span><span class="sxs-lookup"><span data-stu-id="5cb79-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="5cb79-105">Číst nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="5cb79-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="5cb79-106">Přístup k příslušné nastavení prostřednictvím Properties.Settings.Default člena.</span><span class="sxs-lookup"><span data-stu-id="5cb79-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="5cb79-107">Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` na vlastnost Barva pozadí.</span><span class="sxs-lookup"><span data-stu-id="5cb79-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="5cb79-108">Vyžaduje, abyste vytvořili nastavení souboru, který obsahuje nastavení s názvem `myColor` typu `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="5cb79-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="5cb79-109">Informace o vytvoření souboru nastavení najdete v tématu [postupy: vytvoření nového nastavení v době návrhu](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="5cb79-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5cb79-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cb79-110">See Also</span></span>  
 [<span data-ttu-id="5cb79-111">Použití nastavení aplikace a nastavení uživatele</span><span class="sxs-lookup"><span data-stu-id="5cb79-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="5cb79-112">Postupy: Zápis uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="5cb79-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="5cb79-113">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="5cb79-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
