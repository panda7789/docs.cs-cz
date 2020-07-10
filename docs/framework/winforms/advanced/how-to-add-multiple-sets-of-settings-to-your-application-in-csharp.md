---
title: 'Postupy: Přidání více množin nastavení do vaší aplikace v C#'
description: Naučte se, jak do aplikace v jazyce C# přidat více sad model Windows Forms nastavení pomocí sady Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173442"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="2ff8f-103">Postupy: Přidání více sad nastavení do aplikace v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="2ff8f-103">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="2ff8f-104">V některých případech možná budete chtít mít v aplikaci více sad nastavení.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-104">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="2ff8f-105">Například při vývoji aplikace, kde se očekává, že se určitá skupina nastavení často mění, může být vhodné je rozdělit do jediného souboru, aby bylo možné tento soubor nahradit, takže ostatní nastavení neovlivní.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-105">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="2ff8f-106">Sada Visual Studio umožňuje přidat do projektu více sad nastavení.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-106">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="2ff8f-107">K dalším sadám nastavení lze přistupovat prostřednictvím `Properties.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-107">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="2ff8f-108">Přidat další sadu nastavení</span><span class="sxs-lookup"><span data-stu-id="2ff8f-108">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="2ff8f-109">V aplikaci Visual Studio v nabídce **projekt** vyberte možnost **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-109">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="2ff8f-110">Otevře se dialogové okno **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="2ff8f-110">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="2ff8f-111">V dialogovém okně **Přidat novou položku** vyberte možnost **soubor nastavení**, zadejte název souboru a kliknutím na tlačítko **Přidat** přidejte nový soubor nastavení do řešení.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-111">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="2ff8f-112">V **Průzkumník řešení**přetáhněte nový soubor nastavení do složky Properties ( **vlastnosti** ).</span><span class="sxs-lookup"><span data-stu-id="2ff8f-112">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="2ff8f-113">To umožňuje, aby vaše nová nastavení byla k dispozici v kódu.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-113">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="2ff8f-114">V tomto souboru můžete přidat a použít nastavení stejným způsobem jako jakýkoli jiný soubor nastavení.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-114">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="2ff8f-115">K této skupině nastavení můžete přistupovat prostřednictvím `Properties.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="2ff8f-115">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ff8f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ff8f-116">See also</span></span>

- [<span data-ttu-id="2ff8f-117">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="2ff8f-117">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="2ff8f-118">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="2ff8f-118">Application Settings Overview</span></span>](application-settings-overview.md)
