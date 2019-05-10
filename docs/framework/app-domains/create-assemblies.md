---
title: Vytváření sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 993c7f590f30b44f45e4833b4364b40ad9748b58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607768"
---
# <a name="creating-assemblies"></a><span data-ttu-id="d5de7-102">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="d5de7-102">Creating Assemblies</span></span>

<span data-ttu-id="d5de7-103">Můžete vytvořit jeden soubor nebo vícesouborové sestavení pomocí rozhraní IDE, jako je Visual Studio, nebo poskytovaný kompilátory a nástroje [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5de7-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="d5de7-104">Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načteno do domény jednu aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d5de7-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="d5de7-105">Toto sestavení nemůže být odkazován jiná sestavení mimo adresář aplikace a nejdou dělit kontrolu verze.</span><span class="sxs-lookup"><span data-stu-id="d5de7-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="d5de7-106">Chcete-li odinstalovat aplikaci, kterou tvoří sestavení, jednoduše odstranit adresář, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="d5de7-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="d5de7-107">Pro mnoho vývojářů sestavení s těmito funkcemi je vše, co je potřeba k nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5de7-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="d5de7-108">Vytvořit vícesouborové sestavení z několika modulů kódu a souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="d5de7-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="d5de7-109">Můžete také vytvořit sestavení, které může sdílet více aplikací.</span><span class="sxs-lookup"><span data-stu-id="d5de7-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="d5de7-110">Sdílená sestavení musí mít silný název a je možné nasadit v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5de7-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="d5de7-111">Máte několik možností, jak při seskupování moduly kódu a prostředků do sestavení, v závislosti na následujících faktorech:</span><span class="sxs-lookup"><span data-stu-id="d5de7-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="d5de7-112">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="d5de7-112">Versioning</span></span>

     <span data-ttu-id="d5de7-113">Skupina modulů, které by měly mít stejné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="d5de7-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="d5de7-114">Nasazení</span><span class="sxs-lookup"><span data-stu-id="d5de7-114">Deployment</span></span>

     <span data-ttu-id="d5de7-115">Moduly skupiny kódu a prostředků, které podporují modelu nasazení.</span><span class="sxs-lookup"><span data-stu-id="d5de7-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="d5de7-116">Opakované použití</span><span class="sxs-lookup"><span data-stu-id="d5de7-116">Reuse</span></span>

     <span data-ttu-id="d5de7-117">Seskupit moduly, pokud jsou logicky lze společně za účelem některé.</span><span class="sxs-lookup"><span data-stu-id="d5de7-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="d5de7-118">Sestavení obsahující typy a třídy zřídka používané pro údržbu programu můžete například umístit ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5de7-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="d5de7-119">Kromě toho by se měly seskupit typy, které chcete sdílet s více aplikacemi do sestavení a sestavení by měl být podepsáno silným názvem.</span><span class="sxs-lookup"><span data-stu-id="d5de7-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="d5de7-120">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d5de7-120">Security</span></span>

     <span data-ttu-id="d5de7-121">Skupina moduly obsahující typy, které vyžadují stejná oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d5de7-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="d5de7-122">Vytváření oborů</span><span class="sxs-lookup"><span data-stu-id="d5de7-122">Scoping</span></span>

     <span data-ttu-id="d5de7-123">Skupina moduly obsahující typy, jejichž viditelnost by měla být omezena na stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="d5de7-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="d5de7-124">Speciální aspekty musí vzít v úvahu zpřístupnění common language runtime sestavení s nespravovanými aplikacemi COM.</span><span class="sxs-lookup"><span data-stu-id="d5de7-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="d5de7-125">Další informace o práci s nespravovaným kódem, najdete v části [vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="d5de7-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5de7-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5de7-126">See also</span></span>

- [<span data-ttu-id="d5de7-127">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="d5de7-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="d5de7-128">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="d5de7-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="d5de7-129">Postupy: Sestavení s jediným souborem</span><span class="sxs-lookup"><span data-stu-id="d5de7-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [<span data-ttu-id="d5de7-130">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="d5de7-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="d5de7-131">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="d5de7-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d5de7-132">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="d5de7-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)