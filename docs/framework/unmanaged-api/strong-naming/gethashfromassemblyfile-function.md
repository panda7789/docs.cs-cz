---
title: "GetHashFromAssemblyFile – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromAssemblyFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromAssemblyFile
helpviewer_keywords: GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1598e4e332525f87392ae5b0ad486a735e760651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="1dd10-102">GetHashFromAssemblyFile – funkce</span><span class="sxs-lookup"><span data-stu-id="1dd10-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="1dd10-103">Získá hodnotu hash souboru zadaného sestavení pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="1dd10-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="1dd10-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1dd10-104">This function has been deprecated.</span></span> <span data-ttu-id="1dd10-105">Použití [iclrstrongname::gethashfromassemblyfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="1dd10-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd10-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dd10-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1dd10-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dd10-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="1dd10-108">[v] Cesta k souboru, který se použít algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="1dd10-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="1dd10-109">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="1dd10-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="1dd10-110">Používejte nula pro výchozí algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="1dd10-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="1dd10-111">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1dd10-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="1dd10-112">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="1dd10-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="1dd10-113">[out] Vrácen velikost v bajtech, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="1dd10-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd10-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1dd10-114">Requirements</span></span>  
 <span data-ttu-id="1dd10-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd10-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd10-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="1dd10-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1dd10-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1dd10-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd10-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd10-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd10-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dd10-119">See Also</span></span>  
 [<span data-ttu-id="1dd10-120">Gethashfromassemblyfile – metoda</span><span class="sxs-lookup"><span data-stu-id="1dd10-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="1dd10-121">Gethashfromassemblyfilew – metoda</span><span class="sxs-lookup"><span data-stu-id="1dd10-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="1dd10-122">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1dd10-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
