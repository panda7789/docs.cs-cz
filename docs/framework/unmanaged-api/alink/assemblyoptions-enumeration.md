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
ms.openlocfilehash: 49e7b73559e8def890f8df8f596fbe8ad5bb5d3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777480"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="649fc-102">AssemblyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="649fc-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="649fc-103">Vytvoří výčet možností sestavení.</span><span class="sxs-lookup"><span data-stu-id="649fc-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="649fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="649fc-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="649fc-105">Pole</span><span class="sxs-lookup"><span data-stu-id="649fc-105">Fields</span></span>  
  
|<span data-ttu-id="649fc-106">Pole</span><span class="sxs-lookup"><span data-stu-id="649fc-106">Field</span></span>|<span data-ttu-id="649fc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="649fc-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="649fc-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="649fc-108">optAssemTitle</span></span>|<span data-ttu-id="649fc-109">Řetězec – představuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="649fc-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="649fc-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="649fc-110">optAssemDescription</span></span>|<span data-ttu-id="649fc-111">Řetězec – obsahuje popis sestavení.</span><span class="sxs-lookup"><span data-stu-id="649fc-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="649fc-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="649fc-112">optAssemConfig</span></span>|<span data-ttu-id="649fc-113">Řetězec – obsahuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="649fc-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="649fc-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="649fc-114">optAssemOS</span></span>|<span data-ttu-id="649fc-115">Řetězec kódovaný jako: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="649fc-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="649fc-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="649fc-116">optAssemProcessor</span></span>|<span data-ttu-id="649fc-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="649fc-117">ULONG</span></span>|  
|<span data-ttu-id="649fc-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="649fc-118">optAssemLocale</span></span>|<span data-ttu-id="649fc-119">Řetězec – obsahuje národní prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="649fc-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="649fc-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="649fc-120">optAssemVersion</span></span>|<span data-ttu-id="649fc-121">Řetězec kódovaný jako: "Hlavní_verze. podverze. sestavení. revize".</span><span class="sxs-lookup"><span data-stu-id="649fc-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="649fc-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="649fc-122">optAssemCompany</span></span>|<span data-ttu-id="649fc-123">Řetězec – obsahuje společnost.</span><span class="sxs-lookup"><span data-stu-id="649fc-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="649fc-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="649fc-124">optAssemProduct</span></span>|<span data-ttu-id="649fc-125">Řetězec – obsahuje název produktu.</span><span class="sxs-lookup"><span data-stu-id="649fc-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="649fc-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="649fc-126">optAssemProductVersion</span></span>|<span data-ttu-id="649fc-127">String (označuje se také jako InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="649fc-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="649fc-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="649fc-128">optAssemCopyright</span></span>|<span data-ttu-id="649fc-129">Řetězec – obsahuje informace o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="649fc-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="649fc-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="649fc-130">optAssemTrademark</span></span>|<span data-ttu-id="649fc-131">Řetězec – obsahuje informace o ochranných známkách.</span><span class="sxs-lookup"><span data-stu-id="649fc-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="649fc-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="649fc-132">optAssemKeyFile</span></span>|<span data-ttu-id="649fc-133">String (název souboru).</span><span class="sxs-lookup"><span data-stu-id="649fc-133">String (file name).</span></span>|  
|<span data-ttu-id="649fc-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="649fc-134">optAssemKeyName</span></span>|<span data-ttu-id="649fc-135">Řetězec (název klíče).</span><span class="sxs-lookup"><span data-stu-id="649fc-135">String (The key name).</span></span>|  
|<span data-ttu-id="649fc-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="649fc-136">optAssemAlgID</span></span>|<span data-ttu-id="649fc-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="649fc-137">ULONG</span></span>|  
|<span data-ttu-id="649fc-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="649fc-138">optAssemFlags</span></span>|<span data-ttu-id="649fc-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="649fc-139">ULONG</span></span>|  
|<span data-ttu-id="649fc-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="649fc-140">optAssemHalfSign</span></span>|<span data-ttu-id="649fc-141">Bool (označuje se také jako DelaySign).</span><span class="sxs-lookup"><span data-stu-id="649fc-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="649fc-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="649fc-142">optAssemFileVersion</span></span>|<span data-ttu-id="649fc-143">Řetězec – zakódovaný jako "hlavní_verze. podverze. sestavení. revize" – stejné jako ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="649fc-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="649fc-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="649fc-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="649fc-145">Řetězec – zakódovaný jako "hlavní_verze. podverze. sestavení. revize".</span><span class="sxs-lookup"><span data-stu-id="649fc-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="649fc-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="649fc-146">optLastAssemOption</span></span>|<span data-ttu-id="649fc-147">Čítač počtu prvků.</span><span class="sxs-lookup"><span data-stu-id="649fc-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="649fc-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="649fc-148">Requirements</span></span>  
 <span data-ttu-id="649fc-149">**Záhlaví:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="649fc-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="649fc-150">**Knihovna**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="649fc-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="649fc-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="649fc-151">See also</span></span>

- [<span data-ttu-id="649fc-152">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="649fc-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
