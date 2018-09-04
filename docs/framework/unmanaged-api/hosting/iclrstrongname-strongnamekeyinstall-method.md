---
title: ICLRStrongName::StrongNameKeyInstall – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d60e1e503cd48b9b9e2ed91a6bfea000aeeea2af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527873"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="8a411-102">ICLRStrongName::StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="8a411-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="8a411-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8a411-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a411-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a411-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a411-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a411-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="8a411-106">[in] Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8a411-106">[in] The name of the key container.</span></span> <span data-ttu-id="8a411-107">`wszKeyContainer` musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8a411-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8a411-108">[in] Binární pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="8a411-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8a411-109">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8a411-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a411-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8a411-110">Return Value</span></span>  
 <span data-ttu-id="8a411-111">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="8a411-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a411-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a411-112">Remarks</span></span>  
 <span data-ttu-id="8a411-113">Použití [iclrstrongname::strongnamekeydelete –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metodu pro odstranění kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8a411-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a411-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a411-114">Requirements</span></span>  
 <span data-ttu-id="8a411-115">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a411-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a411-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8a411-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8a411-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a411-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a411-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a411-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a411-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a411-119">See Also</span></span>  
 [<span data-ttu-id="8a411-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="8a411-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="8a411-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a411-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
