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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293787d7798768ff2b4e2fb8fec9ed201fdb85ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790101"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="a94db-102">AssemblyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="a94db-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="a94db-103">Vytvoří výčet možností sestavení.</span><span class="sxs-lookup"><span data-stu-id="a94db-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a94db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a94db-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="a94db-105">Pole</span><span class="sxs-lookup"><span data-stu-id="a94db-105">Fields</span></span>  
  
|<span data-ttu-id="a94db-106">Pole</span><span class="sxs-lookup"><span data-stu-id="a94db-106">Field</span></span>|<span data-ttu-id="a94db-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a94db-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a94db-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="a94db-108">optAssemTitle</span></span>|<span data-ttu-id="a94db-109">String – představuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="a94db-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="a94db-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="a94db-110">optAssemDescription</span></span>|<span data-ttu-id="a94db-111">String – obsahuje popis sestavení.</span><span class="sxs-lookup"><span data-stu-id="a94db-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="a94db-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="a94db-112">optAssemConfig</span></span>|<span data-ttu-id="a94db-113">String – obsahuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="a94db-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="a94db-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="a94db-114">optAssemOS</span></span>|<span data-ttu-id="a94db-115">String – zakódován jako: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="a94db-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="a94db-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="a94db-116">optAssemProcessor</span></span>|<span data-ttu-id="a94db-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="a94db-117">ULONG</span></span>|  
|<span data-ttu-id="a94db-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="a94db-118">optAssemLocale</span></span>|<span data-ttu-id="a94db-119">String – obsahuje národní prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="a94db-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="a94db-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="a94db-120">optAssemVersion</span></span>|<span data-ttu-id="a94db-121">String – zakódován jako: "Major.Minor.Build.Revision".</span><span class="sxs-lookup"><span data-stu-id="a94db-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="a94db-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="a94db-122">optAssemCompany</span></span>|<span data-ttu-id="a94db-123">String – obsahuje společnosti.</span><span class="sxs-lookup"><span data-stu-id="a94db-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="a94db-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="a94db-124">optAssemProduct</span></span>|<span data-ttu-id="a94db-125">String – obsahuje název produktu.</span><span class="sxs-lookup"><span data-stu-id="a94db-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="a94db-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="a94db-126">optAssemProductVersion</span></span>|<span data-ttu-id="a94db-127">Řetězec (označované také jako InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="a94db-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="a94db-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="a94db-128">optAssemCopyright</span></span>|<span data-ttu-id="a94db-129">String – obsahuje informace o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="a94db-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="a94db-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="a94db-130">optAssemTrademark</span></span>|<span data-ttu-id="a94db-131">String – obsahuje informace o ochranných známkách.</span><span class="sxs-lookup"><span data-stu-id="a94db-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="a94db-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="a94db-132">optAssemKeyFile</span></span>|<span data-ttu-id="a94db-133">String (název souboru).</span><span class="sxs-lookup"><span data-stu-id="a94db-133">String (file name).</span></span>|  
|<span data-ttu-id="a94db-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="a94db-134">optAssemKeyName</span></span>|<span data-ttu-id="a94db-135">String (název klíče).</span><span class="sxs-lookup"><span data-stu-id="a94db-135">String (The key name).</span></span>|  
|<span data-ttu-id="a94db-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="a94db-136">optAssemAlgID</span></span>|<span data-ttu-id="a94db-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="a94db-137">ULONG</span></span>|  
|<span data-ttu-id="a94db-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="a94db-138">optAssemFlags</span></span>|<span data-ttu-id="a94db-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="a94db-139">ULONG</span></span>|  
|<span data-ttu-id="a94db-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="a94db-140">optAssemHalfSign</span></span>|<span data-ttu-id="a94db-141">BOOL (označované také jako DelaySign).</span><span class="sxs-lookup"><span data-stu-id="a94db-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="a94db-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="a94db-142">optAssemFileVersion</span></span>|<span data-ttu-id="a94db-143">String – kódovaný jako "Hlavníverze.podverze.Build.revize" – stejně jako ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="a94db-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="a94db-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="a94db-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="a94db-145">String – kódovaný jako "Hlavníverze.podverze.Build.revize".</span><span class="sxs-lookup"><span data-stu-id="a94db-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="a94db-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="a94db-146">optLastAssemOption</span></span>|<span data-ttu-id="a94db-147">Čítač Počet prvků.</span><span class="sxs-lookup"><span data-stu-id="a94db-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a94db-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a94db-148">Requirements</span></span>  
 <span data-ttu-id="a94db-149">**Záhlaví:** alink.h</span><span class="sxs-lookup"><span data-stu-id="a94db-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="a94db-150">**Knihovna**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="a94db-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a94db-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a94db-151">See also</span></span>

- [<span data-ttu-id="a94db-152">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="a94db-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
