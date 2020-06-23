---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocí C#'
description: Přečtěte si, jak číst nastavení s rozsahem aplikace i s uživatelským rozsahem v době běhu v jazyce C# prostřednictvím objektu Properties.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903348"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="780f5-103">Postupy: čtení nastavení v době běhu pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="780f5-103">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="780f5-104">Pomocí objektu Properties lze v době běhu číst nastavení s rozsahem aplikace i uživatele s rozsahem.</span><span class="sxs-lookup"><span data-stu-id="780f5-104">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="780f5-105">Objekt Properties zpřístupňuje všechna výchozí nastavení pro projekt prostřednictvím vlastností. Settings. Default ve výchozím oboru názvů projektu, ve kterém jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="780f5-105">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="780f5-106">Čtení nastavení v době běhu pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="780f5-106">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="780f5-107">Přístup k příslušnému nastavení získáte prostřednictvím vlastnosti. Settings. default.</span><span class="sxs-lookup"><span data-stu-id="780f5-107">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="780f5-108">Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` k vlastnosti BackColor.</span><span class="sxs-lookup"><span data-stu-id="780f5-108">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="780f5-109">Vyžaduje, abyste předtím vytvořili soubor nastavení obsahující nastavení s názvem `myColor` typu `System.Drawing.Color` .</span><span class="sxs-lookup"><span data-stu-id="780f5-109">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="780f5-110">Informace o vytvoření souboru nastavení najdete v tématu [Postup: vytvoření nového nastavení v době návrhu](how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="780f5-110">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="780f5-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="780f5-111">See also</span></span>

- [<span data-ttu-id="780f5-112">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="780f5-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="780f5-113">Postupy: Zápis uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="780f5-113">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="780f5-114">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="780f5-114">Application Settings Overview</span></span>](application-settings-overview.md)
