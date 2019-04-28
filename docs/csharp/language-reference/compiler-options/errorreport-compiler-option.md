---
title: -errorreport (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 4797f35a3738955f620fad7a93f8695685d21057
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662917"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="83e9f-102">-errorreport (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="83e9f-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="83e9f-103">Tato možnost poskytuje pohodlný způsob, jak nahlásit chybu kompilátoru jazyka C# společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="83e9f-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83e9f-104">Ve Windows Vista a Windows Server 2008 nastavení generování sestav chyb, které jste udělali ve Visual Studio přepsat nastavení provedená prostřednictvím Windows Chyba vytváření sestav (zasílání).</span><span class="sxs-lookup"><span data-stu-id="83e9f-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="83e9f-105">Nastavení zasílání vždy přednost před nastavením hlášení chyb sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="83e9f-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e9f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83e9f-106">Syntax</span></span>  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="83e9f-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="83e9f-107">Arguments</span></span>  
 <span data-ttu-id="83e9f-108">**None**</span><span class="sxs-lookup"><span data-stu-id="83e9f-108">**none**</span></span>  
 <span data-ttu-id="83e9f-109">Sestavy o vnitřních chybách kompilátoru nebudou shromážděné nebo odeslané společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="83e9f-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="83e9f-110">**prompt**</span><span class="sxs-lookup"><span data-stu-id="83e9f-110">**prompt**</span></span>  
 <span data-ttu-id="83e9f-111">Zobrazí výzvu k odeslání hlášení, pokud obdržíte chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="83e9f-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="83e9f-112">**řádek** výchozí nastavení je při kompilaci aplikace ve vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="83e9f-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="83e9f-113">**fronty**</span><span class="sxs-lookup"><span data-stu-id="83e9f-113">**queue**</span></span>  
 <span data-ttu-id="83e9f-114">Zařadí do fronty zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="83e9f-114">Queues the error report.</span></span> <span data-ttu-id="83e9f-115">Při přihlášení s přihlašovacími údaji správce, můžete nahlásit všechny chyby od posledního přihlášení.</span><span class="sxs-lookup"><span data-stu-id="83e9f-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="83e9f-116">Nezobrazí výzva k odeslání zprávy o chybách více než jednou za tři dny.</span><span class="sxs-lookup"><span data-stu-id="83e9f-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="83e9f-117">**fronty** výchozí nastavení je při kompilaci aplikace příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="83e9f-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="83e9f-118">**Odeslat**</span><span class="sxs-lookup"><span data-stu-id="83e9f-118">**send**</span></span>  
 <span data-ttu-id="83e9f-119">Automaticky posílá do Microsoftu zprávy o vnitřních chybách kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="83e9f-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="83e9f-120">Chcete-li tuto možnost povolte, musíte nejdříve souhlasit s zásady shromažďování údajů společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="83e9f-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="83e9f-121">Když se poprvé zadáte **- errorreport: Odeslat** na počítači, bude zpráva kompilátoru odkazovat na web, který obsahuje zásady sběru dat společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="83e9f-121">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
    
## <a name="remarks"></a><span data-ttu-id="83e9f-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83e9f-122">Remarks</span></span>  
 <span data-ttu-id="83e9f-123">Vnitřní chyba kompilátoru (ICE) výsledky, když kompilátor nemůže zpracovat soubor zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="83e9f-123">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="83e9f-124">Pokud dojde k ICE, kompilátor nevytvoří výstupní soubor nebo užitečnou diagnostiku, která můžete použít jak kód opravit.</span><span class="sxs-lookup"><span data-stu-id="83e9f-124">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="83e9f-125">V předchozích verzích při přijetí ICE jste vyzkoušeli Kontaktujte Microsoft Product Support Services nahlásit problém.</span><span class="sxs-lookup"><span data-stu-id="83e9f-125">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="83e9f-126">S použitím **- errorreport**, můžete zadat informace o ICE týmu Visual C#.</span><span class="sxs-lookup"><span data-stu-id="83e9f-126">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="83e9f-127">Zprávy o chybách můžete zvýšit kompilátoru budoucích verzí.</span><span class="sxs-lookup"><span data-stu-id="83e9f-127">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="83e9f-128">Uživatele umožňuje odeslat sestavy závisí na oprávnění zásad počítače a uživatele.</span><span class="sxs-lookup"><span data-stu-id="83e9f-128">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="83e9f-129">Další informace o ladění chyb, naleznete v tématu [Popis zotavení po havárii. Nástroje Watson pro Windows (Drwtsn32.exe)](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span><span class="sxs-lookup"><span data-stu-id="83e9f-129">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="83e9f-130">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83e9f-130">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="83e9f-131">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="83e9f-131">Open the project's **Properties** page.</span></span> <span data-ttu-id="83e9f-132">Další informace najdete v tématu [stránku sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="83e9f-132">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="83e9f-133">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="83e9f-133">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="83e9f-134">Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="83e9f-134">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="83e9f-135">Upravit **hlášení vnitřních chyb kompilátoru** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="83e9f-135">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="83e9f-136">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="83e9f-136">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e9f-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83e9f-137">See also</span></span>

- [<span data-ttu-id="83e9f-138">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="83e9f-138">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
