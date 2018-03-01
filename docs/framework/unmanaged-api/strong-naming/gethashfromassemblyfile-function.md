---
title: "GetHashFromAssemblyFile – funkce"
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
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ed5de637f8b8d51e2619ba205d89c753b27722bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="2883d-102">GetHashFromAssemblyFile – funkce</span><span class="sxs-lookup"><span data-stu-id="2883d-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="2883d-103">Získá hodnotu hash souboru zadaného sestavení pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="2883d-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="2883d-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="2883d-104">This function has been deprecated.</span></span> <span data-ttu-id="2883d-105">Použití [iclrstrongname::gethashfromassemblyfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="2883d-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2883d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2883d-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2883d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2883d-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="2883d-108">[v] Cesta k souboru, který se použít algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="2883d-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2883d-109">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="2883d-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2883d-110">Používejte nula pro výchozí algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="2883d-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2883d-111">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2883d-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2883d-112">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2883d-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2883d-113">[out] Vrácen velikost v bajtech, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2883d-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2883d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2883d-114">Requirements</span></span>  
 <span data-ttu-id="2883d-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2883d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2883d-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2883d-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2883d-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2883d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2883d-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2883d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2883d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2883d-119">See Also</span></span>  
 [<span data-ttu-id="2883d-120">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="2883d-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="2883d-121">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="2883d-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="2883d-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2883d-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
