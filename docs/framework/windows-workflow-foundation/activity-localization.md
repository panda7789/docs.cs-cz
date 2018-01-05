---
title: Lokalizace aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccabcda9e26751db80ee7e955458d0eee0cae7e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="activity-localization"></a><span data-ttu-id="7077a-102">Lokalizace aktivity</span><span class="sxs-lookup"><span data-stu-id="7077a-102">Activity Localization</span></span>
<span data-ttu-id="7077a-103">Pokud pracovní postup aplikace a součásti potenciální lokalizovat do jiných jazykové verze a jazyky, řetězce prostředků je třeba použít tak, aby mohly být lokalizovány bez nutnosti rekompilace.</span><span class="sxs-lookup"><span data-stu-id="7077a-103">When workflow applications and components have the potential to be localized into other cultures and languages, resource strings should be used so that they can be localized without recompiling.</span></span>  
  
## <a name="activity-localization"></a><span data-ttu-id="7077a-104">Lokalizace aktivity</span><span class="sxs-lookup"><span data-stu-id="7077a-104">Activity Localization</span></span>  
 <span data-ttu-id="7077a-105">Jako u všech aplikací, které musí být lokalizovaný (vydané v různých verzích pro různé jazyky a kultur), všechny řetězce, které se zobrazí uživateli by neměl být put přímo v kódu, ale spíš uložené v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="7077a-105">As with all applications that must be localized (released in different versions for different languages and cultures), any strings that are displayed to the user should not be put directly in code, but rather stored in a resource file.</span></span> <span data-ttu-id="7077a-106">Řetězce lze přistupovat prostřednictvím <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span><span class="sxs-lookup"><span data-stu-id="7077a-106">The strings can then be accessed through <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span></span> <span data-ttu-id="7077a-107">Pokud vyvíjíte komponenty, která se distribuuje v několika jazycích, chcete taky použít řetězce prostředků pro aktivity ověřovacích zpráv, uživatelem definované sledování dat trasování zprávy a také chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="7077a-107">If you are developing a component that is distributed in several languages, you also want to use resource strings for activity validation messages, user-defined tracking data, tracing messages, and error messages as well.</span></span>  
  
 <span data-ttu-id="7077a-108">Následujícím cvičení ukazuje, jak pomocí zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="7077a-108">The following exercise demonstrates how to use a resource file.</span></span>  
  
#### <a name="using-resource-files-for-localized-strings"></a><span data-ttu-id="7077a-109">Použití zdrojových souborů pro lokalizované řetězce</span><span class="sxs-lookup"><span data-stu-id="7077a-109">Using resource files for localized strings</span></span>  
  
1.  <span data-ttu-id="7077a-110">V [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **přidat...** , **Novou položku...** .</span><span class="sxs-lookup"><span data-stu-id="7077a-110">In [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], right-click your project in **Solution Explorer** and select **Add…**, **New Item…**.</span></span>  
  
2.  <span data-ttu-id="7077a-111">Vyberte **souboru prostředků** a název souboru ErrorResources.resx.</span><span class="sxs-lookup"><span data-stu-id="7077a-111">Select **Resources File** and name the file ErrorResources.resx.</span></span> <span data-ttu-id="7077a-112">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="7077a-112">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="7077a-113">Otevřete soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="7077a-113">Open the resource file.</span></span> <span data-ttu-id="7077a-114">Přidat novou položku s **název** z ErrorString a **hodnotu** z "aktivity není platný."</span><span class="sxs-lookup"><span data-stu-id="7077a-114">Add a new entry with a **Name** of ErrorString and a **Value** of "The activity is not valid."</span></span>  
  
4.  <span data-ttu-id="7077a-115">Přidejte následující `using` příkazy ke třídě.</span><span class="sxs-lookup"><span data-stu-id="7077a-115">Add the following `using` statements to your class.</span></span>  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  <span data-ttu-id="7077a-116">Vytvořte prostředek manager ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="7077a-116">Create a resource manager in your project.</span></span>  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  <span data-ttu-id="7077a-117">Získáte řetězec ze Správce prostředků, kdy je potřeba.</span><span class="sxs-lookup"><span data-stu-id="7077a-117">Get the string from the resource manager where it is required.</span></span>  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 <span data-ttu-id="7077a-118">Následující příklad kódu ukazuje, jak využívat lokalizovaných řetězců v <xref:System.Activities.Activity.CacheMetadata%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7077a-118">The following code sample demonstrates how to utilize localized strings in the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span>  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
