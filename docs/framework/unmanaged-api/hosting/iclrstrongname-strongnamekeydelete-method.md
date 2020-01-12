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
ms.openlocfilehash: 95098cbb060c06d2d5a5a4c04b6fa9017bca66a1
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899593"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="aa12e-102">ICLRStrongName::StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="aa12e-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="aa12e-103">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="aa12e-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa12e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa12e-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa12e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa12e-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="aa12e-106">pro Název kontejneru klíčů, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="aa12e-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa12e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa12e-107">Return Value</span></span>  
 <span data-ttu-id="aa12e-108">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="aa12e-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa12e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa12e-109">Remarks</span></span>  
 <span data-ttu-id="aa12e-110">Pomocí metody [ICLRStrongName:: StrongNameKeyInstall –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) importujte pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="aa12e-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa12e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa12e-111">Requirements</span></span>  
 <span data-ttu-id="aa12e-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa12e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa12e-113">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="aa12e-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aa12e-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aa12e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa12e-115">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa12e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa12e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa12e-116">See also</span></span>

- [<span data-ttu-id="aa12e-117">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="aa12e-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="aa12e-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa12e-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
