---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocí C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710230"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="65ca4-102">Postupy: Čtení nastavení za běhu pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="65ca4-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="65ca4-103">Pomocí objektu Properties lze v době běhu číst nastavení s rozsahem aplikace i uživatele s rozsahem.</span><span class="sxs-lookup"><span data-stu-id="65ca4-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="65ca4-104">Objekt Properties zpřístupňuje všechna výchozí nastavení pro projekt prostřednictvím vlastností. Settings. Default ve výchozím oboru názvů projektu, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="65ca4-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="65ca4-105">Čtení nastavení v době běhu pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="65ca4-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="65ca4-106">Přístup k příslušnému nastavení získáte prostřednictvím vlastnosti. Settings. default.</span><span class="sxs-lookup"><span data-stu-id="65ca4-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="65ca4-107">Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` k vlastnosti BackColor.</span><span class="sxs-lookup"><span data-stu-id="65ca4-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="65ca4-108">Vyžaduje, abyste předtím vytvořili soubor nastavení obsahující nastavení s názvem `myColor` typu. `System.Drawing.Color`</span><span class="sxs-lookup"><span data-stu-id="65ca4-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="65ca4-109">Informace o vytvoření souboru nastavení naleznete v tématu [How to: Vytvořte nové nastavení v době](how-to-create-a-new-setting-at-design-time.md)návrhu.</span><span class="sxs-lookup"><span data-stu-id="65ca4-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="65ca4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65ca4-110">See also</span></span>

- [<span data-ttu-id="65ca4-111">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="65ca4-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="65ca4-112">Postupy: Zápis uživatelských nastavení v době běhu pomocíC#</span><span class="sxs-lookup"><span data-stu-id="65ca4-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="65ca4-113">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="65ca4-113">Application Settings Overview</span></span>](application-settings-overview.md)
