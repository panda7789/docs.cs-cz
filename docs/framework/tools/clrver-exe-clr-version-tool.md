---
title: Clrver.exe (nástroj verze CLR)
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: bfc612ef5455e1b4a03d15fd99a8a1873d2c7c08
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715800"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="74deb-102">Clrver.exe (nástroj verze CLR)</span><span class="sxs-lookup"><span data-stu-id="74deb-102">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="74deb-103">Nástroj CLR Version (Clrver.exe) vypíše všechny verze modulu Common Language Runtime (CLR) nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="74deb-103">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="74deb-104">Tento nástroj je automaticky nainstalován se sadou Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="74deb-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="74deb-105">Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7).</span><span class="sxs-lookup"><span data-stu-id="74deb-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="74deb-106">Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="74deb-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="74deb-107">V příkazovém řádku zadejte následující:</span><span class="sxs-lookup"><span data-stu-id="74deb-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74deb-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74deb-108">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="74deb-109">Možnosti</span><span class="sxs-lookup"><span data-stu-id="74deb-109">Options</span></span>  
  
|<span data-ttu-id="74deb-110">Možnost</span><span class="sxs-lookup"><span data-stu-id="74deb-110">Option</span></span>|<span data-ttu-id="74deb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="74deb-111">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="74deb-112">Zobrazí všechny procesy v počítači využívající modul CLR.</span><span class="sxs-lookup"><span data-stu-id="74deb-112">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="74deb-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="74deb-113">*pid*</span></span>|<span data-ttu-id="74deb-114">Zobrazí verze modulu CLR využívané procesem se zadaným identifikátorem ID procesu (PID).</span><span class="sxs-lookup"><span data-stu-id="74deb-114">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="74deb-115">Zobrazí syntaxi příkazu a možnosti nástroje.</span><span class="sxs-lookup"><span data-stu-id="74deb-115">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74deb-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74deb-116">Remarks</span></span>  
 <span data-ttu-id="74deb-117">Při volání nástroje Clrver.exe bez použití možností se zobrazí všechny nainstalované verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="74deb-117">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="74deb-118">Pokud zadáte identifikátor PID pro jiného uživatele, musíte mít oprávnění správce, chcete-li získat informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="74deb-118">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74deb-119">Nástroj Řízení uživatelských účtů (UAC) v systému Windows Vista a novějším určuje oprávnění uživatele.</span><span class="sxs-lookup"><span data-stu-id="74deb-119">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="74deb-120">Pokud jste členem předdefinované skupiny Administrators, máte přiřazeny dva přístupové tokeny run-time: token přístupu uživatele se standardním oprávněním a token přístupu správce.</span><span class="sxs-lookup"><span data-stu-id="74deb-120">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="74deb-121">Ve výchozím nastavení máte roli standardního uživatele.</span><span class="sxs-lookup"><span data-stu-id="74deb-121">By default, you are in the standard user role.</span></span> <span data-ttu-id="74deb-122">Chcete-li spustit kód vyžadující oprávnění správce, musíte nejprve zvýšit své oprávnění ze standardního uživatele na správce.</span><span class="sxs-lookup"><span data-stu-id="74deb-122">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="74deb-123">Můžete tak učinit při spouštění příkazového řádku kliknutím pravým tlačítkem myši na ikonu příkazového řádku a označením, že chcete nástroj spustit jako správce.</span><span class="sxs-lookup"><span data-stu-id="74deb-123">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="74deb-124">Při pokusu o určení verze modulu CLR pro procesy SYSTEM, LOCAL SERVICE a NETWORK SERVICE dojde k zobrazení zprávy, že PID neexistuje.</span><span class="sxs-lookup"><span data-stu-id="74deb-124">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="74deb-125">Příklady</span><span class="sxs-lookup"><span data-stu-id="74deb-125">Examples</span></span>  
 <span data-ttu-id="74deb-126">Následující příkaz zobrazí všechny verze modulu CLR nainstalované v počítači.</span><span class="sxs-lookup"><span data-stu-id="74deb-126">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="74deb-127">Následující příkaz zobrazí verzi modulu CLR používanou procesem 128.</span><span class="sxs-lookup"><span data-stu-id="74deb-127">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="74deb-128">Následující příkaz zobrazí všechny spravované procesy a verzi modulu CLR, kterou používají.</span><span class="sxs-lookup"><span data-stu-id="74deb-128">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="74deb-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74deb-129">See also</span></span>

- [<span data-ttu-id="74deb-130">Nástroje</span><span class="sxs-lookup"><span data-stu-id="74deb-130">Tools</span></span>](index.md)
- [<span data-ttu-id="74deb-131">Příkazové řádky</span><span class="sxs-lookup"><span data-stu-id="74deb-131">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
