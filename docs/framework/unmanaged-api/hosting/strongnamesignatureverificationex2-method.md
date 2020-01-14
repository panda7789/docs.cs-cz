---
title: StrongNameSignatureVerificationEx2 – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
ms.openlocfilehash: 81640e8e34335898f4dd7f4f43eafbd3ef191d19
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938158"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="e0102-102">StrongNameSignatureVerificationEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e0102-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="e0102-103">Ověří podpis silně pojmenovaného sestavení a poskytuje mapování z klíče ECMA na skutečný klíč.</span><span class="sxs-lookup"><span data-stu-id="e0102-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0102-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0102-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0102-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0102-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e0102-106">pro Cesta k přenositelnému spustitelnému souboru (. exe nebo. dll) pro sestavení, které má být ověřeno.</span><span class="sxs-lookup"><span data-stu-id="e0102-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="e0102-107">[in] `true` provádět ověřování, i když je nutné přepsat nastavení registru. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e0102-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="e0102-108">pro Ukazatel na mapování z veřejného klíče ECMA na skutečný klíč, který se používá k ověření.</span><span class="sxs-lookup"><span data-stu-id="e0102-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="e0102-109">pro Délka skutečného veřejného klíče ECMA</span><span class="sxs-lookup"><span data-stu-id="e0102-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="e0102-110">[out] `true`, jestli se podpis silného názvu ověřil; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e0102-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="e0102-111">Tento parametr je také nastaven na `false`, pokud bylo ověření úspěšné z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="e0102-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0102-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0102-112">Return Value</span></span>  
 <span data-ttu-id="e0102-113">`S_OK`, zda bylo ověření úspěšné; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="e0102-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0102-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0102-114">Requirements</span></span>  
 <span data-ttu-id="e0102-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0102-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0102-116">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e0102-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e0102-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e0102-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0102-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0102-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0102-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0102-119">See also</span></span>

- [<span data-ttu-id="e0102-120">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="e0102-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="e0102-121">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="e0102-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="e0102-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0102-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
