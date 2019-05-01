---
title: ICeeGen – rozhraní
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fb081c48abf899b44da1c1351efa3f6036f1c8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050204"
---
# <a name="iceegen-interface"></a><span data-ttu-id="689a2-102">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="689a2-102">ICeeGen Interface</span></span>
<span data-ttu-id="689a2-103">Poskytuje metody pro kompilaci dynamického kódu.</span><span class="sxs-lookup"><span data-stu-id="689a2-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="689a2-104">Toto rozhraní je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="689a2-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="689a2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="689a2-105">Methods</span></span>  
  
|<span data-ttu-id="689a2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-106">Method</span></span>|<span data-ttu-id="689a2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="689a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="689a2-108">AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="689a2-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-109">Obsolete.</span></span> <span data-ttu-id="689a2-110">Přidá .reloc instrukce k základu kódu.</span><span class="sxs-lookup"><span data-stu-id="689a2-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="689a2-111">AllocateMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="689a2-112">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-112">Obsolete.</span></span> <span data-ttu-id="689a2-113">Vytvoří vyrovnávací paměti o zadané velikosti pro metodu a získá relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="689a2-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="689a2-114">ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="689a2-115">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-115">Obsolete.</span></span> <span data-ttu-id="689a2-116">Určuje vyrovnávací paměti pro část zadaný kód.</span><span class="sxs-lookup"><span data-stu-id="689a2-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="689a2-117">EmitString – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="689a2-118">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-118">Obsolete.</span></span> <span data-ttu-id="689a2-119">Zadaný řetězec vysílá do základu kódu.</span><span class="sxs-lookup"><span data-stu-id="689a2-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="689a2-120">GenerateCeeFile – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="689a2-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-121">Obsolete.</span></span> <span data-ttu-id="689a2-122">Generuje soubor základu kódu, který obsahuje základní kód aktuálně načtené do tohoto `ICeeGen`.</span><span class="sxs-lookup"><span data-stu-id="689a2-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="689a2-123">GenerateCeeMemoryImage – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="689a2-124">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-124">Obsolete.</span></span> <span data-ttu-id="689a2-125">Vytvoří bitovou kopii v paměti pro základ kódu.</span><span class="sxs-lookup"><span data-stu-id="689a2-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="689a2-126">GetIlSection – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="689a2-127">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-127">Obsolete.</span></span> <span data-ttu-id="689a2-128">Získá části základu kódu IL odkazuje Zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="689a2-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="689a2-129">GetIMapTokenIface – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="689a2-130">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-130">Obsolete.</span></span> <span data-ttu-id="689a2-131">Získá rozhraní odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="689a2-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="689a2-132">GetMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="689a2-133">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-133">Obsolete.</span></span> <span data-ttu-id="689a2-134">Získá vyrovnávací paměť o velikosti odpovídající metodu na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="689a2-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="689a2-135">GetSectionBlock – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="689a2-136">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-136">Obsolete.</span></span> <span data-ttu-id="689a2-137">Získá blok části základu kódu.</span><span class="sxs-lookup"><span data-stu-id="689a2-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="689a2-138">GetSectionCreate – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="689a2-139">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-139">Obsolete.</span></span> <span data-ttu-id="689a2-140">Generuje a získá oddíl kódu pomocí zadaného názvu a hodnoty příznaku.</span><span class="sxs-lookup"><span data-stu-id="689a2-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="689a2-141">GetSectionDataLen – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="689a2-142">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-142">Obsolete.</span></span> <span data-ttu-id="689a2-143">Získá délku zadaný oddíl.</span><span class="sxs-lookup"><span data-stu-id="689a2-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="689a2-144">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="689a2-145">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-145">Obsolete.</span></span> <span data-ttu-id="689a2-146">Získá řetězec uložen na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="689a2-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="689a2-147">GetStringSection – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="689a2-148">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-148">Obsolete.</span></span> <span data-ttu-id="689a2-149">Získá řetězcovou reprezentaci části kódu, který odkazuje Zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="689a2-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="689a2-150">TruncateSection – metoda</span><span class="sxs-lookup"><span data-stu-id="689a2-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="689a2-151">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="689a2-151">Obsolete.</span></span> <span data-ttu-id="689a2-152">Zkrátí části zadaný kód pomocí zadané délky.</span><span class="sxs-lookup"><span data-stu-id="689a2-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="689a2-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="689a2-153">Requirements</span></span>  
 <span data-ttu-id="689a2-154">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="689a2-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="689a2-155">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="689a2-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="689a2-156">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="689a2-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="689a2-157">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="689a2-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="689a2-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="689a2-158">See also</span></span>

- [<span data-ttu-id="689a2-159">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="689a2-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
