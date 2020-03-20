---
title: ICLRStrongName::StrongNameSignatureSize – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: e789996af3aedd17251fc52cde52a336f65053ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176341"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="66c79-102">ICLRStrongName::StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="66c79-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="66c79-103">Vrátí velikost podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="66c79-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="66c79-104">Tato metoda se obvykle používá kompilátory k určení, kolik místa rezervovat v souboru při vytváření sestavení podepsané zpoždění.</span><span class="sxs-lookup"><span data-stu-id="66c79-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c79-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66c79-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="66c79-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="66c79-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="66c79-107">[v] Struktura typu [PublicKeyBlob,](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) který obsahuje veřejnou část dvojice klíčů slouží ke generování podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="66c79-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="66c79-108">[v] Velikost v bajtů `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="66c79-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="66c79-109">[v] Počet bajtů potřebných k uložení podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="66c79-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66c79-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="66c79-110">Return Value</span></span>  
 <span data-ttu-id="66c79-111">`S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="66c79-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c79-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66c79-112">Requirements</span></span>  
 <span data-ttu-id="66c79-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c79-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c79-114">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="66c79-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="66c79-115">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66c79-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66c79-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c79-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c79-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="66c79-117">See also</span></span>

- [<span data-ttu-id="66c79-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c79-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
