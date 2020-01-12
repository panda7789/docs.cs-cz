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
ms.openlocfilehash: 2a76377857c3cf1e40a328b9a13fb4834321707e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899571"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="cd945-102">ICLRStrongName::StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="cd945-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="cd945-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="cd945-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd945-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd945-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd945-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd945-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="cd945-106">pro Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="cd945-106">[in] The name of the key container.</span></span> <span data-ttu-id="cd945-107">`wszKeyContainer` musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="cd945-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="cd945-108">pro Dvojice binárních klíčů.</span><span class="sxs-lookup"><span data-stu-id="cd945-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="cd945-109">pro Velikost `pbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="cd945-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd945-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cd945-110">Return Value</span></span>  
 <span data-ttu-id="cd945-111">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="cd945-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd945-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd945-112">Remarks</span></span>  
 <span data-ttu-id="cd945-113">K odstranění kontejneru klíčů použijte metodu [ICLRStrongName:: StrongNameKeyDelete –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cd945-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd945-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd945-114">Requirements</span></span>  
 <span data-ttu-id="cd945-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd945-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd945-116">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="cd945-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cd945-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cd945-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd945-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd945-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd945-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd945-119">See also</span></span>

- [<span data-ttu-id="cd945-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="cd945-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="cd945-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd945-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
