---
title: "ICLRStrongName::StrongNameSignatureSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureSize
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a961cca6bba24ac8a2428a20c616a2ee074b8abf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="ef8d6-102">ICLRStrongName::StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="ef8d6-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="ef8d6-103">Vrátí velikost podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="ef8d6-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="ef8d6-104">Tato metoda se obvykle používá kompilátory, chcete-li zjistit, kolik místa vyhradit v souboru při vytváření sestavení se zpožděním podepsané.</span><span class="sxs-lookup"><span data-stu-id="ef8d6-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef8d6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef8d6-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef8d6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef8d6-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="ef8d6-107">[v] Struktura typu [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů sloužící ke generování podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="ef8d6-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="ef8d6-108">[v] Velikost v bajtech z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ef8d6-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="ef8d6-109">[v] Počet bajtů požadovaných k uložení podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="ef8d6-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef8d6-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ef8d6-110">Return Value</span></span>  
 <span data-ttu-id="ef8d6-111">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="ef8d6-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef8d6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef8d6-112">Requirements</span></span>  
 <span data-ttu-id="ef8d6-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef8d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef8d6-114">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ef8d6-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ef8d6-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef8d6-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef8d6-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef8d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8d6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef8d6-117">See Also</span></span>  
 [<span data-ttu-id="ef8d6-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef8d6-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
