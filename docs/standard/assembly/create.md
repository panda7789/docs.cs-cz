---
title: Vytváření sestavení
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 8a00784e6aa2d663c738339367b4076e79ed9c95
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122490"
---
# <a name="create-assemblies"></a><span data-ttu-id="9fd53-102">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="9fd53-102">Create assemblies</span></span>

<span data-ttu-id="9fd53-103">Můžete vytvořit jednosouborové nebo vícesouborové sestavení pomocí integrovaného vývojového prostředí (IDE), jako je například Visual Studio, nebo kompilátorů a nástrojů poskytovaných Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="9fd53-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="9fd53-104">Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načten do jedné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9fd53-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="9fd53-105">Na toto sestavení nemůže odkazovat jiná sestavení mimo adresář aplikace a neprovádí kontrolu verze.</span><span class="sxs-lookup"><span data-stu-id="9fd53-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="9fd53-106">Chcete-li odinstalovat aplikaci tvořenou sestavením, stačí odstranit adresář, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="9fd53-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="9fd53-107">Pro mnoho vývojářů je sestavení s těmito funkcemi všechno, co je potřeba k nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="9fd53-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="9fd53-108">Můžete vytvořit vícesouborové sestavení z několika modulů kódu a souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="9fd53-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="9fd53-109">Můžete také vytvořit sestavení, které může být sdíleno více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="9fd53-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="9fd53-110">Sdílené sestavení musí mít silný název a může být nasazeno v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9fd53-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="9fd53-111">Máte několik možností, jak seskupit moduly kódu a prostředky do sestavení, v závislosti na následujících faktorech:</span><span class="sxs-lookup"><span data-stu-id="9fd53-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="9fd53-112">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="9fd53-112">Versioning</span></span>

     <span data-ttu-id="9fd53-113">Seskupujte moduly, které by měly mít stejné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="9fd53-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="9fd53-114">Nasazení</span><span class="sxs-lookup"><span data-stu-id="9fd53-114">Deployment</span></span>

     <span data-ttu-id="9fd53-115">Seskupuje moduly a prostředky kódu, které podporují váš model nasazení.</span><span class="sxs-lookup"><span data-stu-id="9fd53-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="9fd53-116">Opakovan</span><span class="sxs-lookup"><span data-stu-id="9fd53-116">Reuse</span></span>

     <span data-ttu-id="9fd53-117">Skupinové moduly, pokud je lze logicky používat pro určitý účel.</span><span class="sxs-lookup"><span data-stu-id="9fd53-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="9fd53-118">Například sestavení sestávající z typů a tříd, které jsou používány zřídka pro údržbu programu, lze umístit do stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="9fd53-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="9fd53-119">Kromě toho musí být typy, které chcete sdílet s více aplikacemi, seskupeny do sestavení a sestavení by mělo být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9fd53-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="9fd53-120">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9fd53-120">Security</span></span>

     <span data-ttu-id="9fd53-121">Moduly skupin obsahující typy, které vyžadují stejná oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9fd53-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="9fd53-122">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9fd53-122">Scoping</span></span>

     <span data-ttu-id="9fd53-123">Moduly skupin obsahující typy, jejichž viditelnost by měly být omezeny na stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="9fd53-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="9fd53-124">Existují zvláštní předpoklady pro zpřístupnění sestavení společného jazykového modulu runtime pro nespravované aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9fd53-124">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="9fd53-125">Další informace o práci s nespravovaným kódem naleznete v tématu [Vystavení .NET Frameworkch komponent modelu COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="9fd53-125">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fd53-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fd53-126">See also</span></span>

- [<span data-ttu-id="9fd53-127">Program se sestaveními</span><span class="sxs-lookup"><span data-stu-id="9fd53-127">Program with assemblies</span></span>](program.md)
- [<span data-ttu-id="9fd53-128">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="9fd53-128">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="9fd53-129">Postupy: sestavení sestavení s jedním souborem</span><span class="sxs-lookup"><span data-stu-id="9fd53-129">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="9fd53-130">Postupy: sestavení vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="9fd53-130">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="9fd53-131">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="9fd53-131">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="9fd53-132">Vícesouborové sestavení</span><span class="sxs-lookup"><span data-stu-id="9fd53-132">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
