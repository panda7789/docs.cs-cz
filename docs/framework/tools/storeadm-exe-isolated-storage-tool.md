---
title: "Storeadm.exe (nástroj izolovaného úložiště)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8351219b8352af7de534ebc5bd6521d5cf4773e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="a5fa9-102">Storeadm.exe (nástroj izolovaného úložiště)</span><span class="sxs-lookup"><span data-stu-id="a5fa9-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="a5fa9-103">Nástroj izolované úložiště vypíše seznam všech existujících úložišť pro aktuálního uživatele nebo všechna existující úložiště odebere.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="a5fa9-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a5fa9-105">Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="a5fa9-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a5fa9-106">Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a5fa9-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="a5fa9-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="a5fa9-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5fa9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5fa9-108">Syntax</span></span>  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5fa9-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5fa9-109">Parameters</span></span>  
  
|<span data-ttu-id="a5fa9-110">Možnost</span><span class="sxs-lookup"><span data-stu-id="a5fa9-110">Option</span></span>|<span data-ttu-id="a5fa9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a5fa9-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a5fa9-112">**/h**[**nápovědu**]</span><span class="sxs-lookup"><span data-stu-id="a5fa9-112">**/h**[**elp**]</span></span>|<span data-ttu-id="a5fa9-113">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="a5fa9-114">**/ list**</span><span class="sxs-lookup"><span data-stu-id="a5fa9-114">**/list**</span></span>|<span data-ttu-id="a5fa9-115">Zobrazí všechna existující úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="a5fa9-116">Jedná se o úložiště pro všechny aplikace nebo sestavení spuštěná tímto uživatelem.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="a5fa9-117">**/ počítače**</span><span class="sxs-lookup"><span data-stu-id="a5fa9-117">**/machine**</span></span>|<span data-ttu-id="a5fa9-118">Vybere úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-118">Selects the machine store.</span></span> <span data-ttu-id="a5fa9-119">Pomocí této možnosti se **/list** nebo **/odebrat** můžete určit, že akce by se měly používat k úložišti počítače.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="a5fa9-120">Novinky v rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="a5fa9-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="a5fa9-121">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="a5fa9-121">**/quiet**</span></span>|<span data-ttu-id="a5fa9-122">Nastaví tichý režim; potlačí informační výstup tak, aby se zobrazovaly pouze chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="a5fa9-123">**/ Remove**</span><span class="sxs-lookup"><span data-stu-id="a5fa9-123">**/remove**</span></span>|<span data-ttu-id="a5fa9-124">Permanentně odstraní všechna existující úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="a5fa9-125">**/ roamingu**</span><span class="sxs-lookup"><span data-stu-id="a5fa9-125">**/roaming**</span></span>|<span data-ttu-id="a5fa9-126">Vybere roamingové úložiště.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-126">Selects the roaming store.</span></span> <span data-ttu-id="a5fa9-127">Pomocí této možnosti se **/list** nebo **/odebrat** možností, které určují, že akce by se měly používat k úložišti roamingu.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="a5fa9-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="a5fa9-128">**/?**</span></span>|<span data-ttu-id="a5fa9-129">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5fa9-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5fa9-130">Remarks</span></span>  
 <span data-ttu-id="a5fa9-131">Jestliže spustíte nástroj Storeadm.exe z příkazového řádku bez zadání jakýchkoli možností, zobrazí se syntaxe a možnosti pro tento nástroj.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="a5fa9-132">**/List** a **/odebrat** možnosti jsou obvykle používanými jeden po druhém, ale pokud jsou zadány dvě nebo více možností se bude provedena v pořadí, ve kterém jsou zobrazeny na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="a5fa9-133">Aplikace mají možnost ukládat do jednoho nebo dvou úložišť pro uživatele nebo do úložiště počítače:</span><span class="sxs-lookup"><span data-stu-id="a5fa9-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
-   <span data-ttu-id="a5fa9-134">V umístění, které záruku, že není se bude používat roaming (v systému Windows 2000 a novější), i když je uživatel datový roaming je povolená pro uživatele existuje místní úložiště.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
-   <span data-ttu-id="a5fa9-135">Cestovní úložiště existuje v umístění, které je možné přesouvat, ale můžete tak učinit pouze pokud je roaming povolený pro uživatele na základě správy systému Windows NT.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
-   <span data-ttu-id="a5fa9-136">Úložiště počítače je společné pro všechny uživatele počítače a je uloženo ve společném adresáři v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a5fa9-137">Úložiště počítače je v rozhraní .NET Framework verze 2.0 novinkou.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="a5fa9-138">To, zda je roaming skutečně povolen pro určitého uživatele, nemá vliv na správu nástroje Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="a5fa9-139">Při spuštění nástroje bez jakýchkoli možností se použijí všechny akce na místní úložiště.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="a5fa9-140">Spuštění nástroje s **/ roamingu** možnost se vztahuje k úložišti, který se bude moct přesouvat všechny akce.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="a5fa9-141">Spuštění nástroje s **/machine** možnost všechny akce se vztahuje na úložišti počítače.</span><span class="sxs-lookup"><span data-stu-id="a5fa9-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fa9-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5fa9-142">See Also</span></span>  
 [<span data-ttu-id="a5fa9-143">Nástroje</span><span class="sxs-lookup"><span data-stu-id="a5fa9-143">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="a5fa9-144">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="a5fa9-144">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="a5fa9-145">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="a5fa9-145">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
