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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715716"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="c4e6b-102">Storeadm.exe (nástroj izolovaného úložiště)</span><span class="sxs-lookup"><span data-stu-id="c4e6b-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="c4e6b-103">Nástroj izolované úložiště vypíše seznam všech existujících úložišť pro aktuálního uživatele nebo všechna existující úložiště odebere.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="c4e6b-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="c4e6b-105">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="c4e6b-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="c4e6b-106">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c4e6b-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="c4e6b-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="c4e6b-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e6b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4e6b-108">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4e6b-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4e6b-109">Parameters</span></span>  
  
|<span data-ttu-id="c4e6b-110">Možnost</span><span class="sxs-lookup"><span data-stu-id="c4e6b-110">Option</span></span>|<span data-ttu-id="c4e6b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c4e6b-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c4e6b-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="c4e6b-112">**/h**[**elp**]</span></span>|<span data-ttu-id="c4e6b-113">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="c4e6b-114">**/list**</span><span class="sxs-lookup"><span data-stu-id="c4e6b-114">**/list**</span></span>|<span data-ttu-id="c4e6b-115">Zobrazí všechna existující úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="c4e6b-116">Jedná se o úložiště pro všechny aplikace nebo sestavení spuštěná tímto uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="c4e6b-117">**/Machine**</span><span class="sxs-lookup"><span data-stu-id="c4e6b-117">**/machine**</span></span>|<span data-ttu-id="c4e6b-118">Vybere úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-118">Selects the machine store.</span></span> <span data-ttu-id="c4e6b-119">Tuto možnost použijte spolu s možností **/list** nebo **/Remove** a určete tak, že se akce má vztahovat na úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="c4e6b-120">Novinky v rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="c4e6b-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="c4e6b-121">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="c4e6b-121">**/quiet**</span></span>|<span data-ttu-id="c4e6b-122">Nastaví tichý režim; potlačí informační výstup tak, aby se zobrazovaly pouze chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="c4e6b-123">**/Remove**</span><span class="sxs-lookup"><span data-stu-id="c4e6b-123">**/remove**</span></span>|<span data-ttu-id="c4e6b-124">Permanentně odstraní všechna existující úložiště pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="c4e6b-125">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="c4e6b-125">**/roaming**</span></span>|<span data-ttu-id="c4e6b-126">Vybere roamingové úložiště.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-126">Selects the roaming store.</span></span> <span data-ttu-id="c4e6b-127">Tuto možnost použijte spolu s možnostmi **/list** nebo **/Remove** k určení, že by akce měla platit pro roamingové úložiště.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="c4e6b-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="c4e6b-128">**/?**</span></span>|<span data-ttu-id="c4e6b-129">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4e6b-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4e6b-130">Remarks</span></span>  
 <span data-ttu-id="c4e6b-131">Jestliže spustíte nástroj Storeadm.exe z příkazového řádku bez zadání jakýchkoli možností, zobrazí se syntaxe a možnosti pro tento nástroj.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="c4e6b-132">Možnosti **/list** a **/Remove** jsou obvykle používány po jednom. Pokud jsou však zadány dvě nebo více možností, budou provedeny v pořadí, ve kterém se zobrazí na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="c4e6b-133">Aplikace mají možnost ukládat do jednoho nebo dvou úložišť pro uživatele nebo do úložiště počítače:</span><span class="sxs-lookup"><span data-stu-id="c4e6b-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="c4e6b-134">Místní úložiště existuje v umístění, ve kterém se garantuje roaming (ve Windows 2000 a novějším), a to i v případě, že je pro uživatele povolen roaming dat uživatele.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="c4e6b-135">Roamingové úložiště existuje v umístění, které se může přenášet, ale může to udělat jenom v případě, že je pro uživatele povolený roaming prostřednictvím správy systému Windows NT.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="c4e6b-136">Úložiště počítače je společné pro všechny uživatele počítače a je uloženo ve společném adresáři v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c4e6b-137">Úložiště počítače je v rozhraní .NET Framework verze 2.0 novinkou.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="c4e6b-138">To, zda je roaming skutečně povolen pro určitého uživatele, nemá vliv na správu nástroje Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="c4e6b-139">Při spuštění nástroje bez jakýchkoli možností se použijí všechny akce na místní úložiště.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="c4e6b-140">Spuštění nástroje s možností **/roaming** aplikuje všechny akce do úložiště, které je možné přenášet na roaming.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="c4e6b-141">Spuštění nástroje s možností **/Machine** použije všechny akce na úložiště počítače.</span><span class="sxs-lookup"><span data-stu-id="c4e6b-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e6b-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4e6b-142">See also</span></span>

- [<span data-ttu-id="c4e6b-143">Nástroje</span><span class="sxs-lookup"><span data-stu-id="c4e6b-143">Tools</span></span>](index.md)
- [<span data-ttu-id="c4e6b-144">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="c4e6b-144">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="c4e6b-145">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="c4e6b-145">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
