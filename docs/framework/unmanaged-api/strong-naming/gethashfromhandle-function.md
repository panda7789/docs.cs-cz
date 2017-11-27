---
title: "GetHashFromHandle – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromHandle
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromHandle
helpviewer_keywords: GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ccb6d3b50e70d69b706f63be8a783ad6d7f7cdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="a21fa-102">GetHashFromHandle – funkce</span><span class="sxs-lookup"><span data-stu-id="a21fa-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="a21fa-103">Generuje součet hash přes obsah souboru s popisovačem zadaný soubor, použití zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="a21fa-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="a21fa-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a21fa-104">This function has been deprecated.</span></span> <span data-ttu-id="a21fa-105">Použití [iclrstrongname::gethashfromhandle –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="a21fa-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a21fa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a21fa-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a21fa-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a21fa-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="a21fa-108">[v] Popisovač souboru, který se použít algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="a21fa-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a21fa-109">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="a21fa-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="a21fa-110">Používejte nula pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="a21fa-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a21fa-111">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a21fa-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a21fa-112">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="a21fa-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a21fa-113">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="a21fa-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a21fa-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a21fa-114">Requirements</span></span>  
 <span data-ttu-id="a21fa-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a21fa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a21fa-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a21fa-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a21fa-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a21fa-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a21fa-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a21fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a21fa-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a21fa-119">See Also</span></span>  
 [<span data-ttu-id="a21fa-120">Gethashfromhandle – metoda</span><span class="sxs-lookup"><span data-stu-id="a21fa-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="a21fa-121">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a21fa-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
