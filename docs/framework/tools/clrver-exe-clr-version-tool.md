---
title: Clrver.exe (nástroj verze CLR)
description: Kontrola Clrver.exe, nástroje verze CLR. Tento nástroj oznamuje všechny nainstalované verze modulu CLR (Common Language Runtime) v počítači.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: e914034819418df00438c454e209e6c86779ba3c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167280"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="8b1c5-104">Clrver.exe (nástroj verze CLR)</span><span class="sxs-lookup"><span data-stu-id="8b1c5-104">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="8b1c5-105">Nástroj CLR Version (Clrver.exe) vypíše všechny verze modulu Common Language Runtime (CLR) nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="8b1c5-106">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="8b1c5-107">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="8b1c5-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="8b1c5-108">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8b1c5-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="8b1c5-109">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="8b1c5-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1c5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b1c5-110">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="8b1c5-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8b1c5-111">Options</span></span>  
  
|<span data-ttu-id="8b1c5-112">Možnost</span><span class="sxs-lookup"><span data-stu-id="8b1c5-112">Option</span></span>|<span data-ttu-id="8b1c5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8b1c5-113">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="8b1c5-114">Zobrazí všechny procesy v počítači využívající modul CLR.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-114">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="8b1c5-115">*PID*</span><span class="sxs-lookup"><span data-stu-id="8b1c5-115">*pid*</span></span>|<span data-ttu-id="8b1c5-116">Zobrazí verze modulu CLR využívané procesem se zadaným identifikátorem ID procesu (PID).</span><span class="sxs-lookup"><span data-stu-id="8b1c5-116">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="8b1c5-117">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-117">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b1c5-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b1c5-118">Remarks</span></span>  
 <span data-ttu-id="8b1c5-119">Při volání nástroje Clrver.exe bez použití možností se zobrazí všechny nainstalované verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-119">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="8b1c5-120">Pokud zadáte identifikátor PID pro jiného uživatele, musíte mít oprávnění správce, chcete-li získat informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-120">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b1c5-121">Nástroj Řízení uživatelských účtů (UAC) v systému Windows Vista a novějším určuje oprávnění uživatele.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-121">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="8b1c5-122">Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-122">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="8b1c5-123">Ve výchozím nastavení máte roli standardního uživatele.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-123">By default, you are in the standard user role.</span></span> <span data-ttu-id="8b1c5-124">Chcete-li spustit kód vyžadující oprávnění správce, musíte nejprve zvýšit své oprávnění ze standardního uživatele na správce.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-124">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="8b1c5-125">Můžete tak učinit při spouštění příkazového řádku kliknutím pravým tlačítkem myši na ikonu příkazového řádku a označením, že chcete nástroj spustit jako správce.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-125">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="8b1c5-126">Při pokusu o určení verze modulu CLR pro procesy SYSTEM, LOCAL SERVICE a NETWORK SERVICE dojde k zobrazení zprávy, že PID neexistuje.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-126">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8b1c5-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="8b1c5-127">Examples</span></span>  
 <span data-ttu-id="8b1c5-128">Následující příkaz zobrazí všechny verze modulu CLR nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-128">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="8b1c5-129">Následující příkaz zobrazí verzi modulu CLR používanou procesem 128.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-129">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="8b1c5-130">Následující příkaz zobrazí všechny spravované procesy a verzi modulu CLR, kterou používají.</span><span class="sxs-lookup"><span data-stu-id="8b1c5-130">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="8b1c5-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b1c5-131">See also</span></span>

- [<span data-ttu-id="8b1c5-132">Nástroje</span><span class="sxs-lookup"><span data-stu-id="8b1c5-132">Tools</span></span>](index.md)
- [<span data-ttu-id="8b1c5-133">Výzvy příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="8b1c5-133">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
