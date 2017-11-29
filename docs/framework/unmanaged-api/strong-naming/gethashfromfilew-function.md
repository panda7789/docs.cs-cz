---
title: "GetHashFromFileW – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFileW
helpviewer_keywords: GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c19047f03279b1284ea8b5b8f99785cfaff5146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="d8ea7-102">GetHashFromFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="d8ea7-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="d8ea7-103">Generuje součet hash přes obsah soubor určený touto řetězec znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="d8ea7-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-104">This function has been deprecated.</span></span> <span data-ttu-id="d8ea7-105">Použití [iclrstrongname::gethashfromfilew –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ea7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8ea7-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8ea7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8ea7-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d8ea7-108">[v] Unicode název souboru, který se hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d8ea7-109">[ve out] Algoritmus použitý při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="d8ea7-110">Platný algoritmy jsou definované rozhraní CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="d8ea7-111">Pokud `piHashAlg` je nastaven na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d8ea7-112">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d8ea7-113">[v] Maximální velikost vyrovnávací paměti, na kterou odkazuje `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d8ea7-114">[out] Velikost v bajtech z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ea7-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8ea7-115">Remarks</span></span>  
 <span data-ttu-id="d8ea7-116">Tato funkce je stejný jako [gethashfromfile –](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)kromě toho, že zadání názvu souboru je Unicode místo ANSI.</span><span class="sxs-lookup"><span data-stu-id="d8ea7-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ea7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8ea7-117">Requirements</span></span>  
 <span data-ttu-id="d8ea7-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ea7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ea7-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d8ea7-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d8ea7-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8ea7-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8ea7-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ea7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ea7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8ea7-122">See Also</span></span>  
 [<span data-ttu-id="d8ea7-123">Gethashfromfilew – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ea7-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="d8ea7-124">Gethashfromfile – metoda</span><span class="sxs-lookup"><span data-stu-id="d8ea7-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="d8ea7-125">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8ea7-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
