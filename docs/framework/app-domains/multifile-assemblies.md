---
title: Vícesouborová sestavení
description: Použijte vícesouborové sestavení, která cílí na rozhraní .NET pomocí kompilátorů příkazového řádku nebo sady Visual Studio s Visual C++. Soubor v sestavení musí obsahovat manifest sestavení.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: a5fb41b3b136a325e6b8658da521cba3176e929f
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104634"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="f3dba-104">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="f3dba-104">Multifile assemblies</span></span>

<span data-ttu-id="f3dba-105">Můžete vytvořit vícesouborové sestavení, která cílí na .NET Framework pomocí kompilátorů příkazového řádku nebo sady Visual Studio s Visual C++.</span><span class="sxs-lookup"><span data-stu-id="f3dba-105">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="f3dba-106">Jeden soubor v sestavení musí obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3dba-106">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="f3dba-107">Sestavení, které spustí aplikaci, musí také obsahovat vstupní bod, například `Main` `WinMain` metodu nebo.</span><span class="sxs-lookup"><span data-stu-id="f3dba-107">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="f3dba-108">Předpokládejme například, že máte aplikaci, která obsahuje dva kódové moduly, *Client.cs* a *Stringer.cs*.</span><span class="sxs-lookup"><span data-stu-id="f3dba-108">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="f3dba-109">*Stringer.cs* vytvoří `myStringer` obor názvů, na který se odkazuje v kódu v *Client.cs*.</span><span class="sxs-lookup"><span data-stu-id="f3dba-109">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="f3dba-110">*Client.cs* obsahuje `Main` metodu, která je vstupním bodem aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3dba-110">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="f3dba-111">V tomto příkladu kompilujete dva kódové moduly a pak vytvoříte třetí soubor, který obsahuje manifest sestavení, který spouští aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f3dba-111">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="f3dba-112">Manifest sestavení odkazuje jak na moduly *klienta* , tak pro *Stringer* .</span><span class="sxs-lookup"><span data-stu-id="f3dba-112">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="f3dba-113">Vícesouborové sestavení může mít pouze jeden vstupní bod, a to i v případě, že sestavení má více kódových modulů.</span><span class="sxs-lookup"><span data-stu-id="f3dba-113">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="f3dba-114">Existuje několik důvodů, proč je vhodné vytvořit vícesouborové sestavení:</span><span class="sxs-lookup"><span data-stu-id="f3dba-114">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="f3dba-115">Pro kombinování modulů napsaných v různých jazycích.</span><span class="sxs-lookup"><span data-stu-id="f3dba-115">To combine modules written in different languages.</span></span> <span data-ttu-id="f3dba-116">Toto je nejběžnější důvod pro vytvoření vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3dba-116">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="f3dba-117">Chcete-li optimalizovat stahování aplikace v modulu, který je stažen pouze v případě potřeby, a to pomocí zřídka používaných typů.</span><span class="sxs-lookup"><span data-stu-id="f3dba-117">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f3dba-118">Pokud vytváříte aplikace, které budou staženy pomocí `<object>` značky v aplikaci Microsoft Internet Explorer, je důležité vytvořit vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3dba-118">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="f3dba-119">V tomto scénáři vytvoříte soubor oddělený od modulů kódu, který obsahuje pouze manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3dba-119">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="f3dba-120">Internet Explorer nejprve stáhne manifest sestavení a poté vytvoří pracovní vlákna ke stažení jakýchkoli dalších modulů nebo sestavení potřebných pro.</span><span class="sxs-lookup"><span data-stu-id="f3dba-120">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="f3dba-121">Při stahování souboru obsahujícího manifest sestavení přestane Internet Explorer reagovat na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="f3dba-121">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="f3dba-122">Menší soubor, který obsahuje manifest sestavení, méně času přestane Internet Explorer reagovat.</span><span class="sxs-lookup"><span data-stu-id="f3dba-122">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="f3dba-123">Pro kombinování kódových modulů napsaných několika vývojáři.</span><span class="sxs-lookup"><span data-stu-id="f3dba-123">To combine code modules written by several developers.</span></span> <span data-ttu-id="f3dba-124">I když každý z vývojářů může kompilovat modul kódu do sestavení, může to vynutit, aby některé typy byly veřejně vystaveny, které nejsou vystaveny, pokud jsou všechny moduly vloženy do vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3dba-124">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="f3dba-125">Po vytvoření sestavení můžete podepsat soubor, který obsahuje manifest sestavení, a sestavení, nebo můžete soubor a sestavení přidělit silný název a vložit je do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="f3dba-125">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3dba-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3dba-126">See also</span></span>

- [<span data-ttu-id="f3dba-127">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="f3dba-127">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="f3dba-128">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="f3dba-128">Program with assemblies</span></span>](../../standard/assembly/index.md)
