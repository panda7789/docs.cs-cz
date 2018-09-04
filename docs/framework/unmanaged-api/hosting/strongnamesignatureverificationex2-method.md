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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e47c2ac69317b2d2db489dce9a0102b5fe304c05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556595"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="51994-102">StrongNameSignatureVerificationEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="51994-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="51994-103">Ověří podpis sestavení se silným názvem a poskytuje mapování z klíče ECMA skutečné klíče.</span><span class="sxs-lookup"><span data-stu-id="51994-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51994-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51994-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51994-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51994-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="51994-106">[in] Cesta k přenositelný spustitelný soubor (.exe nebo .dll) soubor pro sestavení, který se má ověřit.</span><span class="sxs-lookup"><span data-stu-id="51994-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="51994-107">[in] `true` provádět ověřování, i když je potřeba přepsat nastavení registru; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="51994-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="51994-108">[in] Ukazatel na mapování z veřejného klíče ECMA skutečné klíče používané pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="51994-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="51994-109">[in] Délka skutečné ECMA veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="51994-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="51994-110">[out] `true` Pokud byl podpis silného názvu ověřené; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="51994-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="51994-111">Tento parametr je také nastavena na `false` Pokud bude ověření úspěšné z důvodu nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="51994-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51994-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51994-112">Return Value</span></span>  
 <span data-ttu-id="51994-113">`S_OK` Pokud bude ověření úspěšné; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="51994-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51994-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51994-114">Requirements</span></span>  
 <span data-ttu-id="51994-115">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51994-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51994-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="51994-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="51994-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51994-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51994-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51994-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51994-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="51994-119">See Also</span></span>  
 [<span data-ttu-id="51994-120">StrongNameSignatureVerification – metoda</span><span class="sxs-lookup"><span data-stu-id="51994-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="51994-121">StrongNameSignatureVerificationEx – metoda</span><span class="sxs-lookup"><span data-stu-id="51994-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="51994-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51994-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
