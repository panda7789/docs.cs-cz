---
title: ICLRStrongName::StrongNameSignatureVerificationEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: fbc9ea6aab9f0c3d9be95e6affcd04342ce4c5cc
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901077"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="b1327-102">ICLRStrongName::StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="b1327-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="b1327-103">Získá hodnotu, která označuje, zda manifest sestavení v zadané cestě obsahuje podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="b1327-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1327-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1327-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1327-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1327-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b1327-106">pro Cesta k přenositelnému spustitelnému souboru (. exe nebo. dll) pro sestavení, které má být ověřeno.</span><span class="sxs-lookup"><span data-stu-id="b1327-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="b1327-107">[in] `true` provádět ověřování, i když je nutné přepsat nastavení registru. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="b1327-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="b1327-108">[out] `true`, jestli se podpis silného názvu ověřil; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="b1327-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="b1327-109">`pfWasVerified` je také nastaveno na `false`, pokud bylo ověření úspěšné z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="b1327-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1327-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b1327-110">Return Value</span></span>  
 <span data-ttu-id="b1327-111">`S_OK`, zda bylo ověření úspěšné; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="b1327-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1327-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1327-112">Remarks</span></span>  
 <span data-ttu-id="b1327-113">Metoda [ICLRStrongName:: StrongNameSignatureVerificationEx –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) poskytuje funkci podobnou metodě [ICLRStrongName:: StrongNameSignatureVerification –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b1327-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="b1327-114">Druhý vstupní parametr a výstupní parametr pro [ICLRStrongName:: StrongNameSignatureVerificationEx –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) jsou však typu `BOOLEAN` místo `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="b1327-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1327-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1327-115">Requirements</span></span>  
 <span data-ttu-id="b1327-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1327-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1327-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b1327-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b1327-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1327-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1327-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1327-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1327-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1327-120">See also</span></span>

- [<span data-ttu-id="b1327-121">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="b1327-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="b1327-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1327-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
