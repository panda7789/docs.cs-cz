---
title: Storeadm.exe (nástroj izolovaného úložiště)
description: Přečtěte si o Storeadm.exe, nástroji izolované úložiště. Tento nástroj vypíše nebo odebere všechna existující úložiště pro aktuálního uživatele.
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: 153fc2b4b5a955fd5ed768d1492f053595363e6e
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517006"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="67594-104">Storeadm.exe (nástroj izolovaného úložiště)</span><span class="sxs-lookup"><span data-stu-id="67594-104">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="67594-105">Nástroj izolované úložiště vypíše seznam všech existujících úložišť pro aktuálního uživatele nebo všechna existující úložiště odebere.</span><span class="sxs-lookup"><span data-stu-id="67594-105">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="67594-106">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67594-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="67594-107">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="67594-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="67594-108">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="67594-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="67594-109">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="67594-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67594-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67594-110">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="67594-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="67594-111">Parameters</span></span>  
  
|<span data-ttu-id="67594-112">Možnost</span><span class="sxs-lookup"><span data-stu-id="67594-112">Option</span></span>|<span data-ttu-id="67594-113">Popis</span><span class="sxs-lookup"><span data-stu-id="67594-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="67594-114">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="67594-114">**/h**[**elp**]</span></span>|<span data-ttu-id="67594-115">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="67594-115">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="67594-116">**/list**</span><span class="sxs-lookup"><span data-stu-id="67594-116">**/list**</span></span>|<span data-ttu-id="67594-117">Zobrazí všechna existující úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="67594-117">Displays all existing stores for the current user.</span></span> <span data-ttu-id="67594-118">Jedná se o úložiště pro všechny aplikace nebo sestavení spuštěná tímto uživatelem.</span><span class="sxs-lookup"><span data-stu-id="67594-118">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="67594-119">**/Machine**</span><span class="sxs-lookup"><span data-stu-id="67594-119">**/machine**</span></span>|<span data-ttu-id="67594-120">Vybere úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="67594-120">Selects the machine store.</span></span> <span data-ttu-id="67594-121">Tuto možnost použijte spolu s možností **/list** nebo **/Remove** a určete tak, že se akce má vztahovat na úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="67594-121">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="67594-122">Novinky v rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="67594-122">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="67594-123">**parametr**</span><span class="sxs-lookup"><span data-stu-id="67594-123">**/quiet**</span></span>|<span data-ttu-id="67594-124">Nastaví tichý režim; potlačí informační výstup tak, aby se zobrazovaly pouze chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="67594-124">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="67594-125">**/Remove**</span><span class="sxs-lookup"><span data-stu-id="67594-125">**/remove**</span></span>|<span data-ttu-id="67594-126">Permanentně odstraní všechna existující úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="67594-126">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="67594-127">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="67594-127">**/roaming**</span></span>|<span data-ttu-id="67594-128">Vybere roamingové úložiště.</span><span class="sxs-lookup"><span data-stu-id="67594-128">Selects the roaming store.</span></span> <span data-ttu-id="67594-129">Tuto možnost použijte spolu s možnostmi **/list** nebo **/Remove** k určení, že by akce měla platit pro roamingové úložiště.</span><span class="sxs-lookup"><span data-stu-id="67594-129">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="67594-130">**/?**</span><span class="sxs-lookup"><span data-stu-id="67594-130">**/?**</span></span>|<span data-ttu-id="67594-131">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="67594-131">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67594-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67594-132">Remarks</span></span>  
 <span data-ttu-id="67594-133">Jestliže spustíte nástroj Storeadm.exe z příkazového řádku bez zadání jakýchkoli možností, zobrazí se syntaxe a možnosti pro tento nástroj.</span><span class="sxs-lookup"><span data-stu-id="67594-133">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="67594-134">Možnosti **/list** a **/Remove** jsou obvykle používány po jednom. Pokud jsou však zadány dvě nebo více možností, budou provedeny v pořadí, ve kterém se zobrazí na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="67594-134">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="67594-135">Aplikace mají možnost ukládat do jednoho nebo dvou úložišť pro uživatele nebo do úložiště počítače:</span><span class="sxs-lookup"><span data-stu-id="67594-135">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="67594-136">Místní úložiště existuje v umístění, ve kterém se garantuje roaming (ve Windows 2000 a novějším), a to i v případě, že je pro uživatele povolen roaming dat uživatele.</span><span class="sxs-lookup"><span data-stu-id="67594-136">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="67594-137">Roamingové úložiště existuje v umístění, které se může přenášet, ale může to udělat jenom v případě, že je pro uživatele povolený roaming prostřednictvím správy systému Windows NT.</span><span class="sxs-lookup"><span data-stu-id="67594-137">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="67594-138">Úložiště počítače je společné pro všechny uživatele počítače a je uloženo ve společném adresáři v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="67594-138">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="67594-139">Úložiště počítače je v rozhraní .NET Framework verze 2.0 novinkou.</span><span class="sxs-lookup"><span data-stu-id="67594-139">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="67594-140">To, zda je roaming skutečně povolen pro určitého uživatele, nemá vliv na správu nástroje Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="67594-140">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="67594-141">Při spuštění nástroje bez jakýchkoli možností se použijí všechny akce na místní úložiště.</span><span class="sxs-lookup"><span data-stu-id="67594-141">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="67594-142">Spuštění nástroje s možností **/roaming** aplikuje všechny akce do úložiště, které je možné přenášet na roaming.</span><span class="sxs-lookup"><span data-stu-id="67594-142">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="67594-143">Spuštění nástroje s možností **/Machine** použije všechny akce na úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="67594-143">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67594-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="67594-144">See also</span></span>

- [<span data-ttu-id="67594-145">Nástroje</span><span class="sxs-lookup"><span data-stu-id="67594-145">Tools</span></span>](index.md)
- [<span data-ttu-id="67594-146">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="67594-146">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="67594-147">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="67594-147">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
