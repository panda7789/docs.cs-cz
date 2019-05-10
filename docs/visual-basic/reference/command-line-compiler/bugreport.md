---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 6ff9aa23fb6d7dee5c245ed174318f6589e7d245
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624322"
---
# <a name="-bugreport"></a><span data-ttu-id="3ddee-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="3ddee-102">-bugreport</span></span>
<span data-ttu-id="3ddee-103">Vytvoří soubor, který vám pomůže při souboru hlášení o chybě.</span><span class="sxs-lookup"><span data-stu-id="3ddee-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ddee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ddee-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3ddee-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3ddee-105">Arguments</span></span>  
  
|<span data-ttu-id="3ddee-106">Termín</span><span class="sxs-lookup"><span data-stu-id="3ddee-106">Term</span></span>|<span data-ttu-id="3ddee-107">Definice</span><span class="sxs-lookup"><span data-stu-id="3ddee-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="3ddee-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3ddee-108">Required.</span></span> <span data-ttu-id="3ddee-109">Název souboru, který bude obsahovat vaše hlášení o chybě.</span><span class="sxs-lookup"><span data-stu-id="3ddee-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="3ddee-110">Název souboru uzavřete do uvozovek ("") Pokud název obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="3ddee-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ddee-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ddee-111">Remarks</span></span>  
 <span data-ttu-id="3ddee-112">Následující informace se přidají do `file`:</span><span class="sxs-lookup"><span data-stu-id="3ddee-112">The following information is added to `file`:</span></span>  
  
- <span data-ttu-id="3ddee-113">Zkopírujte všechny soubory zdrojového kódu dané kompilace.</span><span class="sxs-lookup"><span data-stu-id="3ddee-113">A copy of all source-code files in the compilation.</span></span>  
  
- <span data-ttu-id="3ddee-114">Seznam možností kompilátoru použita při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="3ddee-114">A list of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="3ddee-115">Informace o verzi kompilátoru, modul common language runtime a operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3ddee-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
- <span data-ttu-id="3ddee-116">Výstup kompilátoru, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="3ddee-116">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="3ddee-117">Popis problému, pro který se zobrazí výzva.</span><span class="sxs-lookup"><span data-stu-id="3ddee-117">A description of the problem, for which you are prompted.</span></span>  
  
- <span data-ttu-id="3ddee-118">Popis jak domníváte, že problém je třeba stanovit, pro který se zobrazí výzva.</span><span class="sxs-lookup"><span data-stu-id="3ddee-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="3ddee-119">Vzhledem k tomu, že kopie všech souborů zdrojového kódu je součástí `file`, možná budete chtít reprodukovat (podezřelý) kód v nejkratší možné program.</span><span class="sxs-lookup"><span data-stu-id="3ddee-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ddee-120">`-bugreport` Možnost vytvoří soubor, který obsahuje potenciálně citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="3ddee-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="3ddee-121">Jedná se o aktuální čas, verze kompilátoru [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] verzi, verze operačního systému, uživatelské jméno, argumenty příkazového řádku, pomocí kterých kompilátor byla spuštěna, s veškerým zdrojovým kódem a binární forma všechny odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="3ddee-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="3ddee-122">Tuto možnost můžete přistupovat zadáním možnosti příkazového řádku v souboru Web.config pro kompilaci na straně serveru z [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ddee-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="3ddee-123">Chcete-li tomu zabránit, upravte soubor Machine.config chcete zakázat uživatelům v kompilaci na serveru.</span><span class="sxs-lookup"><span data-stu-id="3ddee-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="3ddee-124">Pokud tato možnost se používá s `-errorreport:prompt`, `-errorreport:queue`, nebo `-errorreport:send`, a aplikace zaznamená chybu kompilátoru, informace v `file` odeslány společnosti Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="3ddee-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="3ddee-125">Tyto informace vám pomohou určit příčinu chyby odborníky z Microsoftu a může zvýšit následující verzi jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3ddee-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="3ddee-126">Ve výchozím nastavení žádné informace se neposílají do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="3ddee-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="3ddee-127">Nicméně pokud kompilujete aplikace s použitím `-errorreport:queue`, který je ve výchozím nastavení povolené, aplikace shromáždí jeho zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="3ddee-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="3ddee-128">Potom při přihlášení správce počítače, Chyba při vytváření sestav systému zobrazí automaticky otevírané okno, které umožňuje správcům předávání do Microsoftu zprávy o všech chybách, ke které došlo od přihlášení.</span><span class="sxs-lookup"><span data-stu-id="3ddee-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ddee-129">`/bugreport` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici, pouze pokud kompilujete z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3ddee-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ddee-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ddee-130">Example</span></span>  
 <span data-ttu-id="3ddee-131">Následující příklad se zkompiluje `T2.vb` a umístí všechny informace pro hlášení chyb v souboru `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="3ddee-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ddee-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ddee-132">See also</span></span>

- [<span data-ttu-id="3ddee-133">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="3ddee-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3ddee-134">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ddee-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="3ddee-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="3ddee-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [<span data-ttu-id="3ddee-136">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="3ddee-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="3ddee-137">[trustLevel – Element pro securityPolicy (schéma nastavení technologie ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3ddee-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
