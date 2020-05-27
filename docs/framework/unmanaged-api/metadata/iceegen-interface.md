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
ms.openlocfilehash: e6cf0aa6f731d0a417e1a2be0ca1d0f8c9299379
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008271"
---
# <a name="iceegen-interface"></a><span data-ttu-id="483f2-102">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="483f2-102">ICeeGen Interface</span></span>
<span data-ttu-id="483f2-103">Poskytuje metody pro kompilaci dynamického kódu.</span><span class="sxs-lookup"><span data-stu-id="483f2-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="483f2-104">Toto rozhraní je zastaralé a nemělo by se používat.</span><span class="sxs-lookup"><span data-stu-id="483f2-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="483f2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="483f2-105">Methods</span></span>  
  
|<span data-ttu-id="483f2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-106">Method</span></span>|<span data-ttu-id="483f2-107">Description</span><span class="sxs-lookup"><span data-stu-id="483f2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="483f2-108">AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-108">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)|<span data-ttu-id="483f2-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-109">Obsolete.</span></span> <span data-ttu-id="483f2-110">Přidá instrukci. přemístění do základu kódu.</span><span class="sxs-lookup"><span data-stu-id="483f2-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="483f2-111">AllocateMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-111">AllocateMethodBuffer Method</span></span>](iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="483f2-112">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-112">Obsolete.</span></span> <span data-ttu-id="483f2-113">Vytvoří vyrovnávací paměť zadané velikosti pro metodu a získá relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="483f2-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="483f2-114">ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-114">ComputePointer Method</span></span>](iceegen-computepointer-method.md)|<span data-ttu-id="483f2-115">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-115">Obsolete.</span></span> <span data-ttu-id="483f2-116">Určuje vyrovnávací paměť pro zadaný oddíl kódu.</span><span class="sxs-lookup"><span data-stu-id="483f2-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="483f2-117">EmitString – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-117">EmitString Method</span></span>](iceegen-emitstring-method.md)|<span data-ttu-id="483f2-118">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-118">Obsolete.</span></span> <span data-ttu-id="483f2-119">Vygeneruje zadaný řetězec do základu kódu.</span><span class="sxs-lookup"><span data-stu-id="483f2-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="483f2-120">GenerateCeeFile – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-120">GenerateCeeFile Method</span></span>](iceegen-generateceefile-method.md)|<span data-ttu-id="483f2-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-121">Obsolete.</span></span> <span data-ttu-id="483f2-122">Vygeneruje soubor základní znakové sady, který obsahuje základ kódu, který je aktuálně načten do tohoto `ICeeGen` .</span><span class="sxs-lookup"><span data-stu-id="483f2-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="483f2-123">GenerateCeeMemoryImage – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-123">GenerateCeeMemoryImage Method</span></span>](iceegen-generateceememoryimage-method.md)|<span data-ttu-id="483f2-124">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-124">Obsolete.</span></span> <span data-ttu-id="483f2-125">Vygeneruje obrázek v paměti pro základ kódu.</span><span class="sxs-lookup"><span data-stu-id="483f2-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="483f2-126">GetIlSection – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-126">GetIlSection Method</span></span>](iceegen-getilsection-method.md)|<span data-ttu-id="483f2-127">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-127">Obsolete.</span></span> <span data-ttu-id="483f2-128">Získá část základu kódu zprostředkujícího jazyka, na kterou odkazuje zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="483f2-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="483f2-129">GetIMapTokenIface – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-129">GetIMapTokenIface Method</span></span>](iceegen-getimaptokeniface-method.md)|<span data-ttu-id="483f2-130">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-130">Obsolete.</span></span> <span data-ttu-id="483f2-131">Získá rozhraní, na které odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="483f2-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="483f2-132">GetMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-132">GetMethodBuffer Method</span></span>](iceegen-getmethodbuffer-method.md)|<span data-ttu-id="483f2-133">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-133">Obsolete.</span></span> <span data-ttu-id="483f2-134">Načte vyrovnávací paměť odpovídající velikosti pro metodu na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="483f2-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="483f2-135">GetSectionBlock – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-135">GetSectionBlock Method</span></span>](iceegen-getsectionblock-method.md)|<span data-ttu-id="483f2-136">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-136">Obsolete.</span></span> <span data-ttu-id="483f2-137">Získá blok oddílu základu kódu.</span><span class="sxs-lookup"><span data-stu-id="483f2-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="483f2-138">GetSectionCreate – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-138">GetSectionCreate Method</span></span>](iceegen-getsectioncreate-method.md)|<span data-ttu-id="483f2-139">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-139">Obsolete.</span></span> <span data-ttu-id="483f2-140">Vygeneruje a získá oddíl kódu s použitím zadaných hodnot název a příznak.</span><span class="sxs-lookup"><span data-stu-id="483f2-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="483f2-141">GetSectionDataLen – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-141">GetSectionDataLen Method</span></span>](iceegen-getsectiondatalen-method.md)|<span data-ttu-id="483f2-142">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-142">Obsolete.</span></span> <span data-ttu-id="483f2-143">Získá délku zadaného oddílu.</span><span class="sxs-lookup"><span data-stu-id="483f2-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="483f2-144">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-144">GetString Method</span></span>](iceegen-getstring-method.md)|<span data-ttu-id="483f2-145">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-145">Obsolete.</span></span> <span data-ttu-id="483f2-146">Získá řetězec uložený na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="483f2-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="483f2-147">GetStringSection – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-147">GetStringSection Method</span></span>](iceegen-getstringsection-method.md)|<span data-ttu-id="483f2-148">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-148">Obsolete.</span></span> <span data-ttu-id="483f2-149">Načte řetězcovou reprezentaci oddílu kódu, na který odkazuje zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="483f2-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="483f2-150">TruncateSection – metoda</span><span class="sxs-lookup"><span data-stu-id="483f2-150">TruncateSection Method</span></span>](iceegen-truncatesection-method.md)|<span data-ttu-id="483f2-151">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="483f2-151">Obsolete.</span></span> <span data-ttu-id="483f2-152">Zkrátí zadaný oddíl kódu o zadanou délku.</span><span class="sxs-lookup"><span data-stu-id="483f2-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="483f2-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="483f2-153">Requirements</span></span>  
 <span data-ttu-id="483f2-154">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="483f2-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="483f2-155">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="483f2-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="483f2-156">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="483f2-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="483f2-157">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="483f2-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483f2-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="483f2-158">See also</span></span>

- [<span data-ttu-id="483f2-159">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="483f2-159">Metadata Interfaces</span></span>](metadata-interfaces.md)
