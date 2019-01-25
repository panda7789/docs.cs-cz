---
title: GetHashFromAssemblyFile – funkce
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83e3ba8644af1f630b5c9ad5268ec44750badc88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682044"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="27bbe-102">GetHashFromAssemblyFile – funkce</span><span class="sxs-lookup"><span data-stu-id="27bbe-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="27bbe-103">Získá hodnotu hash zadaného souboru sestavení, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="27bbe-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="27bbe-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="27bbe-104">This function has been deprecated.</span></span> <span data-ttu-id="27bbe-105">Použití [iclrstrongname::gethashfromassemblyfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="27bbe-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27bbe-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27bbe-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27bbe-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="27bbe-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="27bbe-108">[in] Cesta k souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="27bbe-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="27bbe-109">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="27bbe-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="27bbe-110">Použít nulu pro výchozí hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="27bbe-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="27bbe-111">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="27bbe-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="27bbe-112">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="27bbe-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="27bbe-113">[out] Velikost v bajtech, vrátil z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="27bbe-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27bbe-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27bbe-114">Requirements</span></span>  
 <span data-ttu-id="27bbe-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27bbe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27bbe-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="27bbe-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="27bbe-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27bbe-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27bbe-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27bbe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bbe-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27bbe-119">See also</span></span>
- [<span data-ttu-id="27bbe-120">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="27bbe-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="27bbe-121">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="27bbe-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="27bbe-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27bbe-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
