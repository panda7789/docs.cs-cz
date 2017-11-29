---
title: "AssemblyOptions – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyOptions
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ccbbcabd3fbb372322ca6334f6ab6db4fdafc2f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="0702e-102">AssemblyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="0702e-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="0702e-103">Vytvoří výčet možností sestavení.</span><span class="sxs-lookup"><span data-stu-id="0702e-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0702e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0702e-104">Syntax</span></span>  
  
```  
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
  
## <a name="fields"></a><span data-ttu-id="0702e-105">Pole</span><span class="sxs-lookup"><span data-stu-id="0702e-105">Fields</span></span>  
  
|<span data-ttu-id="0702e-106">Pole</span><span class="sxs-lookup"><span data-stu-id="0702e-106">Field</span></span>|<span data-ttu-id="0702e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0702e-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0702e-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="0702e-108">optAssemTitle</span></span>|<span data-ttu-id="0702e-109">String – představuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="0702e-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="0702e-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="0702e-110">optAssemDescription</span></span>|<span data-ttu-id="0702e-111">String – obsahuje popis sestavení.</span><span class="sxs-lookup"><span data-stu-id="0702e-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="0702e-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="0702e-112">optAssemConfig</span></span>|<span data-ttu-id="0702e-113">String – obsahuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0702e-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="0702e-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="0702e-114">optAssemOS</span></span>|<span data-ttu-id="0702e-115">String – kódovaná jako: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="0702e-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="0702e-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="0702e-116">optAssemProcessor</span></span>|<span data-ttu-id="0702e-117">ULONG –</span><span class="sxs-lookup"><span data-stu-id="0702e-117">ULONG</span></span>|  
|<span data-ttu-id="0702e-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="0702e-118">optAssemLocale</span></span>|<span data-ttu-id="0702e-119">String – obsahuje národnímu sestavení.</span><span class="sxs-lookup"><span data-stu-id="0702e-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="0702e-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="0702e-120">optAssemVersion</span></span>|<span data-ttu-id="0702e-121">String – kódovaná jako: "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="0702e-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="0702e-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="0702e-122">optAssemCompany</span></span>|<span data-ttu-id="0702e-123">String – obsahuje společnosti.</span><span class="sxs-lookup"><span data-stu-id="0702e-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="0702e-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="0702e-124">optAssemProduct</span></span>|<span data-ttu-id="0702e-125">String – obsahuje název produktu.</span><span class="sxs-lookup"><span data-stu-id="0702e-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="0702e-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="0702e-126">optAssemProductVersion</span></span>|<span data-ttu-id="0702e-127">Řetězec (také označované jako InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="0702e-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="0702e-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="0702e-128">optAssemCopyright</span></span>|<span data-ttu-id="0702e-129">String – obsahuje informace o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="0702e-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="0702e-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="0702e-130">optAssemTrademark</span></span>|<span data-ttu-id="0702e-131">String – obsahuje informace o ochranných známkách.</span><span class="sxs-lookup"><span data-stu-id="0702e-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="0702e-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="0702e-132">optAssemKeyFile</span></span>|<span data-ttu-id="0702e-133">String (název souboru).</span><span class="sxs-lookup"><span data-stu-id="0702e-133">String (file name).</span></span>|  
|<span data-ttu-id="0702e-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="0702e-134">optAssemKeyName</span></span>|<span data-ttu-id="0702e-135">String (název klíče).</span><span class="sxs-lookup"><span data-stu-id="0702e-135">String (The key name).</span></span>|  
|<span data-ttu-id="0702e-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="0702e-136">optAssemAlgID</span></span>|<span data-ttu-id="0702e-137">ULONG –</span><span class="sxs-lookup"><span data-stu-id="0702e-137">ULONG</span></span>|  
|<span data-ttu-id="0702e-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="0702e-138">optAssemFlags</span></span>|<span data-ttu-id="0702e-139">ULONG –</span><span class="sxs-lookup"><span data-stu-id="0702e-139">ULONG</span></span>|  
|<span data-ttu-id="0702e-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="0702e-140">optAssemHalfSign</span></span>|<span data-ttu-id="0702e-141">BOOL (také označované jako DelaySign).</span><span class="sxs-lookup"><span data-stu-id="0702e-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="0702e-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="0702e-142">optAssemFileVersion</span></span>|<span data-ttu-id="0702e-143">String – kódovaná jako "Major.Minor.Build.Revision"--stejný jako ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="0702e-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="0702e-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="0702e-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="0702e-145">String – kódovaná jako "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="0702e-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="0702e-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="0702e-146">optLastAssemOption</span></span>|<span data-ttu-id="0702e-147">Čítač Počet elementů.</span><span class="sxs-lookup"><span data-stu-id="0702e-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0702e-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0702e-148">Requirements</span></span>  
 <span data-ttu-id="0702e-149">**Záhlaví:** alink.h</span><span class="sxs-lookup"><span data-stu-id="0702e-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="0702e-150">**Knihovna**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="0702e-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0702e-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="0702e-151">See Also</span></span>  
 [<span data-ttu-id="0702e-152">Al.exe (Linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="0702e-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
