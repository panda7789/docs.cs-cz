---
title: "Spouštění internetových aplikací v režimu plné důvěryhodnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58eeda82c66ecda6ffd714e808b006634ccba804
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="running-intranet-applications-in-full-trust"></a><span data-ttu-id="47784-102">Spouštění internetových aplikací v režimu plné důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="47784-102">Running Intranet Applications in Full Trust</span></span>
<span data-ttu-id="47784-103">Od verze rozhraní .NET Framework verze 3.5, Service Pack 1 (SP1), aplikací a jejich sestavení knihovny můžete spouštět jako plné důvěryhodnosti sestavení ze sdílené síťové složky.</span><span class="sxs-lookup"><span data-stu-id="47784-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), applications and their library assemblies can be run as full-trust assemblies from a network share.</span></span> <span data-ttu-id="47784-104"><xref:System.Security.SecurityZone.MyComputer>důkaz zóny se automaticky přidá do sestavení, která jsou načtena ze sdílené složky v síti intranet.</span><span class="sxs-lookup"><span data-stu-id="47784-104"><xref:System.Security.SecurityZone.MyComputer> zone evidence is automatically added to assemblies that are loaded from a share on the intranet.</span></span> <span data-ttu-id="47784-105">Tento důkaz poskytuje tyto sestavení, udělení stejné sady (což je obvykle úplný vztah důvěryhodnosti) jako sestavení, které jsou umístěny v počítači.</span><span class="sxs-lookup"><span data-stu-id="47784-105">This evidence gives those assemblies the same grant set (which is typically full trust) as the assemblies that reside on the computer.</span></span> <span data-ttu-id="47784-106">Tato funkce neplatí pro aplikace ClickOnce nebo aplikace, které jsou určená ke spuštění na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="47784-106">This functionality does not apply to ClickOnce applications or to applications that are designed to run on a host.</span></span>  
  
## <a name="rules-for-library-assemblies"></a><span data-ttu-id="47784-107">Pravidla pro sestavení knihovny</span><span class="sxs-lookup"><span data-stu-id="47784-107">Rules for Library Assemblies</span></span>  
 <span data-ttu-id="47784-108">Následující pravidla platí při sestavení, které jsou načteny spustitelný soubor ve sdílené síťové složce:</span><span class="sxs-lookup"><span data-stu-id="47784-108">The following rules apply to assemblies that are loaded by an executable on a network share:</span></span>  
  
-   <span data-ttu-id="47784-109">Sestavení knihovny se musí nacházet ve stejné složce jako spustitelný soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="47784-109">Library assemblies must reside in the same folder as the executable assembly.</span></span> <span data-ttu-id="47784-110">Sestavení, které jsou umístěny v podsložce nebo se odkazuje na jinou cestu nejsou zadané sady udělení plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="47784-110">Assemblies that reside in a subfolder or are referenced on a different path are not given the full-trust grant set.</span></span>  
  
-   <span data-ttu-id="47784-111">Pokud spustitelný soubor zpoždění načte sestavení, musí používat stejnou cestu, která se používá ke spuštění spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="47784-111">If the executable delay-loads an assembly, it must use the same path that was used to start the executable.</span></span> <span data-ttu-id="47784-112">Například pokud sdílenou složku \\ \\ *počítače v síti*\\*sdílet* je namapovaný na písmeno jednotky a spustitelný soubor spouští z cesty, sestavení, která jsou načtena pomocí spustitelného souboru s použitím síťovou cestu neposkytne úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="47784-112">For example, if the share \\\\*network-computer*\\*share* is mapped to a drive letter and the executable is run from that path, assemblies that are loaded by the executable by using the network path will not be granted full trust.</span></span> <span data-ttu-id="47784-113">Načtení se zpožděním sestavení v <xref:System.Security.SecurityZone.MyComputer> zóny, spustitelný soubor, musíte použít cestu s písmenem jednotky.</span><span class="sxs-lookup"><span data-stu-id="47784-113">To delay-load an assembly in the <xref:System.Security.SecurityZone.MyComputer> zone, the executable must use the drive letter path.</span></span>  
  
## <a name="restoring-the-former-intranet-policy"></a><span data-ttu-id="47784-114">Obnovení dosavadní intranetu zásad</span><span class="sxs-lookup"><span data-stu-id="47784-114">Restoring the Former Intranet Policy</span></span>  
 <span data-ttu-id="47784-115">V dřívějších verzích rozhraní .NET Framework byla poskytnuta sdílená sestavení <xref:System.Security.SecurityZone.Intranet> zónu důkaz.</span><span class="sxs-lookup"><span data-stu-id="47784-115">In earlier versions of the .NET Framework, shared assemblies were granted <xref:System.Security.SecurityZone.Intranet> zone evidence.</span></span> <span data-ttu-id="47784-116">Musíte zadat zásady zabezpečení přístupu kódu udělit úplný vztah důvěryhodnosti k sestavení ve sdílené složce.</span><span class="sxs-lookup"><span data-stu-id="47784-116">You had to specify code access security policy to grant full trust to an assembly on a share.</span></span>  
  
 <span data-ttu-id="47784-117">Toto chování je výchozí pro sestavení intranetu.</span><span class="sxs-lookup"><span data-stu-id="47784-117">This new behavior is the default for intranet assemblies.</span></span> <span data-ttu-id="47784-118">Můžete se vrátit dřívějšímu chování poskytování <xref:System.Security.SecurityZone.Intranet> důkaz nastavením klíče registru, který se vztahuje na všechny aplikace v počítači.</span><span class="sxs-lookup"><span data-stu-id="47784-118">You can return to the earlier behavior of providing <xref:System.Security.SecurityZone.Intranet> evidence by setting a registry key that applies to all applications on the computer.</span></span> <span data-ttu-id="47784-119">Tento proces se liší pro 32bitové a 64bitové počítače:</span><span class="sxs-lookup"><span data-stu-id="47784-119">This process is different for 32-bit and 64-bit computers:</span></span>  
  
-   <span data-ttu-id="47784-120">Na 32bitové počítače, vytvořte podklíč HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč v registru systému.</span><span class="sxs-lookup"><span data-stu-id="47784-120">On 32-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="47784-121">Použijte název klíče LegacyMyComputerZone s hodnotou DWORD s hodnotou 1.</span><span class="sxs-lookup"><span data-stu-id="47784-121">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span>  
  
-   <span data-ttu-id="47784-122">Na 64bitových počítačích, vytvořte podklíč HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč v registru systému.</span><span class="sxs-lookup"><span data-stu-id="47784-122">On 64-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="47784-123">Použijte název klíče LegacyMyComputerZone s hodnotou DWORD s hodnotou 1.</span><span class="sxs-lookup"><span data-stu-id="47784-123">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span> <span data-ttu-id="47784-124">Vytvořit podklíč stejné pod HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="47784-124">Create the same subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47784-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="47784-125">See Also</span></span>  
 [<span data-ttu-id="47784-126">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="47784-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
