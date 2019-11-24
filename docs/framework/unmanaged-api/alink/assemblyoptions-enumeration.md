---
title: AssemblyOptions – výčet
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
ms.openlocfilehash: ed45e06297b77ea60304cdcfe1b08e97f9e4c085
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446587"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="5be5e-102">AssemblyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="5be5e-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="5be5e-103">Enumerates the assembly options.</span><span class="sxs-lookup"><span data-stu-id="5be5e-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5be5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5be5e-104">Syntax</span></span>  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="5be5e-105">Pole</span><span class="sxs-lookup"><span data-stu-id="5be5e-105">Fields</span></span>  
  
|<span data-ttu-id="5be5e-106">Pole</span><span class="sxs-lookup"><span data-stu-id="5be5e-106">Field</span></span>|<span data-ttu-id="5be5e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5be5e-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5be5e-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="5be5e-108">optAssemTitle</span></span>|<span data-ttu-id="5be5e-109">String - Represents the assembly title.</span><span class="sxs-lookup"><span data-stu-id="5be5e-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="5be5e-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="5be5e-110">optAssemDescription</span></span>|<span data-ttu-id="5be5e-111">String - Contains the assembly description.</span><span class="sxs-lookup"><span data-stu-id="5be5e-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="5be5e-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="5be5e-112">optAssemConfig</span></span>|<span data-ttu-id="5be5e-113">String - Contains the assembly configuration.</span><span class="sxs-lookup"><span data-stu-id="5be5e-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="5be5e-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="5be5e-114">optAssemOS</span></span>|<span data-ttu-id="5be5e-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="5be5e-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="5be5e-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="5be5e-116">optAssemProcessor</span></span>|<span data-ttu-id="5be5e-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="5be5e-117">ULONG</span></span>|  
|<span data-ttu-id="5be5e-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="5be5e-118">optAssemLocale</span></span>|<span data-ttu-id="5be5e-119">String - Contains the assembly locale.</span><span class="sxs-lookup"><span data-stu-id="5be5e-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="5be5e-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="5be5e-120">optAssemVersion</span></span>|<span data-ttu-id="5be5e-121">String - Encoded as: "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="5be5e-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="5be5e-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="5be5e-122">optAssemCompany</span></span>|<span data-ttu-id="5be5e-123">String - Contains the company.</span><span class="sxs-lookup"><span data-stu-id="5be5e-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="5be5e-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="5be5e-124">optAssemProduct</span></span>|<span data-ttu-id="5be5e-125">String - Contains the product name.</span><span class="sxs-lookup"><span data-stu-id="5be5e-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="5be5e-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="5be5e-126">optAssemProductVersion</span></span>|<span data-ttu-id="5be5e-127">String (also known as InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="5be5e-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="5be5e-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="5be5e-128">optAssemCopyright</span></span>|<span data-ttu-id="5be5e-129">String - Contains the copyright information.</span><span class="sxs-lookup"><span data-stu-id="5be5e-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="5be5e-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="5be5e-130">optAssemTrademark</span></span>|<span data-ttu-id="5be5e-131">String - Contains the trademark information.</span><span class="sxs-lookup"><span data-stu-id="5be5e-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="5be5e-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="5be5e-132">optAssemKeyFile</span></span>|<span data-ttu-id="5be5e-133">String (file name).</span><span class="sxs-lookup"><span data-stu-id="5be5e-133">String (file name).</span></span>|  
|<span data-ttu-id="5be5e-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="5be5e-134">optAssemKeyName</span></span>|<span data-ttu-id="5be5e-135">String (The key name).</span><span class="sxs-lookup"><span data-stu-id="5be5e-135">String (The key name).</span></span>|  
|<span data-ttu-id="5be5e-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="5be5e-136">optAssemAlgID</span></span>|<span data-ttu-id="5be5e-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="5be5e-137">ULONG</span></span>|  
|<span data-ttu-id="5be5e-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="5be5e-138">optAssemFlags</span></span>|<span data-ttu-id="5be5e-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="5be5e-139">ULONG</span></span>|  
|<span data-ttu-id="5be5e-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="5be5e-140">optAssemHalfSign</span></span>|<span data-ttu-id="5be5e-141">Bool (Also known as DelaySign).</span><span class="sxs-lookup"><span data-stu-id="5be5e-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="5be5e-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="5be5e-142">optAssemFileVersion</span></span>|<span data-ttu-id="5be5e-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="5be5e-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="5be5e-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="5be5e-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="5be5e-145">String - Encoded as "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="5be5e-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="5be5e-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="5be5e-146">optLastAssemOption</span></span>|<span data-ttu-id="5be5e-147">A counter of the number of elements.</span><span class="sxs-lookup"><span data-stu-id="5be5e-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5be5e-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5be5e-148">Requirements</span></span>  
 <span data-ttu-id="5be5e-149">**Header:** alink.h</span><span class="sxs-lookup"><span data-stu-id="5be5e-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="5be5e-150">**Library**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="5be5e-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be5e-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5be5e-151">See also</span></span>

- [<span data-ttu-id="5be5e-152">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="5be5e-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
