---
title: ICLRStrongName::StrongNameTokenFromAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: 0e7e49fae24ff7e12c5a8d9cac5e814f7a7ae813
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092595"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="79e2d-102">ICLRStrongName::StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="79e2d-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="79e2d-103">Vytvoří ze zadaného souboru sestavení token se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="79e2d-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79e2d-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79e2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79e2d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="79e2d-106">pro Cesta k přenosnému spustitelnému souboru (PE) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="79e2d-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="79e2d-107">mimo Vrácený token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="79e2d-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="79e2d-108">mimo Velikost tokenu silného názvu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="79e2d-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79e2d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="79e2d-109">Return Value</span></span>  
 <span data-ttu-id="79e2d-110">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="79e2d-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79e2d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79e2d-111">Remarks</span></span>  
 <span data-ttu-id="79e2d-112">Token silného názvu je zkrácenou formou veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="79e2d-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="79e2d-113">Token je 64 hodnota hash, která je vytvořena z veřejného klíče použitého k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="79e2d-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="79e2d-114">Token je součástí silného názvu sestavení a lze ho číst z metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="79e2d-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="79e2d-115">Po vytvoření tokenu byste měli zavolat metodu [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="79e2d-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79e2d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79e2d-116">Requirements</span></span>  
 <span data-ttu-id="79e2d-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79e2d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79e2d-118">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="79e2d-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="79e2d-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="79e2d-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79e2d-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79e2d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e2d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79e2d-121">See also</span></span>

- [<span data-ttu-id="79e2d-122">StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="79e2d-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="79e2d-123">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79e2d-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
