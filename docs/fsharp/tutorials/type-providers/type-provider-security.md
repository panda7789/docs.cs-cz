---
title: Zabezpečení zprostředkovatele typů
description: 'Další informace o zabezpečení zprostředkovatele typů v jazyce F #, včetně toho, jak chcete-li změnit nastavení vztahu důvěryhodnosti pro zprostředkovatele typů.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4f0b55062aec6c560112fe10ca4df77f42493011
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="type-provider-security"></a><span data-ttu-id="eb670-103">Zabezpečení zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="eb670-103">Type Provider Security</span></span>

<span data-ttu-id="eb670-104">Zprostředkovatelé typů jsou sestavení (DLL) odkazuje F # projektu nebo skriptu obsahující kód k připojení k externím zdrojům dat a prezentovat informace o typu prostředí typ F #.</span><span class="sxs-lookup"><span data-stu-id="eb670-104">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="eb670-105">Kód v odkazovaných sestaveních je obvykle spustit pouze při kompilaci a potom spusťte kód (nebo v případě skriptu poslat kód F # interaktivní).</span><span class="sxs-lookup"><span data-stu-id="eb670-105">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="eb670-106">Sestavení zprostředkovatele typ však bude fungovat v sadě Visual Studio, při procházení kódu jenom v editoru.</span><span class="sxs-lookup"><span data-stu-id="eb670-106">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="eb670-107">K tomu dochází, protože typ zprostředkovatele musí spustit a přidat doplňující informace do editoru, jako je například popisy tlačítek rychlé informace, dokončování IntelliSense a tak dále.</span><span class="sxs-lookup"><span data-stu-id="eb670-107">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="eb670-108">V důsledku toho existují další bezpečnostní aspekty pro typ sestavení zprostředkovatele, vzhledem k tomu, že budou automaticky spustit uvnitř proces sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb670-108">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="eb670-109">Dialogové okno upozornění zabezpečení</span><span class="sxs-lookup"><span data-stu-id="eb670-109">Security Warning Dialog</span></span>
<span data-ttu-id="eb670-110">Při prvním použití sestavení zprostředkovatele konkrétní typ, Visual Studio zobrazí dialogové okno zabezpečení, které vás varuje, že typ zprostředkovatele je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="eb670-110">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="eb670-111">Předtím, než Visual Studio načítá typu poskytovatele, nabízí možnost rozhodnout, zda důvěřovat tohoto konkrétního zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="eb670-111">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="eb670-112">Pokud považujete zdroj typ zprostředkovatele, pak vyberte "Důvěřuji tohoto typu zprostředkovatele."</span><span class="sxs-lookup"><span data-stu-id="eb670-112">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="eb670-113">Pokud nedůvěřujete zdroji typ zprostředkovatele, pak vyberte "I možnost nedůvěřujete tohoto typu zprostředkovatele."</span><span class="sxs-lookup"><span data-stu-id="eb670-113">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="eb670-114">Důvěřující zprostředkovatel umožňuje ho spustit v prostředí Visual Studio a poskytovat technologii IntelliSense a sestavení funkce.</span><span class="sxs-lookup"><span data-stu-id="eb670-114">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="eb670-115">Ale pokud typ samotné se zlými úmysly, spuštění jeho kódu by mohly ohrozit váš počítač.</span><span class="sxs-lookup"><span data-stu-id="eb670-115">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="eb670-116">Pokud projekt obsahuje kód, který odkazuje na typ zprostředkovatele, které jste zvolili v dialogu není pro vztah důvěryhodnosti, pak při kompilaci, kompilátor nahlásí chybu, která označuje, že je zprostředkovatel typu nedůvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="eb670-116">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="eb670-117">Všechny typy, které jsou závislé na poskytovateli nedůvěryhodné typu jsou označeny červenou podtržení vlnovkou.</span><span class="sxs-lookup"><span data-stu-id="eb670-117">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="eb670-118">Je bezpečné procházet kód v editoru.</span><span class="sxs-lookup"><span data-stu-id="eb670-118">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="eb670-119">Pokud se rozhodnete změnit nastavení důvěryhodnosti přímo v sadě Visual Studio, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="eb670-119">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="eb670-120">Chcete-li změnit nastavení vztahu důvěryhodnosti pro zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="eb670-120">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="eb670-121">Na `Tools` nabídce vyberte možnost `Options`a rozbalte `F# Tools` uzlu.</span><span class="sxs-lookup"><span data-stu-id="eb670-121">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="eb670-122">Vyberte `Type Providers`a v seznamu zprostředkovatelů typů, zaškrtněte políčko pro typ zprostředkovatele důvěřujete a zrušte zaškrtnutí políčka u uživatelů, kterým nedůvěřujete.</span><span class="sxs-lookup"><span data-stu-id="eb670-122">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="eb670-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb670-123">See Also</span></span>
[<span data-ttu-id="eb670-124">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="eb670-124">Type Providers</span></span>](index.md)
