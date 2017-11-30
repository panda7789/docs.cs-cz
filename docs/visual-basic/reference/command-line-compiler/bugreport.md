---
title: /bugreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7090142f940ae42f554fc0ba16bcc80d8537e38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bugreport"></a><span data-ttu-id="ef40d-102">/bugreport</span><span class="sxs-lookup"><span data-stu-id="ef40d-102">/bugreport</span></span>
<span data-ttu-id="ef40d-103">Vytvoří soubor, který můžete použít, když soubor sestavy chyb.</span><span class="sxs-lookup"><span data-stu-id="ef40d-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef40d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef40d-104">Syntax</span></span>  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ef40d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ef40d-105">Arguments</span></span>  
  
|<span data-ttu-id="ef40d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ef40d-106">Term</span></span>|<span data-ttu-id="ef40d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ef40d-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="ef40d-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ef40d-108">Required.</span></span> <span data-ttu-id="ef40d-109">Název souboru, který bude obsahovat sestavy chyb.</span><span class="sxs-lookup"><span data-stu-id="ef40d-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="ef40d-110">Uzavřete název souboru v uvozovkách ("") Pokud název obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="ef40d-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef40d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef40d-111">Remarks</span></span>  
 <span data-ttu-id="ef40d-112">Následující informace, které jsou přidány do `file`:</span><span class="sxs-lookup"><span data-stu-id="ef40d-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="ef40d-113">Kopírování všech souborů zdrojového kódu v kompilace.</span><span class="sxs-lookup"><span data-stu-id="ef40d-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="ef40d-114">Seznam možností kompilátoru použita při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="ef40d-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="ef40d-115">Informace o verzi o kompilátoru, modul common language runtime a operačního systému.</span><span class="sxs-lookup"><span data-stu-id="ef40d-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="ef40d-116">Výstup kompilátoru, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="ef40d-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="ef40d-117">Popis problému, pro který se zobrazí výzva.</span><span class="sxs-lookup"><span data-stu-id="ef40d-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="ef40d-118">Popis jak domníváte, že problém je třeba stanovit, pro který se zobrazí výzva.</span><span class="sxs-lookup"><span data-stu-id="ef40d-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="ef40d-119">Protože je součástí kopii všechny soubory zdrojového kódu `file`, možná budete chtít reprodukovat (možného) kód do nejkratší programu.</span><span class="sxs-lookup"><span data-stu-id="ef40d-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef40d-120">`/bugreport` Možnost vytvoří soubor, který obsahuje potenciálně citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="ef40d-120">The `/bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="ef40d-121">To zahrnuje aktuální čas, verze kompilátoru [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] verze, verze operačního systému, uživatelské jméno, argumenty příkazového řádku, se kterými kompilátor bylo spuštěno, všechny zdrojového kódu a binárního formátu všech odkazovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef40d-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="ef40d-122">Tato možnost je přístupná zadáním možnosti příkazového řádku v souboru Web.config pro kompilaci na straně serveru [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef40d-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="ef40d-123">Chcete-li tomu zabránit, upravte souboru Machine.config. Chcete-li zakázat uživatelům v kompilaci na serveru.</span><span class="sxs-lookup"><span data-stu-id="ef40d-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="ef40d-124">Pokud tato možnost se používá s `/errorreport:prompt`, `/errorreport:queue`, nebo `/errorreport:send`, a aplikace, dojde k chybě vnitřní kompilátoru, informace v `file` je odeslány společnosti Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="ef40d-124">If this option is used with `/errorreport:prompt`, `/errorreport:queue`, or `/errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="ef40d-125">Tyto informace vám pomohou určit příčinu chyby pracovníci společnosti Microsoft a může pomoct zlepšit další verzi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef40d-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="ef40d-126">Ve výchozím nastavení je odeslány žádné informace společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ef40d-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="ef40d-127">Ale při kompilaci aplikace pomocí `/errorreport:queue`, který je ve výchozím nastavení povolené, aplikace shromažďuje jeho zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="ef40d-127">However, when you compile an application by using `/errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="ef40d-128">Pak když se na správce přihlásí, zobrazí se chyba systému místní okno, které umožňuje správcům předávat je společnosti Microsoft sestavy všechny chyby, které došlo od přihlášení.</span><span class="sxs-lookup"><span data-stu-id="ef40d-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef40d-129">`/bugreport` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici, pouze při sestavování z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ef40d-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef40d-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef40d-130">Example</span></span>  
 <span data-ttu-id="ef40d-131">Následující příklad zkompiluje `T2.vb` a vloží všechny informace o vytváření sestav chyb v souboru `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="ef40d-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef40d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef40d-132">See Also</span></span>  
 [<span data-ttu-id="ef40d-133">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ef40d-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ef40d-134">/ Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef40d-134">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="ef40d-135">/ errorreport</span><span class="sxs-lookup"><span data-stu-id="ef40d-135">/errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [<span data-ttu-id="ef40d-136">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ef40d-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="ef40d-137">trustLevel Element pro securityPolicy (schéma nastavení ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="ef40d-137">trustLevel Element for securityPolicy (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)
