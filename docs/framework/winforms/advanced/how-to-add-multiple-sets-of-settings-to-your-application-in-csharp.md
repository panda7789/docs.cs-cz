---
title: 'Postupy: Přidání více množin nastavení do vaší aplikace vC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 43402d8a1b0b1ca26e656be1424a5fa341ac4728
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719647"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="e3ad8-102">Postupy: Přidání více množin nastavení do vaší aplikace v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="e3ad8-102">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>
<span data-ttu-id="e3ad8-103">V některých případech můžete chtít mít více množin nastavení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="e3ad8-104">Například pokud vyvíjíte aplikaci kde se očekává často měnit konkrétní skupinu nastavení, může být vhodné oddělit vše do jediného souboru tak, aby soubor se dá nahradit velkoobchodních, ostatní nechat to neovlivní.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="e3ad8-105">Visual Studio umožňuje přidání více množin nastavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="e3ad8-106">Další sadu nastavení je možný prostřednictvím Properties.Settings objektu.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="e3ad8-107">Chcete-li přidat další sadu nastavení do vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="e3ad8-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="e3ad8-108">Z **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="e3ad8-109">**Přidat novou položku** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="e3ad8-110">V **přidat novou položku** dialogu **souboru s nastavením**, zadejte název souboru a klikněte na tlačítko **přidat** přidáte nový soubor nastavení do vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="e3ad8-111">V **Průzkumníka řešení**, přetáhněte nový soubor nastavení do **vlastnosti** složky.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="e3ad8-112">To umožňuje nové nastavení k dispozici v kódu.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="e3ad8-113">Přidat a používat nastavení v tomto souboru, stejně jako jakýkoli jiný soubor nastavení.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="e3ad8-114">Tato skupina nastavení prostřednictvím objektu Properties.Settings můžete přistupovat.</span><span class="sxs-lookup"><span data-stu-id="e3ad8-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ad8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3ad8-115">See also</span></span>
- [<span data-ttu-id="e3ad8-116">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="e3ad8-116">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="e3ad8-117">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="e3ad8-117">Application Settings Overview</span></span>](application-settings-overview.md)
