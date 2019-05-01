---
title: GetHashFromHandle – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48dd987896536006fe81bc01528cadb507123e27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049424"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="b2503-102">GetHashFromHandle – funkce</span><span class="sxs-lookup"><span data-stu-id="b2503-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="b2503-103">Vygeneruje hodnotu hash přes obsah souboru pomocí zadaného popisovače souboru, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="b2503-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="b2503-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b2503-104">This function has been deprecated.</span></span> <span data-ttu-id="b2503-105">Použití [iclrstrongname::gethashfromhandle –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="b2503-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2503-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2503-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2503-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2503-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="b2503-108">[in] Popisovač souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="b2503-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b2503-109">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="b2503-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="b2503-110">Použít nulu pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="b2503-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b2503-111">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b2503-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b2503-112">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b2503-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b2503-113">[out] Velikost v bajtech, vráceného `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b2503-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2503-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2503-114">Requirements</span></span>  
 <span data-ttu-id="b2503-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2503-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2503-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b2503-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b2503-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2503-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2503-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2503-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2503-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2503-119">See also</span></span>

- [<span data-ttu-id="b2503-120">GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="b2503-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="b2503-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2503-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
