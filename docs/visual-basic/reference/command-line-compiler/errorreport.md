---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: c8e193a8cb4d4dbc7515c32139bad9dce8b48ed7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005617"
---
# <a name="-errorreport"></a><span data-ttu-id="a4f7a-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="a4f7a-102">-errorreport</span></span>

<span data-ttu-id="a4f7a-103">Určuje, jak by měl kompilátor Visual Basic hlásit vnitřní chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4f7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4f7a-104">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="a4f7a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4f7a-105">Remarks</span></span>

<span data-ttu-id="a4f7a-106">Tato možnost poskytuje pohodlný způsob, jak ohlásit Visual Basic vnitřní chybu kompilátoru (ICE) týmu Visual Basic v Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="a4f7a-107">Ve výchozím nastavení kompilátor neodesílá společnosti Microsoft žádné informace.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="a4f7a-108">Pokud ale dojde k vnitřní chybě kompilátoru, tato možnost vám umožní ohlásit chybu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="a4f7a-109">Tyto informace pomohou technikům Microsoftu identifikovat příčinu a mohou vám pomoci vylepšit další vydání Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="a4f7a-110">Schopnost uživatele odesílat sestavy závisí na oprávněních pro počítače a uživatele.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="a4f7a-111">Následující tabulka shrnuje efekt možnosti `-errorreport`.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="a4f7a-112">Možnost</span><span class="sxs-lookup"><span data-stu-id="a4f7a-112">Option</span></span>|<span data-ttu-id="a4f7a-113">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="a4f7a-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="a4f7a-114">Pokud dojde k vnitřní chybě kompilátoru, zobrazí se dialogové okno, abyste mohli zobrazit přesná data, která kompilátor shromáždil.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="a4f7a-115">Můžete určit, jestli se v hlášení o chybách nacházejí nějaké citlivé informace, a rozhodnout se, jestli se má poslat Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="a4f7a-116">Pokud se rozhodnete ho odeslat a nastavení zásad počítače a uživatele ho povolí, kompilátor pošle data společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="a4f7a-117">Zařadí do fronty zprávu o chybách.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-117">Queues the error report.</span></span> <span data-ttu-id="a4f7a-118">Když se přihlásíte s oprávněními správce, můžete nahlásit všechny chyby od posledního přihlášení (nebudete vyzváni k odeslání zpráv o selhání více než jednou za tři dny).</span><span class="sxs-lookup"><span data-stu-id="a4f7a-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="a4f7a-119">Toto je výchozí chování, pokud není zadána možnost `-errorreport`.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="a4f7a-120">Pokud dojde k vnitřní chybě kompilátoru a nastavení zásad počítače a uživatele je povolí, kompilátor odesílá data společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="a4f7a-121">Možnost `-errorreport:send` se pokusí automaticky odeslat informace o chybě společnosti Microsoft, pokud je vytváření sestav povoleno nastavením [zasílání zpráv o chybách systému Windows](/windows/desktop/wer/windows-error-reporting) systému.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="a4f7a-122">Dojde-li k vnitřní chybě kompilátoru, nebude shromažďována ani odeslána společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="a4f7a-123">Kompilátor odesílá data, která zahrnují zásobník v době chyby, což obvykle zahrnuje nějaký zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="a4f7a-124">Pokud se `-errorreport` používá s možností [-bugreport –](../../../visual-basic/reference/command-line-compiler/bugreport.md) , pak se pošle celý zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="a4f7a-125">Tato možnost se nejlépe používá s možností [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) , protože umožňuje vývojářům Microsoftu snadněji reprodukování chyby.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-125">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="a4f7a-126">Možnost `-errorreport` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="a4f7a-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4f7a-127">Example</span></span>

<span data-ttu-id="a4f7a-128">Následující kód se pokusí zkompilovat `T2.vb` a pokud kompilátor narazí na vnitřní chybu kompilátoru, zobrazí výzvu k odeslání zprávy o chybách společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4f7a-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="a4f7a-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4f7a-129">See also</span></span>

- [<span data-ttu-id="a4f7a-130">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a4f7a-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a4f7a-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a4f7a-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="a4f7a-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="a4f7a-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
