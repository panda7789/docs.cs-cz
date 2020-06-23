---
title: 'Postupy: Zápis uživatelských nastavení při běhu pomocí C#'
description: Naučte se, jak psát nastavení v době běhu v jazyce C# tím, že se změny nastavení mezi relacemi aplikací zachovají zavoláním metody Save.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904322"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="d1b64-103">Postupy: zápis uživatelských nastavení v době běhu pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="d1b64-103">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="d1b64-104">Nastavení, která jsou v oboru aplikace, jsou jen pro čtení a lze je změnit pouze v době návrhu nebo změnou souboru. config v mezi relacemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="d1b64-104">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="d1b64-105">Nastavení, která jsou v uživatelském rozsahu, však lze zapsat v době běhu stejně, jako byste změnili jakoukoli hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d1b64-105">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="d1b64-106">Nová hodnota zůstává po dobu trvání relace aplikace.</span><span class="sxs-lookup"><span data-stu-id="d1b64-106">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="d1b64-107">Změny nastavení mezi relacemi aplikace můžete zachovat voláním metody Save.</span><span class="sxs-lookup"><span data-stu-id="d1b64-107">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="d1b64-108">Postupy: zápis a zachování uživatelských nastavení za běhu pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="d1b64-108">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="d1b64-109">Nastavte přístup k nastavení a přiřaďte mu novou hodnotu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d1b64-109">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="d1b64-110">Chcete-li zachovat změny nastavení mezi relacemi aplikace, zavolejte metodu Save, jak je znázorněno v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="d1b64-110">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="d1b64-111">Uživatelská nastavení se ukládají do souboru v podsložce složky místní skrytá data aplikace daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="d1b64-111">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b64-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1b64-112">See also</span></span>

- [<span data-ttu-id="d1b64-113">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="d1b64-113">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="d1b64-114">Postupy: Čtení uživatelských nastavení při běhu pomocí C#</span><span class="sxs-lookup"><span data-stu-id="d1b64-114">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="d1b64-115">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="d1b64-115">Application Settings Overview</span></span>](application-settings-overview.md)
