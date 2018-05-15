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
ms.openlocfilehash: 8490351b4ab1bb115e4bd7277f43ad22b144a2df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="creating-assemblies"></a><span data-ttu-id="5c39a-102">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="5c39a-102">Creating Assemblies</span></span>
<span data-ttu-id="5c39a-103">Můžete vytvořit jeden soubor nebo vícesouborového sestavení pomocí rozhraní IDE, jako třeba [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], nebo kompilátory a nástroje poskytované subsystémem [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c39a-103">You can create single-file or multifile assemblies using an IDE, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="5c39a-104">Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načteno do domény jednu aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5c39a-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="5c39a-105">Toto sestavení nemůže být odkazován ostatních sestavení mimo adresář aplikace a není podstoupili kontrolu verze.</span><span class="sxs-lookup"><span data-stu-id="5c39a-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="5c39a-106">Pro odinstalaci aplikace skládá z sestavení, jednoduše odstranit adresář, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="5c39a-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="5c39a-107">Sestavení se tyto funkce pro celá řada vývojářů je všechno, co je potřeba k nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c39a-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>  
  
 <span data-ttu-id="5c39a-108">Můžete vytvořit vícesouborového sestavení z několika moduly kódu a soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="5c39a-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="5c39a-109">Můžete také vytvořit sestavení, které můžete sdílet mezi více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="5c39a-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="5c39a-110">Sdílené sestavení musí mít silný název a je možné nasadit v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c39a-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="5c39a-111">Máte několik možností při seskupování moduly kódu a prostředky do sestavení, a to v závislosti na následujících faktorech:</span><span class="sxs-lookup"><span data-stu-id="5c39a-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>  
  
-   <span data-ttu-id="5c39a-112">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="5c39a-112">Versioning</span></span>  
  
     <span data-ttu-id="5c39a-113">Skupiny moduly, které by měl mít stejné informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="5c39a-113">Group modules that should have the same version information.</span></span>  
  
-   <span data-ttu-id="5c39a-114">Nasazení</span><span class="sxs-lookup"><span data-stu-id="5c39a-114">Deployment</span></span>  
  
     <span data-ttu-id="5c39a-115">Moduly kódu skupiny a prostředky, které podporují modelu nasazení.</span><span class="sxs-lookup"><span data-stu-id="5c39a-115">Group code modules and resources that support your model of deployment.</span></span>  
  
-   <span data-ttu-id="5c39a-116">Opětovné použití</span><span class="sxs-lookup"><span data-stu-id="5c39a-116">Reuse</span></span>  
  
     <span data-ttu-id="5c39a-117">Moduly skupiny, pokud mohou být logicky použity společně pro některé účel.</span><span class="sxs-lookup"><span data-stu-id="5c39a-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="5c39a-118">Například sestavení skládající se z typy a třídy používané zřídka pro Údržba programu můžou být přepnuté do stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c39a-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="5c39a-119">Kromě toho typy, které chcete sdílet s více aplikacemi by měly být seskupené do sestavení a musí být podepsané sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5c39a-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>  
  
-   <span data-ttu-id="5c39a-120">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5c39a-120">Security</span></span>  
  
     <span data-ttu-id="5c39a-121">Skupiny moduly, který obsahuje typy, které vyžadují stejná oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5c39a-121">Group modules containing types that require the same security permissions.</span></span>  
  
-   <span data-ttu-id="5c39a-122">Obor</span><span class="sxs-lookup"><span data-stu-id="5c39a-122">Scoping</span></span>  
  
     <span data-ttu-id="5c39a-123">Skupiny moduly obsahující typy, jejichž viditelnost by mělo být omezeno na stejné sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c39a-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>  
  
 <span data-ttu-id="5c39a-124">Při provádění common language runtime sestavení dostupné pro nespravované aplikace modelu COM, musí být provedeny zvláštní požadavky.</span><span class="sxs-lookup"><span data-stu-id="5c39a-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="5c39a-125">Další informace o práci s nespravovaným kódem najdete v tématu [vystavení komponent architektury .NET Framework do modelu COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="5c39a-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c39a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c39a-126">See Also</span></span>  
 [<span data-ttu-id="5c39a-127">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="5c39a-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="5c39a-128">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="5c39a-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 [<span data-ttu-id="5c39a-129">Postupy: Vytváření sestavení s jediným souborem</span><span class="sxs-lookup"><span data-stu-id="5c39a-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [<span data-ttu-id="5c39a-130">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="5c39a-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="5c39a-131">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="5c39a-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="5c39a-132">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="5c39a-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
