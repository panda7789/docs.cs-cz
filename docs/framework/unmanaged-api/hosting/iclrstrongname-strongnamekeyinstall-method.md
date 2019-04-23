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
ms.openlocfilehash: 415df9928572e095c529119bf2e726fa383577b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224946"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="38fc6-102">ICLRStrongName::StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="38fc6-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="38fc6-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="38fc6-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38fc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38fc6-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38fc6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38fc6-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="38fc6-106">[in] Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="38fc6-106">[in] The name of the key container.</span></span> <span data-ttu-id="38fc6-107">`wszKeyContainer` musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="38fc6-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="38fc6-108">[in] Binární pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="38fc6-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="38fc6-109">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="38fc6-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38fc6-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38fc6-110">Return Value</span></span>  
 <span data-ttu-id="38fc6-111">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="38fc6-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38fc6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38fc6-112">Remarks</span></span>  
 <span data-ttu-id="38fc6-113">Použití [iclrstrongname::strongnamekeydelete –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metodu pro odstranění kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="38fc6-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38fc6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38fc6-114">Requirements</span></span>  
 <span data-ttu-id="38fc6-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38fc6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38fc6-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="38fc6-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="38fc6-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38fc6-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38fc6-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38fc6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38fc6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38fc6-119">See also</span></span>

- [<span data-ttu-id="38fc6-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="38fc6-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="38fc6-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38fc6-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
