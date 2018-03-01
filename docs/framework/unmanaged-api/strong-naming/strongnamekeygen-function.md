---
title: "StrongNameKeyGen – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e3bb9530884f61345d439ec8662a088e1d152de7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="3ff7f-102">StrongNameKeyGen – funkce</span><span class="sxs-lookup"><span data-stu-id="3ff7f-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="3ff7f-103">Vytvoří nový pár veřejného a privátního klíče pro silné jméno použití.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="3ff7f-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-104">This function has been deprecated.</span></span> <span data-ttu-id="3ff7f-105">Použití [iclrstrongname::strongnamekeygen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff7f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ff7f-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ff7f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ff7f-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="3ff7f-108">[v] Název požadovaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-108">[in] The requested key container name.</span></span> <span data-ttu-id="3ff7f-109">`wszKeyContainer`musí být neprázdný řetězec, nebo hodnotu null pro generování dočasný název.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3ff7f-110">[v] Určuje, jestli chcete nechat klíč zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="3ff7f-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="3ff7f-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="3ff7f-112">0x00000000 - použít, když `wszKeyContainer` má hodnotu null při generování názvu dočasné kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="3ff7f-113">0x00000001 (`SN_LEAVE_KEY`)-určuje, které by měl být klíč vlevo registrován.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="3ff7f-114">[out] Vrácený veřejného a privátního klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="3ff7f-115">[out] Velikost v bajtech z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ff7f-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3ff7f-116">Return Value</span></span>  
 <span data-ttu-id="3ff7f-117">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ff7f-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ff7f-118">Remarks</span></span>  
 <span data-ttu-id="3ff7f-119">`StrongNameKeyGen` Funkce vytvoří klíč 1024 bitů.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="3ff7f-120">Po načtení klíč by měly volat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce k uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="3ff7f-121">Pokud `StrongNameKeyGen` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="3ff7f-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ff7f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ff7f-122">Requirements</span></span>  
 <span data-ttu-id="3ff7f-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ff7f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ff7f-124">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3ff7f-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3ff7f-125">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ff7f-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ff7f-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ff7f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff7f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ff7f-127">See Also</span></span>  
 [<span data-ttu-id="3ff7f-128">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff7f-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="3ff7f-129">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="3ff7f-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="3ff7f-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ff7f-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
