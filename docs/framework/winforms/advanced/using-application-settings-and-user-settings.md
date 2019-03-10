---
title: Použití nastavení aplikace a uživatelských nastavení
ms.date: 03/30/2017
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: 8b1fa01d39e4a010ce5fd0d686fba41fae6536ad
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711249"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="b4f92-102">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="b4f92-102">Using Application Settings and User Settings</span></span>
<span data-ttu-id="b4f92-103">Od verze rozhraní .NET Framework 2.0, můžete vytvořit a přistupovat k hodnotám, které jsou trvalé mezi jednotlivými relacemi spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4f92-103">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="b4f92-104">Tyto hodnoty jsou označovány jako *nastavení*.</span><span class="sxs-lookup"><span data-stu-id="b4f92-104">These values are called *settings*.</span></span> <span data-ttu-id="b4f92-105">Nastavení může představovat předvolby uživatele nebo cenné informace aplikace je potřeba použít.</span><span class="sxs-lookup"><span data-stu-id="b4f92-105">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="b4f92-106">Můžete vytvořit řadu nastavení, které ukládají uživatelské předvolby pro barevné schéma aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4f92-106">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="b4f92-107">Nebo může uložit připojovací řetězec, který určuje databázi, která vaše aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="b4f92-107">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="b4f92-108">Nastavení povolit, že jste k oběma zachovat informace, které jsou důležité pro aplikaci mimo kód a vytvářet profily, které ukládají požadavků jednotlivých uživatelů.</span><span class="sxs-lookup"><span data-stu-id="b4f92-108">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="b4f92-109">Témata v této části popisují způsob použití nastavení v době návrhu a běhu.</span><span class="sxs-lookup"><span data-stu-id="b4f92-109">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4f92-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b4f92-110">In This Section</span></span>  
 [<span data-ttu-id="b4f92-111">Postupy: Vytvořit nové nastavení v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b4f92-111">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="b4f92-112">Vysvětluje, jak vytvořit nové nastavení pro aplikaci pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4f92-112">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="b4f92-113">Postupy: Změna hodnoty existujícího nastavení při návrhu</span><span class="sxs-lookup"><span data-stu-id="b4f92-113">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="b4f92-114">Popisuje, jak pomocí sady Visual Studio ke změně hodnoty existujícího nastavení.</span><span class="sxs-lookup"><span data-stu-id="b4f92-114">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="b4f92-115">Postupy: Změna hodnoty nastavení mezi relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="b4f92-115">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="b4f92-116">Podrobné informace o tom, jak změnit hodnoty nastavení v kompilované aplikace mezi jednotlivými relacemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4f92-116">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="b4f92-117">Postupy: Čtení uživatelských nastavení při běhu pomocíC#</span><span class="sxs-lookup"><span data-stu-id="b4f92-117">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="b4f92-118">Popisuje, jak použít kód pro čtení nastavení s C#.</span><span class="sxs-lookup"><span data-stu-id="b4f92-118">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="b4f92-119">Postupy: Zápis uživatelských nastavení při běhu pomocíC#</span><span class="sxs-lookup"><span data-stu-id="b4f92-119">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="b4f92-120">Vysvětluje, jak použít kód pro zápis a uložte příslušné hodnoty uživatelským nastavením u C#.</span><span class="sxs-lookup"><span data-stu-id="b4f92-120">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="b4f92-121">Postupy: Přidání více množin nastavení do vaší aplikace vC#</span><span class="sxs-lookup"><span data-stu-id="b4f92-121">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="b4f92-122">Podrobnosti o přidání více množin nastavení do aplikace s C#.</span><span class="sxs-lookup"><span data-stu-id="b4f92-122">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f92-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4f92-123">See also</span></span>
- [<span data-ttu-id="b4f92-124">Nastavení aplikace pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4f92-124">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
