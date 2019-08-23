---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 75c3e5842447a8f0812d5a90d7157f7a6a496936
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962448"
---
# <a name="-bugreport"></a><span data-ttu-id="b6faa-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="b6faa-102">-bugreport</span></span>
<span data-ttu-id="b6faa-103">Vytvoří soubor, který můžete použít při zaznamenání zprávy o chybě.</span><span class="sxs-lookup"><span data-stu-id="b6faa-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6faa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6faa-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6faa-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b6faa-105">Arguments</span></span>  
  
|<span data-ttu-id="b6faa-106">Termín</span><span class="sxs-lookup"><span data-stu-id="b6faa-106">Term</span></span>|<span data-ttu-id="b6faa-107">Definice</span><span class="sxs-lookup"><span data-stu-id="b6faa-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="b6faa-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b6faa-108">Required.</span></span> <span data-ttu-id="b6faa-109">Název souboru, který bude obsahovat zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="b6faa-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="b6faa-110">Uzavřete název souboru do uvozovek (""), pokud název obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="b6faa-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6faa-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6faa-111">Remarks</span></span>  
 <span data-ttu-id="b6faa-112">Do `file`této části jsou přidány následující informace:</span><span class="sxs-lookup"><span data-stu-id="b6faa-112">The following information is added to `file`:</span></span>  
  
- <span data-ttu-id="b6faa-113">Kopii všech souborů zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="b6faa-113">A copy of all source-code files in the compilation.</span></span>  
  
- <span data-ttu-id="b6faa-114">Seznam možností kompilátoru použitých v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="b6faa-114">A list of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="b6faa-115">Informace o verzi pro kompilátor, modul CLR (Common Language Runtime) a operační systém.</span><span class="sxs-lookup"><span data-stu-id="b6faa-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
- <span data-ttu-id="b6faa-116">Výstup kompilátoru, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="b6faa-116">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="b6faa-117">Popis problému, pro který se zobrazí výzva.</span><span class="sxs-lookup"><span data-stu-id="b6faa-117">A description of the problem, for which you are prompted.</span></span>  
  
- <span data-ttu-id="b6faa-118">Popis toho, jak si myslíte problém, by měl být vyřešen, pro který se zobrazí výzva.</span><span class="sxs-lookup"><span data-stu-id="b6faa-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="b6faa-119">Vzhledem k tomu `file`, že je do aplikace zahrnutá kopie všech souborů zdrojového kódu, můžete v nejbližším programu chtít reprodukování vady kódu (podezřelé).</span><span class="sxs-lookup"><span data-stu-id="b6faa-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b6faa-120">`-bugreport` Možnost vytvoří soubor, který obsahuje potenciálně citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="b6faa-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="b6faa-121">Patří sem aktuální čas, verze kompilátoru, verze .NET Framework, verze operačního systému, uživatelské jméno, argumenty příkazového řádku, s nimiž byl kompilátor spuštěn, veškerý zdrojový kód a binární forma libovolného odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6faa-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="b6faa-122">Tato možnost je k dispozici při zadání možností příkazového řádku v souboru Web. config pro kompilaci ASP.NET aplikace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="b6faa-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="b6faa-123">Chcete-li tomu zabránit, upravte soubor Machine. config tak, aby nedocházelo k tomu, aby uživatelé mohli kompilovat na serveru.</span><span class="sxs-lookup"><span data-stu-id="b6faa-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="b6faa-124">Pokud je tato možnost použita s `-errorreport:prompt`, `-errorreport:queue`nebo `-errorreport:send`a vaše aplikace narazí na vnitřní chybu kompilátoru, informace v `file` nástroji se odesílají společnosti Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="b6faa-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="b6faa-125">Tyto informace pomohou technikům Microsoftu identifikovat příčinu chyby a mohou pomoci zlepšit další vydání Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b6faa-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="b6faa-126">Ve výchozím nastavení se Microsoftu neodesílají žádné informace.</span><span class="sxs-lookup"><span data-stu-id="b6faa-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="b6faa-127">Pokud však zkompilujete aplikaci pomocí nástroje `-errorreport:queue`, který je ve výchozím nastavení povolený, aplikace shromáždí své zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="b6faa-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="b6faa-128">Až se správce počítače přihlásí, systém zasílání zpráv o chybách zobrazí automaticky otevírané okno, které správci umožní předávat společnosti Microsoft jakékoli zprávy o chybách, ke kterým došlo od přihlášení.</span><span class="sxs-lookup"><span data-stu-id="b6faa-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6faa-129">Tato `/bugreport` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="b6faa-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6faa-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6faa-130">Example</span></span>  
 <span data-ttu-id="b6faa-131">Následující příklad zkompiluje `T2.vb` a vloží všechny informace o hlášení chyb v souboru `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="b6faa-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6faa-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6faa-132">See also</span></span>

- [<span data-ttu-id="b6faa-133">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="b6faa-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="b6faa-134">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6faa-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="b6faa-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="b6faa-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [<span data-ttu-id="b6faa-136">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="b6faa-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="b6faa-137">[Element trustLevel pro securityPolicy (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b6faa-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>
