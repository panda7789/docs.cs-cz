---
title: Vytváření sestavení
description: Naučte se vytvářet jednosouborové nebo vícesouborové sestavení pomocí integrovaného vývojového prostředí (IDE), jako je například Visual Studio, nebo kompilátorů a nástrojů poskytovaných Windows SDK.
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 3e17d6a066d937a161135b8b03c3f9258f3586b0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378509"
---
# <a name="create-assemblies"></a><span data-ttu-id="d5aa7-103">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="d5aa7-103">Create assemblies</span></span>

<span data-ttu-id="d5aa7-104">Můžete vytvořit jednosouborové nebo vícesouborové sestavení pomocí integrovaného vývojového prostředí (IDE), jako je například Visual Studio, nebo kompilátorů a nástrojů poskytovaných Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-104">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="d5aa7-105">Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načten do jedné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-105">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="d5aa7-106">Na toto sestavení nemůže odkazovat jiná sestavení mimo adresář aplikace a neprovádí kontrolu verze.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-106">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="d5aa7-107">Chcete-li odinstalovat aplikaci tvořenou sestavením, stačí odstranit adresář, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-107">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="d5aa7-108">Pro mnoho vývojářů je sestavení s těmito funkcemi všechno, co je potřeba k nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-108">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="d5aa7-109">Můžete vytvořit vícesouborové sestavení z několika modulů kódu a souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-109">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="d5aa7-110">Můžete také vytvořit sestavení, které může být sdíleno více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-110">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="d5aa7-111">Sdílené sestavení musí mít silný název a může být nasazeno v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="d5aa7-111">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="d5aa7-112">Máte několik možností, jak seskupit moduly kódu a prostředky do sestavení, v závislosti na následujících faktorech:</span><span class="sxs-lookup"><span data-stu-id="d5aa7-112">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="d5aa7-113">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="d5aa7-113">Versioning</span></span>

     <span data-ttu-id="d5aa7-114">Seskupujte moduly, které by měly mít stejné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-114">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="d5aa7-115">Nasazení</span><span class="sxs-lookup"><span data-stu-id="d5aa7-115">Deployment</span></span>

     <span data-ttu-id="d5aa7-116">Seskupuje moduly a prostředky kódu, které podporují váš model nasazení.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-116">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="d5aa7-117">Opakované použití</span><span class="sxs-lookup"><span data-stu-id="d5aa7-117">Reuse</span></span>

     <span data-ttu-id="d5aa7-118">Skupinové moduly, pokud je lze logicky používat pro určitý účel.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-118">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="d5aa7-119">Například sestavení sestávající z typů a tříd, které jsou používány zřídka pro údržbu programu, lze umístit do stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-119">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="d5aa7-120">Kromě toho musí být typy, které chcete sdílet s více aplikacemi, seskupeny do sestavení a sestavení by mělo být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-120">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="d5aa7-121">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d5aa7-121">Security</span></span>

     <span data-ttu-id="d5aa7-122">Moduly skupin obsahující typy, které vyžadují stejná oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-122">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="d5aa7-123">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d5aa7-123">Scoping</span></span>

     <span data-ttu-id="d5aa7-124">Moduly skupin obsahující typy, jejichž viditelnost by měly být omezeny na stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-124">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="d5aa7-125">Existují zvláštní předpoklady pro zpřístupnění sestavení společného jazykového modulu runtime pro nespravované aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d5aa7-125">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="d5aa7-126">Další informace o práci s nespravovaným kódem naleznete v tématu [Vystavení .NET Frameworkch komponent modelu COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="d5aa7-126">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5aa7-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5aa7-127">See also</span></span>

- [<span data-ttu-id="d5aa7-128">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="d5aa7-128">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="d5aa7-129">Postupy: Vytváření sestavení s jediným souborem</span><span class="sxs-lookup"><span data-stu-id="d5aa7-129">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="d5aa7-130">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="d5aa7-130">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="d5aa7-131">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="d5aa7-131">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d5aa7-132">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="d5aa7-132">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
