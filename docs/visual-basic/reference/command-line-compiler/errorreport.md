---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: 5471f0783eee5e2c14cf0f140094d5c292a73756
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663255"
---
# <a name="-errorreport"></a><span data-ttu-id="34cde-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="34cde-102">-errorreport</span></span>

<span data-ttu-id="34cde-103">Určuje, jak by měl kompilátor jazyka Visual Basic ohlásit interní chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="34cde-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="34cde-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34cde-104">Syntax</span></span>

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="34cde-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34cde-105">Remarks</span></span>

<span data-ttu-id="34cde-106">Tato možnost poskytuje pohodlný způsob, jak sestavu jazyce Visual Basic vnitřní chyba kompilátoru (ICE) týmu Visual Basic v Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="34cde-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="34cde-107">Ve výchozím nastavení kompilátor odesílá žádné informace o společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34cde-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="34cde-108">Ale pokud narazíte na chybu kompilátoru, tato možnost umožňuje nahlásit chyby do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="34cde-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="34cde-109">Tyto informace vám pomohou určit příčinu odborníky z Microsoftu a může zvýšit následující verzi jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34cde-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="34cde-110">Uživatele umožňuje odeslat sestavy závisí na počítače a uživatelských oprávnění zásad.</span><span class="sxs-lookup"><span data-stu-id="34cde-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="34cde-111">Následující tabulka shrnuje vliv `-errorreport` možnost.</span><span class="sxs-lookup"><span data-stu-id="34cde-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="34cde-112">Možnost</span><span class="sxs-lookup"><span data-stu-id="34cde-112">Option</span></span>|<span data-ttu-id="34cde-113">Chování</span><span class="sxs-lookup"><span data-stu-id="34cde-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="34cde-114">Pokud dojde k chybě vnitřní kompilátor, dialogové okno se zobrazí tak, aby se zobrazí přesně ta data, která shromažďují kompilátor.</span><span class="sxs-lookup"><span data-stu-id="34cde-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="34cde-115">Můžete určit, jestli nejsou k dispozici žádné citlivé informace v chybové zprávě a rozhodnutí na tom, zda chcete odesílat společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34cde-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="34cde-116">Pokud se rozhodnete odeslat a povolit nastavení zásad počítače a uživatele, kompilátor odesílá data do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="34cde-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="34cde-117">Zařadí do fronty zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="34cde-117">Queues the error report.</span></span> <span data-ttu-id="34cde-118">Při přihlašování s použitím oprávnění správce, můžete nahlásit všechny chyby od posledního byly zaznamenány v (nezobrazí se výzva k odeslání zprávy o chybách více než jednou za tři dny).</span><span class="sxs-lookup"><span data-stu-id="34cde-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="34cde-119">Toto je výchozí chování při `-errorreport` možnost není zadána.</span><span class="sxs-lookup"><span data-stu-id="34cde-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="34cde-120">Pokud dojde k chybě vnitřního kompilátoru a nastavení zásad počítače a uživatele nepovoluje, kompilátor odesílá data do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="34cde-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="34cde-121">Možnost `-errorreport:send` pokusí automaticky odesílat informace o chybách společnosti Microsoft, pokud vytváření sestav je povoleno podle [zasílání zpráv o chybách Windows](/windows/desktop/wer/windows-error-reporting) nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="34cde-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="34cde-122">Pokud dojde k chybě vnitřní kompilátor, nebude shromážděné nebo odeslané společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34cde-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="34cde-123">Kompilátor odešle data, která zahrnuje zásobníku v době výskytu chyby, který obvykle obsahuje určitý zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="34cde-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="34cde-124">Pokud `-errorreport` se používá s [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, celý zdrojový soubor je odeslaný.</span><span class="sxs-lookup"><span data-stu-id="34cde-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="34cde-125">Tato možnost je vhodné použít v [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, protože umožňuje technikům Microsoftu informace snadno chybu reprodukovat.</span><span class="sxs-lookup"><span data-stu-id="34cde-125">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="34cde-126">`-errorreport` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="34cde-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="34cde-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="34cde-127">Example</span></span>

<span data-ttu-id="34cde-128">Následující kód se pokusí zkompilovat `T2.vb`, a pokud kompilátor narazí vnitřní chyba kompilátoru, vyzve vás k odeslání zprávy o chybách společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34cde-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="34cde-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34cde-129">See also</span></span>

- [<span data-ttu-id="34cde-130">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="34cde-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="34cde-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="34cde-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="34cde-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="34cde-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
