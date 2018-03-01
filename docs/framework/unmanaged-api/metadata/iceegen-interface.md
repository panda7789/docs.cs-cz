---
title: "ICeeGen – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73af58ac55fd22e5b4f19f715cb0b1a137a640a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iceegen-interface"></a><span data-ttu-id="41406-102">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41406-102">ICeeGen Interface</span></span>
<span data-ttu-id="41406-103">Poskytuje metody pro dynamický kód kompilace.</span><span class="sxs-lookup"><span data-stu-id="41406-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="41406-104">Toto rozhraní je zastaralé a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="41406-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41406-105">Metody</span><span class="sxs-lookup"><span data-stu-id="41406-105">Methods</span></span>  
  
|<span data-ttu-id="41406-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="41406-106">Method</span></span>|<span data-ttu-id="41406-107">Popis</span><span class="sxs-lookup"><span data-stu-id="41406-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41406-108">AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="41406-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-109">Obsolete.</span></span> <span data-ttu-id="41406-110">Přidá instrukce .reloc základu kódu.</span><span class="sxs-lookup"><span data-stu-id="41406-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="41406-111">AllocateMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="41406-112">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-112">Obsolete.</span></span> <span data-ttu-id="41406-113">Vytvoří vyrovnávací paměti zadaná velikost pro metodu a získá relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="41406-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="41406-114">ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="41406-115">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-115">Obsolete.</span></span> <span data-ttu-id="41406-116">Určuje velikost vyrovnávací paměti pro část zadaný kód.</span><span class="sxs-lookup"><span data-stu-id="41406-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="41406-117">EmitString – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="41406-118">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-118">Obsolete.</span></span> <span data-ttu-id="41406-119">Zadaný řetězec vysílá do základu kódu.</span><span class="sxs-lookup"><span data-stu-id="41406-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="41406-120">GenerateCeeFile – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="41406-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-121">Obsolete.</span></span> <span data-ttu-id="41406-122">Generuje soubor základu kódu, který obsahuje kód základní momentálně načtených do této `ICeeGen`.</span><span class="sxs-lookup"><span data-stu-id="41406-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="41406-123">GenerateCeeMemoryImage – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="41406-124">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-124">Obsolete.</span></span> <span data-ttu-id="41406-125">Generuje bitovou kopii v paměti pro základu kódu.</span><span class="sxs-lookup"><span data-stu-id="41406-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="41406-126">GetIlSection – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="41406-127">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-127">Obsolete.</span></span> <span data-ttu-id="41406-128">Získá části základní převodní jazyk kódu Zadaný popisovač odkazuje.</span><span class="sxs-lookup"><span data-stu-id="41406-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="41406-129">GetIMapTokenIface – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="41406-130">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-130">Obsolete.</span></span> <span data-ttu-id="41406-131">Získá rozhraní odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="41406-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="41406-132">GetMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="41406-133">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-133">Obsolete.</span></span> <span data-ttu-id="41406-134">Získá odpovídající velikost vyrovnávací paměti pro metodu na zadané adrese relativní virtuální.</span><span class="sxs-lookup"><span data-stu-id="41406-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="41406-135">GetSectionBlock – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="41406-136">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-136">Obsolete.</span></span> <span data-ttu-id="41406-137">Získá blok část základu kódu.</span><span class="sxs-lookup"><span data-stu-id="41406-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="41406-138">GetSectionCreate – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="41406-139">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-139">Obsolete.</span></span> <span data-ttu-id="41406-140">Generuje a získá oddíl kód pomocí zadaného názvu a hodnoty příznaku.</span><span class="sxs-lookup"><span data-stu-id="41406-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="41406-141">GetSectionDataLen – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="41406-142">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-142">Obsolete.</span></span> <span data-ttu-id="41406-143">Získá délku zadaný oddíl.</span><span class="sxs-lookup"><span data-stu-id="41406-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="41406-144">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="41406-145">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-145">Obsolete.</span></span> <span data-ttu-id="41406-146">Získá řetězec uložený na zadané adrese relativní virtuální.</span><span class="sxs-lookup"><span data-stu-id="41406-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="41406-147">GetStringSection – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="41406-148">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-148">Obsolete.</span></span> <span data-ttu-id="41406-149">Získá řetězcovou reprezentaci části kódu, který odkazuje Zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="41406-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="41406-150">TruncateSection – metoda</span><span class="sxs-lookup"><span data-stu-id="41406-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="41406-151">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="41406-151">Obsolete.</span></span> <span data-ttu-id="41406-152">Zkrátí části zadaný kód pomocí zadané délky.</span><span class="sxs-lookup"><span data-stu-id="41406-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41406-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41406-153">Requirements</span></span>  
 <span data-ttu-id="41406-154">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41406-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41406-155">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="41406-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41406-156">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41406-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41406-157">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41406-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41406-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="41406-158">See Also</span></span>  
 [<span data-ttu-id="41406-159">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="41406-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
