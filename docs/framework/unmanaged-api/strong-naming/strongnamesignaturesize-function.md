---
title: "StrongNameSignatureSize – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureSize
helpviewer_keywords: StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70aa82d5eef62856e8377c75515fb3b187d3ae6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="607a6-102">StrongNameSignatureSize – funkce</span><span class="sxs-lookup"><span data-stu-id="607a6-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="607a6-103">Vrátí velikost podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="607a6-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="607a6-104">`StrongNameSignatureSize`se obvykle používá kompilátory Chcete-li zjistit, kolik místa vyhradit v souboru při vytváření sestavení se zpožděním podepsané.</span><span class="sxs-lookup"><span data-stu-id="607a6-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="607a6-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="607a6-105">This function has been deprecated.</span></span> <span data-ttu-id="607a6-106">Použití [iclrstrongname::strongnamesignaturesize –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="607a6-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="607a6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="607a6-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="607a6-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="607a6-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="607a6-109">[v] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů sloužící ke generování podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="607a6-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="607a6-110">[v] Velikost v bajtech z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="607a6-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="607a6-111">[v] Počet bajtů požadovaných k uložení podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="607a6-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="607a6-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="607a6-112">Return Value</span></span>  
 <span data-ttu-id="607a6-113">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="607a6-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="607a6-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="607a6-114">Remarks</span></span>  
 <span data-ttu-id="607a6-115">Pokud `StrongNameSignatureSize` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="607a6-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="607a6-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="607a6-116">Requirements</span></span>  
 <span data-ttu-id="607a6-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="607a6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="607a6-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="607a6-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="607a6-119">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="607a6-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="607a6-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="607a6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607a6-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="607a6-121">See Also</span></span>  
 [<span data-ttu-id="607a6-122">StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="607a6-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)  
 [<span data-ttu-id="607a6-123">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="607a6-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
