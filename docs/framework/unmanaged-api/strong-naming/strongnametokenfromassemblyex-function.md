---
title: StrongNameTokenFromAssemblyEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f95ac4e4c21a2cbaab9f91c1257a868bdce65af
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499183"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="9670b-102">StrongNameTokenFromAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="9670b-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="9670b-103">Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí představující token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9670b-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="9670b-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="9670b-104">This function has been deprecated.</span></span> <span data-ttu-id="9670b-105">Použití [iclrstrongname::strongnametokenfromassemblyex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="9670b-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9670b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9670b-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9670b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9670b-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="9670b-108">[in] Cesta k souboru (PE portable executable) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="9670b-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="9670b-109">[out] Token vrácený silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9670b-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="9670b-110">[out] Velikost v bajtech, silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="9670b-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="9670b-111">[out] Vrácené veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="9670b-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="9670b-112">[out] Velikost v bajtech, veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9670b-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9670b-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9670b-113">Return Value</span></span>  
 <span data-ttu-id="9670b-114">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="9670b-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9670b-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9670b-115">Remarks</span></span>  
 <span data-ttu-id="9670b-116">Zkráceným tvarem veřejný klíč je token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9670b-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="9670b-117">Token je hodnota hash 64-bit, který je vytvořen z veřejného klíče použitý k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="9670b-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="9670b-118">Token, který je součástí silného názvu pro sestavení a může číst z metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="9670b-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="9670b-119">Poté, co načítání klíče a token, který je vytvořen, měli byste zavolat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce přidělená paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="9670b-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="9670b-120">Pokud `StrongNameTokenFromAssemblyEx` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="9670b-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9670b-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9670b-121">Requirements</span></span>  
 <span data-ttu-id="9670b-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9670b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9670b-123">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9670b-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9670b-124">**Knihovna:** Zahrnuté jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9670b-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="9670b-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9670b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9670b-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9670b-126">See also</span></span>
- [<span data-ttu-id="9670b-127">StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="9670b-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="9670b-128">StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="9670b-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="9670b-129">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9670b-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
