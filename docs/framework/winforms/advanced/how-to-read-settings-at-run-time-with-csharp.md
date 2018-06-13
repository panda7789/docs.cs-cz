---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocí C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8259e2f429718793c01868855651d1000620fae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521011"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="634e4-102">Postupy: Čtení uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="634e4-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="634e4-103">Nastavení brány obor aplikace a nastavení uživatele si můžete přečíst v době běhu prostřednictvím vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="634e4-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="634e4-104">Objekt vlastností zpřístupní všechna výchozí nastavení pro projekt prostřednictvím Properties.Settings.Default člena.</span><span class="sxs-lookup"><span data-stu-id="634e4-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="634e4-105">Číst nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="634e4-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="634e4-106">Přístup k příslušné nastavení prostřednictvím Properties.Settings.Default člena.</span><span class="sxs-lookup"><span data-stu-id="634e4-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="634e4-107">Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` na vlastnost Barva pozadí.</span><span class="sxs-lookup"><span data-stu-id="634e4-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="634e4-108">Vyžaduje, abyste vytvořili nastavení souboru, který obsahuje nastavení s názvem `myColor` typu `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="634e4-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="634e4-109">Informace o vytvoření souboru nastavení najdete v tématu [postupy: vytvoření nového nastavení v době návrhu](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="634e4-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="634e4-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="634e4-110">See Also</span></span>  
 [<span data-ttu-id="634e4-111">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="634e4-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="634e4-112">Postupy: Zápis uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="634e4-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="634e4-113">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="634e4-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
