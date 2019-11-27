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
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="3c10a-102">AssemblyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="3c10a-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="3c10a-103">Vytvoří výčet možností sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c10a-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c10a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c10a-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="3c10a-105">Pole</span><span class="sxs-lookup"><span data-stu-id="3c10a-105">Fields</span></span>  
  
|<span data-ttu-id="3c10a-106">Pole</span><span class="sxs-lookup"><span data-stu-id="3c10a-106">Field</span></span>|<span data-ttu-id="3c10a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3c10a-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3c10a-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="3c10a-108">optAssemTitle</span></span>|<span data-ttu-id="3c10a-109">Řetězec – představuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c10a-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="3c10a-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="3c10a-110">optAssemDescription</span></span>|<span data-ttu-id="3c10a-111">Řetězec – obsahuje popis sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c10a-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="3c10a-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="3c10a-112">optAssemConfig</span></span>|<span data-ttu-id="3c10a-113">Řetězec – obsahuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c10a-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="3c10a-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="3c10a-114">optAssemOS</span></span>|<span data-ttu-id="3c10a-115">Řetězec kódovaný jako: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="3c10a-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="3c10a-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="3c10a-116">optAssemProcessor</span></span>|<span data-ttu-id="3c10a-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="3c10a-117">ULONG</span></span>|  
|<span data-ttu-id="3c10a-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="3c10a-118">optAssemLocale</span></span>|<span data-ttu-id="3c10a-119">Řetězec – obsahuje národní prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c10a-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="3c10a-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="3c10a-120">optAssemVersion</span></span>|<span data-ttu-id="3c10a-121">Řetězec – kódovaný jako: "hlavní_verze. podverze. sestavení. revize".</span><span class="sxs-lookup"><span data-stu-id="3c10a-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="3c10a-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="3c10a-122">optAssemCompany</span></span>|<span data-ttu-id="3c10a-123">Řetězec – obsahuje společnost.</span><span class="sxs-lookup"><span data-stu-id="3c10a-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="3c10a-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="3c10a-124">optAssemProduct</span></span>|<span data-ttu-id="3c10a-125">Řetězec – obsahuje název produktu.</span><span class="sxs-lookup"><span data-stu-id="3c10a-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="3c10a-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="3c10a-126">optAssemProductVersion</span></span>|<span data-ttu-id="3c10a-127">String (označuje se také jako InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="3c10a-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="3c10a-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="3c10a-128">optAssemCopyright</span></span>|<span data-ttu-id="3c10a-129">Řetězec – obsahuje informace o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="3c10a-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="3c10a-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="3c10a-130">optAssemTrademark</span></span>|<span data-ttu-id="3c10a-131">Řetězec – obsahuje informace o ochranných známkách.</span><span class="sxs-lookup"><span data-stu-id="3c10a-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="3c10a-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="3c10a-132">optAssemKeyFile</span></span>|<span data-ttu-id="3c10a-133">String (název souboru).</span><span class="sxs-lookup"><span data-stu-id="3c10a-133">String (file name).</span></span>|  
|<span data-ttu-id="3c10a-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="3c10a-134">optAssemKeyName</span></span>|<span data-ttu-id="3c10a-135">Řetězec (název klíče).</span><span class="sxs-lookup"><span data-stu-id="3c10a-135">String (The key name).</span></span>|  
|<span data-ttu-id="3c10a-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="3c10a-136">optAssemAlgID</span></span>|<span data-ttu-id="3c10a-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="3c10a-137">ULONG</span></span>|  
|<span data-ttu-id="3c10a-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="3c10a-138">optAssemFlags</span></span>|<span data-ttu-id="3c10a-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="3c10a-139">ULONG</span></span>|  
|<span data-ttu-id="3c10a-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="3c10a-140">optAssemHalfSign</span></span>|<span data-ttu-id="3c10a-141">Bool (označuje se také jako DelaySign).</span><span class="sxs-lookup"><span data-stu-id="3c10a-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="3c10a-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="3c10a-142">optAssemFileVersion</span></span>|<span data-ttu-id="3c10a-143">Řetězec – zakódovaný jako "hlavní_verze. podverze. sestavení. revize" – stejné jako ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="3c10a-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="3c10a-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="3c10a-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="3c10a-145">Řetězec – zakódovaný jako "hlavní_verze. podverze. sestavení. revize".</span><span class="sxs-lookup"><span data-stu-id="3c10a-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="3c10a-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="3c10a-146">optLastAssemOption</span></span>|<span data-ttu-id="3c10a-147">Čítač počtu prvků.</span><span class="sxs-lookup"><span data-stu-id="3c10a-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c10a-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c10a-148">Requirements</span></span>  
 <span data-ttu-id="3c10a-149">**Záhlaví:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="3c10a-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="3c10a-150">**Knihovna**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="3c10a-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c10a-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c10a-151">See also</span></span>

- [<span data-ttu-id="3c10a-152">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="3c10a-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
