---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5abc09f06bfd2aec270e5ef91fd4778d6aa9a3b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487366"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="ba5b2-102">ICLRStrongName::StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ba5b2-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="ba5b2-103">Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí představující token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba5b2-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba5b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba5b2-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ba5b2-106">[in] Cesta k souboru (PE portable executable) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="ba5b2-107">[out] Token vrácený silného názvu.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="ba5b2-108">[out] Velikost v bajtech, silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ba5b2-109">[out] Vrácené veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ba5b2-110">[out] Velikost v bajtech, veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba5b2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba5b2-111">Return Value</span></span>  
 <span data-ttu-id="ba5b2-112">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="ba5b2-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba5b2-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba5b2-113">Remarks</span></span>  
 <span data-ttu-id="ba5b2-114">Zkráceným tvarem veřejný klíč je token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="ba5b2-115">Token je hodnota hash 64-bit, který je vytvořen z veřejného klíče použitý k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="ba5b2-116">Token, který je součástí silného názvu pro sestavení a může číst z metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="ba5b2-117">Poté, co načítání klíče a token, který je vytvořen, měli byste zavolat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="ba5b2-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba5b2-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba5b2-118">Requirements</span></span>  
 <span data-ttu-id="ba5b2-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba5b2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba5b2-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ba5b2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ba5b2-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba5b2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba5b2-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba5b2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5b2-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba5b2-123">See also</span></span>
- [<span data-ttu-id="ba5b2-124">StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="ba5b2-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="ba5b2-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba5b2-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
