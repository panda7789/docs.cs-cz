---
title: "StrongNameTokenFromAssemblyEx – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromAssemblyEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameTokenFromAssemblyEx
helpviewer_keywords: StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef530595d92995124c590e70ac5ffc32a228c67a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="3e3af-102">StrongNameTokenFromAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="3e3af-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="3e3af-103">Vytvoří token silným názvem ze zadaného souboru sestavení a vrátí veřejný klíč, který představuje daný token.</span><span class="sxs-lookup"><span data-stu-id="3e3af-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="3e3af-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3e3af-104">This function has been deprecated.</span></span> <span data-ttu-id="3e3af-105">Použití [iclrstrongname::strongnametokenfromassemblyex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="3e3af-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3af-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e3af-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e3af-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e3af-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3e3af-108">[v] Cesta k souboru přenosné spustitelný soubor (PE) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e3af-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="3e3af-109">[out] Token vrácený silným názvem.</span><span class="sxs-lookup"><span data-stu-id="3e3af-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="3e3af-110">[out] Velikost v bajtech, silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="3e3af-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="3e3af-111">[out] Vrácený veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="3e3af-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="3e3af-112">[out] Velikost v bajtech, veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="3e3af-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e3af-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e3af-113">Return Value</span></span>  
 <span data-ttu-id="3e3af-114">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="3e3af-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e3af-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e3af-115">Remarks</span></span>  
 <span data-ttu-id="3e3af-116">Zkrácený tvar veřejný klíč je token silným názvem.</span><span class="sxs-lookup"><span data-stu-id="3e3af-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="3e3af-117">Token je 64 bitů hodnotu hash, který je vytvořený z veřejný klíč používaný k podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e3af-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="3e3af-118">Token je součástí silného názvu pro sestavení a můžete číst z metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e3af-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="3e3af-119">Jakmile načítání klíče a token je vytvořen, by měly volat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce k uvolnění přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="3e3af-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="3e3af-120">Pokud `StrongNameTokenFromAssemblyEx` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="3e3af-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e3af-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e3af-121">Requirements</span></span>  
 <span data-ttu-id="3e3af-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e3af-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e3af-123">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3e3af-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3e3af-124">**Knihovna:** zahrnuty jako prostředek v mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3e3af-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="3e3af-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e3af-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e3af-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e3af-126">See Also</span></span>  
 [<span data-ttu-id="3e3af-127">Strongnametokenfromassemblyex – metoda</span><span class="sxs-lookup"><span data-stu-id="3e3af-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="3e3af-128">Strongnametokenfromassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="3e3af-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="3e3af-129">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e3af-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
