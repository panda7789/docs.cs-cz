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
ms.openlocfilehash: 4e72818be6808c519677192d3744bbc5ec414d0d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135081"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="42da1-102">ICLRStrongName::StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="42da1-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="42da1-103">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="42da1-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42da1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42da1-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42da1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42da1-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="42da1-106">pro Název kontejneru klíčů, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="42da1-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42da1-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="42da1-107">Return Value</span></span>  
 <span data-ttu-id="42da1-108">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="42da1-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42da1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42da1-109">Remarks</span></span>  
 <span data-ttu-id="42da1-110">Pomocí metody [ICLRStrongName:: StrongNameKeyInstall –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) importujte pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="42da1-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42da1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42da1-111">Requirements</span></span>  
 <span data-ttu-id="42da1-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42da1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42da1-113">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="42da1-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="42da1-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="42da1-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42da1-115">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42da1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42da1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42da1-116">See also</span></span>

- [<span data-ttu-id="42da1-117">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="42da1-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="42da1-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42da1-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
