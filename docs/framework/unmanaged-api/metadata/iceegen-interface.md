---
title: "ICeeGen – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen
helpviewer_keywords: ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8342c79dd8b7452599af8d9782b0fbec5f83e964
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iceegen-interface"></a><span data-ttu-id="083ad-102">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="083ad-102">ICeeGen Interface</span></span>
<span data-ttu-id="083ad-103">Poskytuje metody pro dynamický kód kompilace.</span><span class="sxs-lookup"><span data-stu-id="083ad-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="083ad-104">Toto rozhraní je zastaralé a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="083ad-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="083ad-105">Metody</span><span class="sxs-lookup"><span data-stu-id="083ad-105">Methods</span></span>  
  
|<span data-ttu-id="083ad-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-106">Method</span></span>|<span data-ttu-id="083ad-107">Popis</span><span class="sxs-lookup"><span data-stu-id="083ad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="083ad-108">Addsectionreloc – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="083ad-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-109">Obsolete.</span></span> <span data-ttu-id="083ad-110">Přidá instrukce .reloc základu kódu.</span><span class="sxs-lookup"><span data-stu-id="083ad-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="083ad-111">Allocatemethodbuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="083ad-112">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-112">Obsolete.</span></span> <span data-ttu-id="083ad-113">Vytvoří vyrovnávací paměti zadaná velikost pro metodu a získá relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="083ad-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="083ad-114">Computepointer – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="083ad-115">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-115">Obsolete.</span></span> <span data-ttu-id="083ad-116">Určuje velikost vyrovnávací paměti pro část zadaný kód.</span><span class="sxs-lookup"><span data-stu-id="083ad-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="083ad-117">Emitstring – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="083ad-118">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-118">Obsolete.</span></span> <span data-ttu-id="083ad-119">Zadaný řetězec vysílá do základu kódu.</span><span class="sxs-lookup"><span data-stu-id="083ad-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="083ad-120">Generateceefile – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="083ad-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-121">Obsolete.</span></span> <span data-ttu-id="083ad-122">Generuje soubor základu kódu, který obsahuje kód základní momentálně načtených do této `ICeeGen`.</span><span class="sxs-lookup"><span data-stu-id="083ad-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="083ad-123">Generateceememoryimage – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="083ad-124">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-124">Obsolete.</span></span> <span data-ttu-id="083ad-125">Generuje bitovou kopii v paměti pro základu kódu.</span><span class="sxs-lookup"><span data-stu-id="083ad-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="083ad-126">Getilsection – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="083ad-127">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-127">Obsolete.</span></span> <span data-ttu-id="083ad-128">Získá části základní převodní jazyk kódu Zadaný popisovač odkazuje.</span><span class="sxs-lookup"><span data-stu-id="083ad-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="083ad-129">Getimaptokeniface – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="083ad-130">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-130">Obsolete.</span></span> <span data-ttu-id="083ad-131">Získá rozhraní odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="083ad-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="083ad-132">Getmethodbuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="083ad-133">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-133">Obsolete.</span></span> <span data-ttu-id="083ad-134">Získá odpovídající velikost vyrovnávací paměti pro metodu na zadané adrese relativní virtuální.</span><span class="sxs-lookup"><span data-stu-id="083ad-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="083ad-135">Getsectionblock – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="083ad-136">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-136">Obsolete.</span></span> <span data-ttu-id="083ad-137">Získá blok část základu kódu.</span><span class="sxs-lookup"><span data-stu-id="083ad-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="083ad-138">Getsectioncreate – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="083ad-139">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-139">Obsolete.</span></span> <span data-ttu-id="083ad-140">Generuje a získá oddíl kód pomocí zadaného názvu a hodnoty příznaku.</span><span class="sxs-lookup"><span data-stu-id="083ad-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="083ad-141">Getsectiondatalen – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="083ad-142">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-142">Obsolete.</span></span> <span data-ttu-id="083ad-143">Získá délku zadaný oddíl.</span><span class="sxs-lookup"><span data-stu-id="083ad-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="083ad-144">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="083ad-145">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-145">Obsolete.</span></span> <span data-ttu-id="083ad-146">Získá řetězec uložený na zadané adrese relativní virtuální.</span><span class="sxs-lookup"><span data-stu-id="083ad-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="083ad-147">Getstringsection – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="083ad-148">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-148">Obsolete.</span></span> <span data-ttu-id="083ad-149">Získá řetězcovou reprezentaci části kódu, který odkazuje Zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="083ad-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="083ad-150">Truncatesection – metoda</span><span class="sxs-lookup"><span data-stu-id="083ad-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="083ad-151">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="083ad-151">Obsolete.</span></span> <span data-ttu-id="083ad-152">Zkrátí části zadaný kód pomocí zadané délky.</span><span class="sxs-lookup"><span data-stu-id="083ad-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="083ad-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="083ad-153">Requirements</span></span>  
 <span data-ttu-id="083ad-154">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="083ad-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="083ad-155">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="083ad-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="083ad-156">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="083ad-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="083ad-157">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="083ad-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083ad-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="083ad-158">See Also</span></span>  
 [<span data-ttu-id="083ad-159">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="083ad-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
