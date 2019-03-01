---
title: 'Postupy: Zápis uživatelských nastavení při běhu pomocíC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 264fa9706f9255d7324cad6d02c36cc424e28995
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981592"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="bdff0-102">Postupy: Zápis uživatelských nastavení při běhu pomocí C\#</span><span class="sxs-lookup"><span data-stu-id="bdff0-102">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="bdff0-103">Nastavení oboru aplikace jsou jen pro čtení a lze změnit pouze v době návrhu nebo úpravou souboru .config mezi jednotlivými relacemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdff0-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="bdff0-104">Nastavení, která jsou s rozsahem uživatele, ale může být napsán v době běhu stejně jako jakoukoli hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bdff0-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="bdff0-105">Nová hodnota se uchovávají po dobu trvání relace aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdff0-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="bdff0-106">Je možné zachovat změny nastavení mezi relacemi aplikace po zavolání metody uložit.</span><span class="sxs-lookup"><span data-stu-id="bdff0-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="bdff0-107">Postupy: Zápis a zachování uživatelského nastavení při běhu pomocí C\#</span><span class="sxs-lookup"><span data-stu-id="bdff0-107">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="bdff0-108">Přístup k nastavení a přiřaďte ji novou hodnotu, jak je znázorněno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="bdff0-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="bdff0-109">Pokud chcete, a zachová tak změny v nastavení mezi relacemi aplikace, zavolejte metodu uložit, jak je znázorněno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="bdff0-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="bdff0-110">Uživatelská nastavení jsou uloženy do souboru do podsložky složky místní skryté aplikace data uživatele.</span><span class="sxs-lookup"><span data-stu-id="bdff0-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdff0-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdff0-111">See also</span></span>

- [<span data-ttu-id="bdff0-112">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="bdff0-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="bdff0-113">Postupy: Čtení uživatelských nastavení při běhu pomocíC#</span><span class="sxs-lookup"><span data-stu-id="bdff0-113">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="bdff0-114">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="bdff0-114">Application Settings Overview</span></span>](application-settings-overview.md)
