---
title: -errorreport (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253882"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="b8d22-102">-errorreport (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="b8d22-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="b8d22-103">Tato možnost nabízí pohodlný způsob, jak hlásit C# vnitřní chybu kompilátoru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b8d22-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="b8d22-104">V systémech Windows Vista a Windows Server 2008 nastavení zasílání zpráv o chybách, která uděláte pro Visual Studio, nepřepisují nastavení vytvořená prostřednictvím služby Zasílání zpráv o chybách systému Windows (WER).</span><span class="sxs-lookup"><span data-stu-id="b8d22-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="b8d22-105">Nastavení funkce WER vždycky mají přednost před nastavením zasílání zpráv o chybách sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8d22-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8d22-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8d22-106">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="b8d22-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="b8d22-107">Arguments</span></span>
 <span data-ttu-id="b8d22-108">**nTato**</span><span class="sxs-lookup"><span data-stu-id="b8d22-108">**none**</span></span>  
 <span data-ttu-id="b8d22-109">Zprávy o vnitřních chybách kompilátoru nebudou shromažďovány ani odesílány společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b8d22-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="b8d22-110">**Zobrazit výzvu** Vyzve vás k odeslání sestavy, když dojde k vnitřní chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b8d22-110">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="b8d22-111">při kompilaci aplikace ve vývojovém prostředí se **zobrazí dotaz** na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8d22-111">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="b8d22-112">**fronta** Zařadí do fronty zprávu o chybách.</span><span class="sxs-lookup"><span data-stu-id="b8d22-112">**queue** Queues the error report.</span></span> <span data-ttu-id="b8d22-113">Když se přihlásíte s přihlašovacími údaji správce, můžete nahlásit všechny chyby od posledního přihlášení.</span><span class="sxs-lookup"><span data-stu-id="b8d22-113">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="b8d22-114">Nebudete vyzváni k odeslání zpráv o selhání více než jednou za tři dny.</span><span class="sxs-lookup"><span data-stu-id="b8d22-114">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="b8d22-115">při kompilaci aplikace na příkazovém řádku je **fronta** výchozí.</span><span class="sxs-lookup"><span data-stu-id="b8d22-115">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="b8d22-116">**Odeslat** Automaticky odesílá zprávy o vnitřních chybách kompilátoru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b8d22-116">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="b8d22-117">Pokud chcete povolit tuto možnost, musíte nejdřív souhlasit se zásadou pro shromažďování dat Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="b8d22-117">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="b8d22-118">Při prvním zadání **– errorreport: Send** v počítači, zpráva kompilátoru vás bude odkazovat na web, který obsahuje zásadu shromažďování dat společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b8d22-118">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8d22-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8d22-119">Remarks</span></span>
 <span data-ttu-id="b8d22-120">Vnitřní chyba kompilátoru (ICE) má za následek, že kompilátor nemůže zpracovat soubor zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="b8d22-120">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="b8d22-121">Když dojde k ICE, kompilátor nevytvoří výstupní soubor nebo žádnou užitečnou diagnostiku, kterou můžete použít k opravě kódu.</span><span class="sxs-lookup"><span data-stu-id="b8d22-121">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="b8d22-122">Pokud jste v předchozích verzích obdrželi ICE, doporučujeme kontaktovat oddělení služeb technické podpory společnosti Microsoft, aby nahlásila problém.</span><span class="sxs-lookup"><span data-stu-id="b8d22-122">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="b8d22-123">Pomocí **-errorreport**můžete zadat informace o ICE pro vizuální C# tým.</span><span class="sxs-lookup"><span data-stu-id="b8d22-123">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="b8d22-124">Vaše zprávy o chybách mohou pomoci vylepšit budoucí verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b8d22-124">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="b8d22-125">Schopnost uživatele odesílat sestavy závisí na oprávněních pro počítače a uživatele.</span><span class="sxs-lookup"><span data-stu-id="b8d22-125">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b8d22-126">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8d22-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="b8d22-127">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="b8d22-127">Open the project's **Properties** page.</span></span> <span data-ttu-id="b8d22-128">Další informace naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="b8d22-128">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="b8d22-129">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="b8d22-129">Click the **Build** property page.</span></span>

3. <span data-ttu-id="b8d22-130">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="b8d22-130">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="b8d22-131">Upravte vlastnost **interního zasílání zpráv o chybách kompilátoru** .</span><span class="sxs-lookup"><span data-stu-id="b8d22-131">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="b8d22-132">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="b8d22-132">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8d22-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8d22-133">See also</span></span>

- [<span data-ttu-id="b8d22-134">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b8d22-134">C# Compiler Options</span></span>](./index.md)
