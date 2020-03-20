---
title: Storeadm.exe (nástroj izolovaného úložiště)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: 46e846eaf92835fb2a9130b85ed20749934ca5a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715716"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="c1f70-102">Storeadm.exe (nástroj izolovaného úložiště)</span><span class="sxs-lookup"><span data-stu-id="c1f70-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="c1f70-103">Nástroj izolované úložiště vypíše seznam všech existujících úložišť pro aktuálního uživatele nebo všechna existující úložiště odebere.</span><span class="sxs-lookup"><span data-stu-id="c1f70-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="c1f70-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1f70-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="c1f70-105">Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="c1f70-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="c1f70-106">Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c1f70-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="c1f70-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="c1f70-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f70-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1f70-108">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1f70-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1f70-109">Parameters</span></span>  
  
|<span data-ttu-id="c1f70-110">Možnost</span><span class="sxs-lookup"><span data-stu-id="c1f70-110">Option</span></span>|<span data-ttu-id="c1f70-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c1f70-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c1f70-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="c1f70-112">**/h**[**elp**]</span></span>|<span data-ttu-id="c1f70-113">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="c1f70-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="c1f70-114">**/seznam**</span><span class="sxs-lookup"><span data-stu-id="c1f70-114">**/list**</span></span>|<span data-ttu-id="c1f70-115">Zobrazí všechna existující úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="c1f70-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="c1f70-116">Jedná se o úložiště pro všechny aplikace nebo sestavení spuštěná tímto uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c1f70-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="c1f70-117">**/stroj**</span><span class="sxs-lookup"><span data-stu-id="c1f70-117">**/machine**</span></span>|<span data-ttu-id="c1f70-118">Vybere úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="c1f70-118">Selects the machine store.</span></span> <span data-ttu-id="c1f70-119">Tuto možnost použijte s parametrem **/list** nebo **/remove** a určete, že akce by se měla vztahovat na úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="c1f70-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="c1f70-120">Novinky v rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="c1f70-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="c1f70-121">**/tichý**</span><span class="sxs-lookup"><span data-stu-id="c1f70-121">**/quiet**</span></span>|<span data-ttu-id="c1f70-122">Nastaví tichý režim; potlačí informační výstup tak, aby se zobrazovaly pouze chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c1f70-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="c1f70-123">**/odebrat**</span><span class="sxs-lookup"><span data-stu-id="c1f70-123">**/remove**</span></span>|<span data-ttu-id="c1f70-124">Permanentně odstraní všechna existující úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="c1f70-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="c1f70-125">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="c1f70-125">**/roaming**</span></span>|<span data-ttu-id="c1f70-126">Vybere roamingové úložiště.</span><span class="sxs-lookup"><span data-stu-id="c1f70-126">Selects the roaming store.</span></span> <span data-ttu-id="c1f70-127">Tuto možnost použijte s možnostmi **/list** nebo **/remove** a určete, že akce by se měla vztahovat na cestovní úložiště.</span><span class="sxs-lookup"><span data-stu-id="c1f70-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="c1f70-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="c1f70-128">**/?**</span></span>|<span data-ttu-id="c1f70-129">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="c1f70-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f70-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1f70-130">Remarks</span></span>  
 <span data-ttu-id="c1f70-131">Jestliže spustíte nástroj Storeadm.exe z příkazového řádku bez zadání jakýchkoli možností, zobrazí se syntaxe a možnosti pro tento nástroj.</span><span class="sxs-lookup"><span data-stu-id="c1f70-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="c1f70-132">Možnosti **/list** a **/remove** se obvykle používají jeden po druhém; pokud jsou však zadány dvě nebo více možností, budou provedeny v pořadí, ve kterém se zobrazí na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="c1f70-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="c1f70-133">Aplikace mají možnost ukládat do jednoho nebo dvou úložišť pro uživatele nebo do úložiště počítače:</span><span class="sxs-lookup"><span data-stu-id="c1f70-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="c1f70-134">Místní úložiště existuje v umístění, které je zaručeno, že nebude roaming (v systému Windows 2000 a novější) i v případě, že je pro uživatele povolen datový roaming uživatele.</span><span class="sxs-lookup"><span data-stu-id="c1f70-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="c1f70-135">Úložiště roamingu existuje v umístění, které se může přemísťovat, ale může tak učinit pouze v případě, že je pro uživatele povolen roaming prostřednictvím správy systému Windows NT.</span><span class="sxs-lookup"><span data-stu-id="c1f70-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="c1f70-136">Úložiště počítače je společné pro všechny uživatele počítače a je uloženo ve společném adresáři v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="c1f70-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1f70-137">Úložiště počítače je v rozhraní .NET Framework verze 2.0 novinkou.</span><span class="sxs-lookup"><span data-stu-id="c1f70-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="c1f70-138">To, zda je roaming skutečně povolen pro určitého uživatele, nemá vliv na správu nástroje Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="c1f70-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="c1f70-139">Při spuštění nástroje bez jakýchkoli možností se použijí všechny akce na místní úložiště.</span><span class="sxs-lookup"><span data-stu-id="c1f70-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="c1f70-140">Spuštění nástroje s parametrem **/roaming** použije všechny akce pro úložiště, které je možné přejít.</span><span class="sxs-lookup"><span data-stu-id="c1f70-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="c1f70-141">Spuštění nástroje s parametrem **/machine** použije všechny akce pro úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="c1f70-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f70-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1f70-142">See also</span></span>

- [<span data-ttu-id="c1f70-143">Nástroje</span><span class="sxs-lookup"><span data-stu-id="c1f70-143">Tools</span></span>](index.md)
- [<span data-ttu-id="c1f70-144">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="c1f70-144">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="c1f70-145">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="c1f70-145">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
