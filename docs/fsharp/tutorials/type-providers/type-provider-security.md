---
title: "Zabezpečení zprostředkovatele typů"
description: "Další informace o zabezpečení zprostředkovatele typů v jazyce F #, včetně toho, jak chcete-li změnit nastavení vztahu důvěryhodnosti pro zprostředkovatele typů."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a><span data-ttu-id="e03ba-104">Zabezpečení zprostředkovatele typů</span><span class="sxs-lookup"><span data-stu-id="e03ba-104">Type Provider Security</span></span>

<span data-ttu-id="e03ba-105">Zprostředkovatelé typů jsou sestavení (DLL) odkazuje F # projektu nebo skriptu obsahující kód k připojení k externím zdrojům dat a prezentovat informace o typu prostředí typ F #.</span><span class="sxs-lookup"><span data-stu-id="e03ba-105">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="e03ba-106">Kód v odkazovaných sestaveních je obvykle spustit pouze při kompilaci a potom spusťte kód (nebo v případě skriptu poslat kód F # interaktivní).</span><span class="sxs-lookup"><span data-stu-id="e03ba-106">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="e03ba-107">Sestavení zprostředkovatele typ však bude fungovat v sadě Visual Studio, při procházení kódu jenom v editoru.</span><span class="sxs-lookup"><span data-stu-id="e03ba-107">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="e03ba-108">K tomu dochází, protože typ zprostředkovatele musí spustit a přidat doplňující informace do editoru, jako je například popisy tlačítek rychlé informace, dokončování IntelliSense a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e03ba-108">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="e03ba-109">V důsledku toho existují další bezpečnostní aspekty pro typ sestavení zprostředkovatele, vzhledem k tomu, že budou automaticky spustit uvnitř proces sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e03ba-109">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="e03ba-110">Dialogové okno upozornění zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e03ba-110">Security Warning Dialog</span></span>
<span data-ttu-id="e03ba-111">Při prvním použití sestavení zprostředkovatele konkrétní typ, Visual Studio zobrazí dialogové okno zabezpečení, které vás varuje, že typ zprostředkovatele je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="e03ba-111">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="e03ba-112">Předtím, než Visual Studio načítá typu poskytovatele, nabízí možnost rozhodnout, zda důvěřovat tohoto konkrétního zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="e03ba-112">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="e03ba-113">Pokud považujete zdroj typ zprostředkovatele, pak vyberte "Důvěřuji tohoto typu zprostředkovatele."</span><span class="sxs-lookup"><span data-stu-id="e03ba-113">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="e03ba-114">Pokud nedůvěřujete zdroji typ zprostředkovatele, pak vyberte "I možnost nedůvěřujete tohoto typu zprostředkovatele."</span><span class="sxs-lookup"><span data-stu-id="e03ba-114">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="e03ba-115">Důvěřující zprostředkovatel umožňuje ho spustit v prostředí Visual Studio a poskytovat technologii IntelliSense a sestavení funkce.</span><span class="sxs-lookup"><span data-stu-id="e03ba-115">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="e03ba-116">Ale pokud typ samotné se zlými úmysly, spuštění jeho kódu by mohly ohrozit váš počítač.</span><span class="sxs-lookup"><span data-stu-id="e03ba-116">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="e03ba-117">Pokud projekt obsahuje kód, který odkazuje na typ zprostředkovatele, které jste zvolili v dialogu není pro vztah důvěryhodnosti, pak při kompilaci, kompilátor nahlásí chybu, která označuje, že je zprostředkovatel typu nedůvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="e03ba-117">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="e03ba-118">Všechny typy, které jsou závislé na poskytovateli nedůvěryhodné typu jsou označeny červenou podtržení vlnovkou.</span><span class="sxs-lookup"><span data-stu-id="e03ba-118">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="e03ba-119">Je bezpečné procházet kód v editoru.</span><span class="sxs-lookup"><span data-stu-id="e03ba-119">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="e03ba-120">Pokud se rozhodnete změnit nastavení důvěryhodnosti přímo v sadě Visual Studio, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="e03ba-120">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="e03ba-121">Chcete-li změnit nastavení vztahu důvěryhodnosti pro zprostředkovatelů typů</span><span class="sxs-lookup"><span data-stu-id="e03ba-121">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="e03ba-122">Na `Tools` nabídce vyberte možnost `Options`a rozbalte `F# Tools` uzlu.</span><span class="sxs-lookup"><span data-stu-id="e03ba-122">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="e03ba-123">Vyberte `Type Providers`a v seznamu zprostředkovatelů typů, zaškrtněte políčko pro typ zprostředkovatele důvěřujete a zrušte zaškrtnutí políčka u uživatelů, kterým nedůvěřujete.</span><span class="sxs-lookup"><span data-stu-id="e03ba-123">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="e03ba-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e03ba-124">See Also</span></span>
[<span data-ttu-id="e03ba-125">Zprostředkovatelé typů</span><span class="sxs-lookup"><span data-stu-id="e03ba-125">Type Providers</span></span>](index.md)
