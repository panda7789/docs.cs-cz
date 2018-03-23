---
title: -errorreport
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59dc833299161eac7b119e654c94534f202b1cb7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-errorreport"></a><span data-ttu-id="34899-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="34899-102">-errorreport</span></span>
<span data-ttu-id="34899-103">Určuje, jak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru by měl zprávy o chybách interní kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="34899-103">Specifies how the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34899-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34899-104">Syntax</span></span>  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="34899-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34899-105">Remarks</span></span>  
 <span data-ttu-id="34899-106">Tato možnost nabízí pohodlný způsob, jak sestavu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vnitřní chyba kompilátoru (LED) k [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] týmu ve společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34899-106">This option provides a convenient way to report a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] internal compiler error (ICE) to the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] team at Microsoft.</span></span> <span data-ttu-id="34899-107">Ve výchozím nastavení kompilátoru odešle žádné informace společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34899-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="34899-108">Ale pokud dojde k chybě vnitřní kompilátoru, tato možnost umožňuje společnosti Microsoft zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="34899-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="34899-109">Tyto informace vám pomohou určit příčinu pracovníci společnosti Microsoft a může pomoct zlepšit další verzi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34899-109">That information will help Microsoft engineers identify the cause and may help improve the next release of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="34899-110">Schopnost uživatele odesílat zprávy závisí na oprávnění zásad počítače a uživatele.</span><span class="sxs-lookup"><span data-stu-id="34899-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="34899-111">Následující tabulka shrnuje účinku `-errorreport` možnost.</span><span class="sxs-lookup"><span data-stu-id="34899-111">The following table summarizes the effect of the `-errorreport` option.</span></span>  
  
|<span data-ttu-id="34899-112">Možnost</span><span class="sxs-lookup"><span data-stu-id="34899-112">Option</span></span>|<span data-ttu-id="34899-113">Chování</span><span class="sxs-lookup"><span data-stu-id="34899-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="34899-114">Pokud dojde k chybě vnitřní kompilátoru, dialogové okno se zobrazí tak, aby můžete zobrazit přesný data, která shromažďují kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="34899-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="34899-115">Můžete zjistit, jestli neexistuje žádné citlivé informace v chybové zprávě a provedení rozhodnutí na tom, zda je k odeslání společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34899-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="34899-116">Pokud se rozhodnete odeslat, a nastavení zásad počítače a uživatele, aby ji, kompilátor odešle data do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="34899-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="34899-117">Fronty zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="34899-117">Queues the error report.</span></span> <span data-ttu-id="34899-118">Když se přihlásíte pomocí oprávnění správce, můžete sestavu případných selhání od posledního byly přihlášení (nezobrazí se výzva k odeslání zpráv o selhání více než jednou za tři dní).</span><span class="sxs-lookup"><span data-stu-id="34899-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="34899-119">Toto je výchozí chování při `-errorreport` není určena možnost.</span><span class="sxs-lookup"><span data-stu-id="34899-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="34899-120">Pokud dojde k chybě vnitřní kompilátoru a nastavení zásad počítače a uživatele, aby ji, kompilátor odešle data do Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="34899-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="34899-121">Možnost `-errorreport:send` pokusí automaticky odesílat informace o chybách společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34899-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="34899-122">Tuto možnost, závisí na registru.</span><span class="sxs-lookup"><span data-stu-id="34899-122">This option depends on the registry.</span></span> <span data-ttu-id="34899-123">Další informace o nastavení na odpovídající hodnoty v registru najdete v tématu [jak zapnout automatické hlášení chyb v příkazového řádku nástroje sady Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).</span><span class="sxs-lookup"><span data-stu-id="34899-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="34899-124">Pokud dojde k chybě vnitřní kompilátoru, nebudou shromažďovány nebo odesílány do společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34899-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="34899-125">Kompilátor odešle data, která zahrnuje zásobníku v době chyby, která obvykle zahrnuje některé zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="34899-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="34899-126">Pokud `-errorreport` se používá s [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, pak je odeslán celý zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="34899-126">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="34899-127">Tato možnost je nejvhodnější pro [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) možnost, protože umožňuje snadno tomu chybu reprodukovat pracovníci společnosti Microsoft na informace.</span><span class="sxs-lookup"><span data-stu-id="34899-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34899-128">`-errorreport` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="34899-128">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34899-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="34899-129">Example</span></span>  
 <span data-ttu-id="34899-130">Následující kód pokusí zkompilovat `T2.vb`, a pokud kompilátor dojde k chybě vnitřní kompilátoru, budete vyzváni k odeslání zprávy o chybách společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34899-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="34899-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="34899-131">See Also</span></span>  
 [<span data-ttu-id="34899-132">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="34899-132">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="34899-133">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="34899-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="34899-134">-bugreport</span><span class="sxs-lookup"><span data-stu-id="34899-134">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
