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
ms.openlocfilehash: 540fda24a8085a3066dc0485228d3ea3bc56fb98
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747786"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="93b19-102">ICLRStrongName::StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="93b19-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="93b19-103">Odstraní zadaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="93b19-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93b19-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93b19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93b19-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="93b19-106">[in] Název kontejneru klíčů pro odstranění.</span><span class="sxs-lookup"><span data-stu-id="93b19-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93b19-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="93b19-107">Return Value</span></span>  
 <span data-ttu-id="93b19-108">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="93b19-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93b19-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93b19-109">Remarks</span></span>  
 <span data-ttu-id="93b19-110">Použití [iclrstrongname::strongnamekeyinstall –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metoda import pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="93b19-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93b19-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93b19-111">Requirements</span></span>  
 <span data-ttu-id="93b19-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93b19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b19-113">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="93b19-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="93b19-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93b19-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93b19-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93b19-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b19-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93b19-116">See also</span></span>

- [<span data-ttu-id="93b19-117">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="93b19-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="93b19-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93b19-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
