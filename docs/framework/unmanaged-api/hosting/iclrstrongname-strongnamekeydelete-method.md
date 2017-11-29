---
title: "ICLRStrongName::StrongNameKeyDelete – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyDelete
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8fbb6af492007eb0dc2a9ea83c53e3559225428d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="ecae3-102">ICLRStrongName::StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="ecae3-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="ecae3-103">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="ecae3-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecae3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecae3-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecae3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecae3-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ecae3-106">[v] Název kontejneru klíčů odstranit.</span><span class="sxs-lookup"><span data-stu-id="ecae3-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecae3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ecae3-107">Return Value</span></span>  
 <span data-ttu-id="ecae3-108">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="ecae3-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecae3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecae3-109">Remarks</span></span>  
 <span data-ttu-id="ecae3-110">Použití [iclrstrongname::strongnamekeyinstall –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metoda import pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ecae3-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecae3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecae3-111">Requirements</span></span>  
 <span data-ttu-id="ecae3-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecae3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecae3-113">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ecae3-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ecae3-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecae3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecae3-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecae3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecae3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecae3-116">See Also</span></span>  
 [<span data-ttu-id="ecae3-117">Strongnamekeyinstall – metoda</span><span class="sxs-lookup"><span data-stu-id="ecae3-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="ecae3-118">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecae3-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
