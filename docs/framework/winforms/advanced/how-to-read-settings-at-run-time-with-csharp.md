---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocí C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966904"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="238c1-102">Postupy: Čtení uživatelských nastavení při běhu pomocí C\#</span><span class="sxs-lookup"><span data-stu-id="238c1-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="238c1-103">Nastavení oboru aplikace i s rozsahem uživatele si můžete přečíst v době běhu pomocí objektu vlastností.</span><span class="sxs-lookup"><span data-stu-id="238c1-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="238c1-104">Objekt vlastností zpřístupní všechna výchozí nastavení projektu prostřednictvím Properties.Settings.Default člena.</span><span class="sxs-lookup"><span data-stu-id="238c1-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="238c1-105">Chcete-li čtení uživatelských nastavení při běhu pomocí C\#</span><span class="sxs-lookup"><span data-stu-id="238c1-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="238c1-106">Přístup k příslušné nastavení prostřednictvím Properties.Settings.Default člena.</span><span class="sxs-lookup"><span data-stu-id="238c1-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="238c1-107">Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` vlastnosti BackColor.</span><span class="sxs-lookup"><span data-stu-id="238c1-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="238c1-108">Vyžaduje, abyste vytvořili soubor nastavení obsahující nastavení s názvem `myColor` typu `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="238c1-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="238c1-109">Informace o vytvoření souboru nastavení najdete v tématu [How To: Vytvoření nového nastavení při návrhu](how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="238c1-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="238c1-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="238c1-110">See also</span></span>

- [<span data-ttu-id="238c1-111">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="238c1-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="238c1-112">Postupy: Zápis uživatelských nastavení při běhu pomocíC#</span><span class="sxs-lookup"><span data-stu-id="238c1-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="238c1-113">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="238c1-113">Application Settings Overview</span></span>](application-settings-overview.md)
