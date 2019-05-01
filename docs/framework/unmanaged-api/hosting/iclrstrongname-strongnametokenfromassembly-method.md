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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a2931c16e13d08c1e3e7d5b62e6583102a1b8cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984578"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="413a1-102">ICLRStrongName::StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="413a1-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="413a1-103">Vytvoří token silného názvu ze zadaného souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="413a1-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="413a1-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="413a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="413a1-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="413a1-106">[in] Cesta k souboru (PE portable executable) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="413a1-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="413a1-107">[out] Token vrácený silného názvu.</span><span class="sxs-lookup"><span data-stu-id="413a1-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="413a1-108">[out] Velikost v bajtech, silný název tokenu.</span><span class="sxs-lookup"><span data-stu-id="413a1-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="413a1-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="413a1-109">Return Value</span></span>  
 <span data-ttu-id="413a1-110">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="413a1-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="413a1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="413a1-111">Remarks</span></span>  
 <span data-ttu-id="413a1-112">Zkráceným tvarem veřejný klíč je token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="413a1-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="413a1-113">Token je hodnota hash 64-bit, který je vytvořen z veřejného klíče použitý k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="413a1-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="413a1-114">Token, který je součástí silného názvu pro sestavení a může číst z metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="413a1-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="413a1-115">Po vytvoření tokenu, měli byste zavolat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="413a1-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="413a1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="413a1-116">Requirements</span></span>  
 <span data-ttu-id="413a1-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="413a1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="413a1-118">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="413a1-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="413a1-119">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="413a1-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="413a1-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="413a1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413a1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="413a1-121">See also</span></span>

- [<span data-ttu-id="413a1-122">StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="413a1-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="413a1-123">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="413a1-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
