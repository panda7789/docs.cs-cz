---
title: "StrongNameKeyGenEx – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyGenEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyGenEx
helpviewer_keywords: StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87841c230c71650f822a6cb2f6cc3f3c17c2ef35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="50959-102">StrongNameKeyGenEx – funkce</span><span class="sxs-lookup"><span data-stu-id="50959-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="50959-103">Generuje nový pár veřejného a privátního klíče pomocí zadané velikost klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="50959-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="50959-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="50959-104">This function has been deprecated.</span></span> <span data-ttu-id="50959-105">Použití [iclrstrongname::strongnamekeygenex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="50959-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50959-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50959-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50959-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="50959-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="50959-108">[v] Název požadovaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="50959-108">[in] The requested key container name.</span></span> <span data-ttu-id="50959-109">`wszKeyContainer`musí být neprázdný řetězec, nebo hodnotu null pro generování dočasný název.</span><span class="sxs-lookup"><span data-stu-id="50959-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="50959-110">[v] Určuje, jestli chcete nechat klíč zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="50959-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="50959-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="50959-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="50959-112">0x00000000 - použít, když `wszKeyContainer` má hodnotu null při generování názvu dočasné kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="50959-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="50959-113">0x00000001 (`SN_LEAVE_KEY`)-určuje, které by měl být klíč vlevo registrován.</span><span class="sxs-lookup"><span data-stu-id="50959-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="50959-114">[v] Požadovaná velikost klíče v bitech.</span><span class="sxs-lookup"><span data-stu-id="50959-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="50959-115">[out] Vrácený veřejného a privátního klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="50959-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="50959-116">[out] Velikost v bajtech z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="50959-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50959-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="50959-117">Return Value</span></span>  
 <span data-ttu-id="50959-118">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="50959-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50959-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50959-119">Remarks</span></span>  
 <span data-ttu-id="50959-120">Vyžadují rozhraní .NET Framework verze 1.0 a 1.1 `dwKeySize` 1 024 bitů pro podepsání sestavení silným názvem; verze 2.0 přidá podporuje pro klíče 2048 bitů.</span><span class="sxs-lookup"><span data-stu-id="50959-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="50959-121">Po načtení klíč by měly volat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce k uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="50959-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="50959-122">Pokud `StrongNameKeyGenEx` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="50959-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50959-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50959-123">Requirements</span></span>  
 <span data-ttu-id="50959-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50959-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50959-125">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="50959-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="50959-126">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50959-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50959-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50959-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50959-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="50959-128">See Also</span></span>  
 [<span data-ttu-id="50959-129">Strongnamekeygenex – metoda</span><span class="sxs-lookup"><span data-stu-id="50959-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="50959-130">Strongnamekeygen – metoda</span><span class="sxs-lookup"><span data-stu-id="50959-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="50959-131">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50959-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
