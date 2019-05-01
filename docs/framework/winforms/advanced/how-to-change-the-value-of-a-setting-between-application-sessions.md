---
title: 'Postupy: Změna hodnoty nastavení mezi relacemi aplikace'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 95e613cb280813cd75d887d3cf147d7c897bc2e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004429"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="a0a5c-102">Postupy: Změna hodnoty nastavení mezi relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="a0a5c-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="a0a5c-103">V některých případech můžete chtít změnit hodnoty nastavení mezi relacemi aplikace poté, co byl zkompilován a nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0a5c-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="a0a5c-104">Například můžete chtít změnit připojovací řetězec tak, aby odkazoval na správnou databázi umístění.</span><span class="sxs-lookup"><span data-stu-id="a0a5c-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="a0a5c-105">Protože návrhových nástrojů nejsou k dispozici, poté, co byl zkompilován a nasazení aplikace, musíte změnit hodnotu nastavení v souboru ručně.</span><span class="sxs-lookup"><span data-stu-id="a0a5c-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="a0a5c-106">Chcete-li změnit hodnoty nastavení mezi relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="a0a5c-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1. <span data-ttu-id="a0a5c-107">Pomocí Microsoft Notepad nebo některé jiné text nebo editoru XML otevřete soubor .config přidruženého k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a0a5c-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2. <span data-ttu-id="a0a5c-108">Vyhledejte položku pro nastavení, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="a0a5c-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="a0a5c-109">By měl vypadat podobně jako v příkladu níže uvedené.</span><span class="sxs-lookup"><span data-stu-id="a0a5c-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3. <span data-ttu-id="a0a5c-110">Zadejte novou hodnotu pro nastavení a soubor uložte.</span><span class="sxs-lookup"><span data-stu-id="a0a5c-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a5c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0a5c-111">See also</span></span>

- [<span data-ttu-id="a0a5c-112">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="a0a5c-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="a0a5c-113">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="a0a5c-113">Application Settings Overview</span></span>](application-settings-overview.md)
