---
title: 'Postupy: Zápis uživatelských nastavení při běhu pomocí C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: f289b6a6a4a726ffa6bb2c9df99c665e2872e8d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522292"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="c3cd2-102">Postupy: Zápis uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="c3cd2-102">How To: Write User Settings at Run Time with C#</span></span> #
<span data-ttu-id="c3cd2-103">Nastavení, které jsou s rozsahem aplikace jsou jen pro čtení a lze změnit pouze v době návrhu nebo změnou souboru .config mezi relacemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="c3cd2-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="c3cd2-104">Nastavení, které jsou zaměřené na uživatele, ale může být napsán v době běhu stejně, jako by měnit všechny hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3cd2-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="c3cd2-105">Nová hodnota trvá po dobu trvání relace aplikace.</span><span class="sxs-lookup"><span data-stu-id="c3cd2-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="c3cd2-106">Můžete zachovat změny nastavení mezi relacemi aplikace pomocí volání metody uložit.</span><span class="sxs-lookup"><span data-stu-id="c3cd2-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="c3cd2-107">Postupy: Zápis a zachovaly uživatelská nastavení v době běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="c3cd2-107">How To: Write and Persist User Settings at Run Time with C#</span></span>  
  
1.  <span data-ttu-id="c3cd2-108">Přístup k nastavení a přiřaďte ho novou hodnotu, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c3cd2-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  <span data-ttu-id="c3cd2-109">Pokud chcete zachovat změny nastavení mezi relacemi aplikace, zavolejte metodu uložit, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c3cd2-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     <span data-ttu-id="c3cd2-110">Uživatelská nastavení se ukládají do souboru v rámci podsložkou složky data místní skrytá aplikace uživatele.</span><span class="sxs-lookup"><span data-stu-id="c3cd2-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3cd2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3cd2-111">See Also</span></span>  
 [<span data-ttu-id="c3cd2-112">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="c3cd2-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="c3cd2-113">Postupy: Čtení uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="c3cd2-113">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="c3cd2-114">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="c3cd2-114">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
