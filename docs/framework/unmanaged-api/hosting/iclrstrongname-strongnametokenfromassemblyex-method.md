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
ms.openlocfilehash: f08006c532d2778de67a4bab09623d248362535c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937432"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="01cdf-102">ICLRStrongName::StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="01cdf-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="01cdf-103">Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč, který token představuje.</span><span class="sxs-lookup"><span data-stu-id="01cdf-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01cdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01cdf-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01cdf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01cdf-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="01cdf-106">pro Cesta k přenosnému spustitelnému souboru (PE) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="01cdf-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="01cdf-107">mimo Vrácený token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="01cdf-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="01cdf-108">mimo Velikost tokenu silného názvu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="01cdf-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="01cdf-109">mimo Vrácený veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="01cdf-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="01cdf-110">mimo Velikost veřejného klíče v bajtech.</span><span class="sxs-lookup"><span data-stu-id="01cdf-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01cdf-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="01cdf-111">Return Value</span></span>  
 <span data-ttu-id="01cdf-112">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="01cdf-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01cdf-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01cdf-113">Remarks</span></span>  
 <span data-ttu-id="01cdf-114">Token silného názvu je zkrácenou formou veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="01cdf-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="01cdf-115">Token je 64 hodnota hash, která je vytvořena z veřejného klíče použitého k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="01cdf-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="01cdf-116">Token je součástí silného názvu sestavení a lze ho číst z metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="01cdf-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="01cdf-117">Po načtení klíče a vytvoření tokenu byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="01cdf-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01cdf-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01cdf-118">Requirements</span></span>  
 <span data-ttu-id="01cdf-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01cdf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01cdf-120">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="01cdf-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="01cdf-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01cdf-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01cdf-122">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01cdf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01cdf-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01cdf-123">See also</span></span>

- [<span data-ttu-id="01cdf-124">StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="01cdf-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="01cdf-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01cdf-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
