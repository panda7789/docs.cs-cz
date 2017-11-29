---
title: "ICLRStrongName::StrongNameKeyInstall – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyInstall
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 241421761b87bf9f3baf7315c2ac8e9ebd499486
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="ee6d4-102">ICLRStrongName::StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="ee6d4-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="ee6d4-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ee6d4-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee6d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee6d4-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee6d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee6d4-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ee6d4-106">[v] Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="ee6d4-106">[in] The name of the key container.</span></span> <span data-ttu-id="ee6d4-107">`wszKeyContainer`musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ee6d4-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ee6d4-108">[v] Binární pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="ee6d4-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ee6d4-109">[v] Velikost v bajtech z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ee6d4-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee6d4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ee6d4-110">Return Value</span></span>  
 <span data-ttu-id="ee6d4-111">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="ee6d4-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee6d4-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee6d4-112">Remarks</span></span>  
 <span data-ttu-id="ee6d4-113">Použití [iclrstrongname::strongnamekeydelete –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metoda odstranit kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="ee6d4-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee6d4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee6d4-114">Requirements</span></span>  
 <span data-ttu-id="ee6d4-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee6d4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee6d4-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ee6d4-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ee6d4-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee6d4-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee6d4-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee6d4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6d4-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee6d4-119">See Also</span></span>  
 [<span data-ttu-id="ee6d4-120">Strongnamekeydelete – metoda</span><span class="sxs-lookup"><span data-stu-id="ee6d4-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="ee6d4-121">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee6d4-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
