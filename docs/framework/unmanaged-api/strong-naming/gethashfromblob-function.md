---
title: "GetHashFromBlob – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromBlob
helpviewer_keywords: GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4564ea36ed8dd4c5de0d1633ba791b47bc2a01b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="6fc49-102">GetHashFromBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="6fc49-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="6fc49-103">Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="6fc49-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="6fc49-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6fc49-104">This function has been deprecated.</span></span> <span data-ttu-id="6fc49-105">Použití [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="6fc49-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fc49-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fc49-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6fc49-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fc49-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="6fc49-108">[v] Ukazatel na adresu paměti blok, který má být použita hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="6fc49-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="6fc49-109">[v] Délka v bajtech bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="6fc49-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6fc49-110">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="6fc49-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="6fc49-111">Používejte nula pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="6fc49-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6fc49-112">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6fc49-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6fc49-113">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6fc49-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6fc49-114">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6fc49-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fc49-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fc49-115">Requirements</span></span>  
 <span data-ttu-id="6fc49-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fc49-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fc49-117">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6fc49-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6fc49-118">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6fc49-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6fc49-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fc49-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc49-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fc49-120">See Also</span></span>  
 [<span data-ttu-id="6fc49-121">GetHashFromBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="6fc49-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="6fc49-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6fc49-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
