---
title: ICLRStrongName::StrongNameKeyDelete – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7636391e97d79befba3b80a9c4a952e5f64840c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467035"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="f054e-102">ICLRStrongName::StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="f054e-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="f054e-103">Odstraní zadaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="f054e-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f054e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f054e-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f054e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f054e-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="f054e-106">[in] Název kontejneru klíčů pro odstranění.</span><span class="sxs-lookup"><span data-stu-id="f054e-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f054e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f054e-107">Return Value</span></span>  
 <span data-ttu-id="f054e-108">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="f054e-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f054e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f054e-109">Remarks</span></span>  
 <span data-ttu-id="f054e-110">Použití [iclrstrongname::strongnamekeyinstall –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metoda import pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f054e-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f054e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f054e-111">Requirements</span></span>  
 <span data-ttu-id="f054e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f054e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f054e-113">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f054e-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f054e-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f054e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f054e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f054e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f054e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f054e-116">See also</span></span>
- [<span data-ttu-id="f054e-117">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="f054e-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="f054e-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f054e-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
