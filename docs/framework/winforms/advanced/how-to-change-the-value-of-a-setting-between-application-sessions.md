---
title: 'Postupy: Změna hodnoty nastavení mezi relacemi aplikace'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 383f72f223fb92170d16a9538c94e67825009abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523407"
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="d0629-102">Postupy: Změna hodnoty nastavení mezi relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="d0629-102">How To: Change the Value of a Setting Between Application Sessions</span></span>
<span data-ttu-id="d0629-103">V některých případech můžete chtít změnit hodnoty nastavení mezi relacemi aplikace po aplikaci byl zkompilován a nasazení.</span><span class="sxs-lookup"><span data-stu-id="d0629-103">At times, you might want to change the value of a setting between application sessions after the application has been compiled and deployed.</span></span> <span data-ttu-id="d0629-104">Můžete například změnit připojovací řetězec tak, aby odkazovaly na správné databázi umístění.</span><span class="sxs-lookup"><span data-stu-id="d0629-104">For example, you might want to change a connection string to point to the correct database location.</span></span> <span data-ttu-id="d0629-105">Vzhledem k tomu, že nástrojů návrhu nejsou k dispozici po aplikaci byl zkompilován a nasazení, je nutné změnit hodnotu nastavení ručně v souboru.</span><span class="sxs-lookup"><span data-stu-id="d0629-105">Since design-time tools are not available after the application has been compiled and deployed, you must change the setting value manually in the file.</span></span>  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a><span data-ttu-id="d0629-106">Chcete-li změnit hodnoty nastavení mezi relacemi aplikace</span><span class="sxs-lookup"><span data-stu-id="d0629-106">To Change the Value of a Setting Between Application Sessions</span></span>  
  
1.  <span data-ttu-id="d0629-107">Pomocí Microsoft Notepad nebo některé další text nebo editoru XML, otevřete soubor .config související s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="d0629-107">Using Microsoft Notepad or some other text or XML editor, open the .config file associated with your application.</span></span>  
  
2.  <span data-ttu-id="d0629-108">Vyhledejte položku s nastavením, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="d0629-108">Locate the entry for the setting you want to change.</span></span> <span data-ttu-id="d0629-109">By měla vypadat podobně jako v příkladu níže uvedené.</span><span class="sxs-lookup"><span data-stu-id="d0629-109">It should look similar to the example presented below.</span></span>  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  <span data-ttu-id="d0629-110">Zadejte novou hodnotu pro vaše nastavení a uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="d0629-110">Type a new value for your setting and save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0629-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0629-111">See Also</span></span>  
 [<span data-ttu-id="d0629-112">Použití nastavení aplikace a uživatelských nastavení</span><span class="sxs-lookup"><span data-stu-id="d0629-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="d0629-113">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="d0629-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
