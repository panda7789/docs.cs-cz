---
title: Vytváření sestavení
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740516"
---
# <a name="create-assemblies"></a><span data-ttu-id="0a260-102">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="0a260-102">Create assemblies</span></span>

<span data-ttu-id="0a260-103">Můžete vytvořit jednosouborová nebo vícesouborová sestavení pomocí ide, jako je například Visual Studio, nebo kompilátory a nástroje poskytované sadou Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="0a260-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="0a260-104">Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načten do jedné domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a260-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="0a260-105">Toto sestavení nelze odkazovat jinými sestaveními mimo adresář aplikace a neprochází kontrolou verze.</span><span class="sxs-lookup"><span data-stu-id="0a260-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="0a260-106">Chcete-li odinstalovat aplikaci tvořenou sestavením, jednoduše odstraňte adresář, ve kterém je umístěn.</span><span class="sxs-lookup"><span data-stu-id="0a260-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="0a260-107">Pro mnoho vývojářů sestavení s těmito funkcemi je vše, co je potřeba k nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a260-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="0a260-108">Můžete vytvořit vícesouborové sestavení z několika modulů kódu a souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="0a260-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="0a260-109">Můžete také vytvořit sestavení, které může být sdíleno více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="0a260-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="0a260-110">Sdílené sestavení musí mít silný název a lze je nasadit v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a260-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="0a260-111">Máte několik možností při seskupování modulů kódu a prostředků do sestavení, v závislosti na následujících faktorech:</span><span class="sxs-lookup"><span data-stu-id="0a260-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="0a260-112">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="0a260-112">Versioning</span></span>

     <span data-ttu-id="0a260-113">Seskupit moduly, které by měly mít stejné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="0a260-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="0a260-114">Nasazení</span><span class="sxs-lookup"><span data-stu-id="0a260-114">Deployment</span></span>

     <span data-ttu-id="0a260-115">Moduly kódu skupiny a prostředky, které podporují váš model nasazení.</span><span class="sxs-lookup"><span data-stu-id="0a260-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="0a260-116">Opakované použití</span><span class="sxs-lookup"><span data-stu-id="0a260-116">Reuse</span></span>

     <span data-ttu-id="0a260-117">Seskupit moduly, pokud mohou být logicky použity společně pro nějaký účel.</span><span class="sxs-lookup"><span data-stu-id="0a260-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="0a260-118">Například sestavení skládající se z typů a tříd, které se používají zřídka pro údržbu programu, může být vloženo do stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a260-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="0a260-119">Kromě toho typy, které chcete sdílet s více aplikacemi by měly být seskupeny do sestavení a sestavení by měly být podepsány silným názvem.</span><span class="sxs-lookup"><span data-stu-id="0a260-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="0a260-120">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0a260-120">Security</span></span>

     <span data-ttu-id="0a260-121">Seskupte moduly obsahující typy, které vyžadují stejná oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0a260-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="0a260-122">Oboru</span><span class="sxs-lookup"><span data-stu-id="0a260-122">Scoping</span></span>

     <span data-ttu-id="0a260-123">Skupiny modulů obsahujících typy, jejichž viditelnost by měla být omezena na stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a260-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="0a260-124">Existují zvláštní aspekty při vytváření sestavení za běhu běžného jazyka pro nespravované aplikace COM.</span><span class="sxs-lookup"><span data-stu-id="0a260-124">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="0a260-125">Další informace o práci s nespravovaným kódem naleznete v [tématu Vystavit součásti rozhraní .NET Framework modelu COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="0a260-125">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a260-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a260-126">See also</span></span>

- [<span data-ttu-id="0a260-127">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="0a260-127">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="0a260-128">Postup: Sestavení sestavení s jedním souborem</span><span class="sxs-lookup"><span data-stu-id="0a260-128">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="0a260-129">Postup: Sestavení vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="0a260-129">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="0a260-130">Jak runtime vyhledá sestavení</span><span class="sxs-lookup"><span data-stu-id="0a260-130">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="0a260-131">Vícesouborná sestavení</span><span class="sxs-lookup"><span data-stu-id="0a260-131">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
