---
title: Použití nastavení aplikace a uživatelských nastavení
ms.date: 03/30/2017
description: Naučte se používat nastavení aplikace a uživatelská nastavení k vytváření a přístup k hodnotám, které jsou trvalé mezi relacemi spuštění aplikace.
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: a30fd354986265eca002fce57bccf5b3bb2adc15
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903165"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="a4012-103">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="a4012-103">Using Application Settings and User Settings</span></span>
<span data-ttu-id="a4012-104">Počínaje .NET Framework 2,0 můžete vytvořit a přistupovat k hodnotám, které jsou trvalé mezi relacemi spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4012-104">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="a4012-105">Tyto hodnoty se nazývají *Nastavení*.</span><span class="sxs-lookup"><span data-stu-id="a4012-105">These values are called *settings*.</span></span> <span data-ttu-id="a4012-106">Nastavení může představovat uživatelské preference nebo cenné informace, které aplikace potřebuje použít.</span><span class="sxs-lookup"><span data-stu-id="a4012-106">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="a4012-107">Můžete například vytvořit řadu nastavení, která ukládají předvolby uživatele pro barevné schéma aplikace.</span><span class="sxs-lookup"><span data-stu-id="a4012-107">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="a4012-108">Případně můžete uložit připojovací řetězec, který určuje databázi, kterou vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="a4012-108">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="a4012-109">Nastavení umožňují uchovat informace, které jsou pro aplikaci mimo kód kritické, a vytvářet profily, které ukládají předvolby jednotlivých uživatelů.</span><span class="sxs-lookup"><span data-stu-id="a4012-109">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="a4012-110">Témata v této části popisují, jak používat nastavení v době návrhu a v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a4012-110">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4012-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a4012-111">In This Section</span></span>  
 [<span data-ttu-id="a4012-112">Postupy: Vytvoření nového nastavení při návrhu</span><span class="sxs-lookup"><span data-stu-id="a4012-112">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="a4012-113">Vysvětluje, jak pomocí sady Visual Studio vytvořit nové nastavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a4012-113">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="a4012-114">Postupy: Změna hodnoty existujícího nastavení při návrhu</span><span class="sxs-lookup"><span data-stu-id="a4012-114">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="a4012-115">Popisuje, jak pomocí sady Visual Studio změnit hodnotu existujícího nastavení.</span><span class="sxs-lookup"><span data-stu-id="a4012-115">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="a4012-116">Postupy: Změna hodnoty nastavení mezi relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="a4012-116">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="a4012-117">Podrobnosti o tom, jak změnit hodnotu nastavení v kompilované aplikaci mezi aplikačními relacemi.</span><span class="sxs-lookup"><span data-stu-id="a4012-117">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="a4012-118">Postupy: Čtení uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="a4012-118">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="a4012-119">Popisuje způsob použití kódu ke čtení nastavení pomocí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="a4012-119">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="a4012-120">Postupy: Zápis uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="a4012-120">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="a4012-121">Vysvětluje, jak použít kód pro zápis a uložení hodnot uživatelských nastavení pomocí C#.</span><span class="sxs-lookup"><span data-stu-id="a4012-121">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="a4012-122">Postupy: Přidání více množin nastavení do vaší aplikace v C#</span><span class="sxs-lookup"><span data-stu-id="a4012-122">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="a4012-123">Podrobně popisuje, jak přidat více sad nastavení do aplikace pomocí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="a4012-123">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4012-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4012-124">See also</span></span>

- [<span data-ttu-id="a4012-125">Nastavení aplikace pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4012-125">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
