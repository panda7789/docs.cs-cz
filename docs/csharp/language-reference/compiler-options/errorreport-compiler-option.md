---
title: -errorreport (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253882"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="41865-102">-errorreport (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="41865-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="41865-103">Tato možnost poskytuje pohodlný způsob, jak nahlásit chybu interního kompilátoru jazyka C# společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="41865-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="41865-104">V systémech Windows Vista a Windows Server 2008 nastavení zasílání zpráv o chybách, která provedete pro aplikaci Visual Studio, nepřepíší nastavení provedená prostřednictvím systému Windows Error Reporting (WER).</span><span class="sxs-lookup"><span data-stu-id="41865-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="41865-105">Nastavení WER má vždy přednost před nastavením zasílání zpráv o chybách sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41865-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="41865-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41865-106">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="41865-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="41865-107">Arguments</span></span>
 <span data-ttu-id="41865-108">**žádný**</span><span class="sxs-lookup"><span data-stu-id="41865-108">**none**</span></span>  
 <span data-ttu-id="41865-109">Zprávy o interních chybách kompilátoru nebudou shromažďovány ani odesílány společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="41865-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="41865-110">**výzva** Zobrazí výzvu k odeslání sestavy, když se zobrazí vnitřní chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="41865-110">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="41865-111">**výzva** je výchozí při kompilaci aplikace ve vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="41865-111">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="41865-112">**fronta** Zařadí zprávu o chybě do fronty.</span><span class="sxs-lookup"><span data-stu-id="41865-112">**queue** Queues the error report.</span></span> <span data-ttu-id="41865-113">Při přihlášení pomocí pověření pro správu můžete hlásit všechny chyby od posledního přihlášení.</span><span class="sxs-lookup"><span data-stu-id="41865-113">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="41865-114">Nebudete vyzváni k odesílání zpráv o selhání více než jednou za tři dny.</span><span class="sxs-lookup"><span data-stu-id="41865-114">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="41865-115">**fronta** je výchozí při kompilaci aplikace na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="41865-115">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="41865-116">**odeslat** Automaticky odesílá zprávy o interních chybách kompilátoru společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="41865-116">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="41865-117">Chcete-li tuto možnost povolit, musíte nejprve souhlasit se zásadami shromažďování dat společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="41865-117">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="41865-118">Při prvním zadání **-errorreport:send** v počítači vás zpráva kompilátoru přejde na web, který obsahuje zásady shromažďování dat společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="41865-118">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="41865-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41865-119">Remarks</span></span>
 <span data-ttu-id="41865-120">Vnitřní chyba kompilátoru (ICE) je výsledkem, když kompilátor nemůže zpracovat soubor zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="41865-120">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="41865-121">Dojde-li ICE, kompilátor nevytváří výstupní soubor nebo užitečnou diagnostiku, kterou můžete použít k opravě kódu.</span><span class="sxs-lookup"><span data-stu-id="41865-121">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="41865-122">V předchozích verzích, když jste obdrželi ICE, byli jste vyzváni, abyste se obrátili na služby odborné pomoci společnosti Microsoft a nahlásili problém.</span><span class="sxs-lookup"><span data-stu-id="41865-122">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="41865-123">Pomocí **-errorreport**můžete poskytnout ice informace týmu Visual C#.</span><span class="sxs-lookup"><span data-stu-id="41865-123">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="41865-124">Vaše zprávy o chybách mohou pomoci zlepšit budoucí verze kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="41865-124">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="41865-125">Možnost uživatele odesílat sestavy závisí na oprávněních zásad počítače a uživatele.</span><span class="sxs-lookup"><span data-stu-id="41865-125">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="41865-126">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="41865-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="41865-127">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="41865-127">Open the project's **Properties** page.</span></span> <span data-ttu-id="41865-128">Další informace naleznete v [tématu Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="41865-128">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="41865-129">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="41865-129">Click the **Build** property page.</span></span>

3. <span data-ttu-id="41865-130">Klepněte na tlačítko **Upřesnit.**</span><span class="sxs-lookup"><span data-stu-id="41865-130">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="41865-131">Upravte vlastnost **Interní zasílání zpráv o chybách kompilátoru.**</span><span class="sxs-lookup"><span data-stu-id="41865-131">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="41865-132">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="41865-132">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="41865-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="41865-133">See also</span></span>

- [<span data-ttu-id="41865-134">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="41865-134">C# Compiler Options</span></span>](./index.md)
