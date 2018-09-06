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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc5a40a0e26f116ce1700973a5000e8d6bbbd890
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732935"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="1f77d-102">ICLRStrongName::StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="1f77d-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="1f77d-103">Vrátí velikost položky podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="1f77d-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="1f77d-104">Tato metoda se obvykle používá kompilátory, chcete-li určit, kolik místa vyhradit v souboru při vytváření sestavení se zpožděným podpisem.</span><span class="sxs-lookup"><span data-stu-id="1f77d-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f77d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f77d-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f77d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f77d-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="1f77d-107">[in] Strukturu typu [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="1f77d-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="1f77d-108">[in] Velikost v bajtech, z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="1f77d-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="1f77d-109">[in] Počet bajtů vyžadovaných k uložení podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="1f77d-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f77d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1f77d-110">Return Value</span></span>  
 <span data-ttu-id="1f77d-111">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="1f77d-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f77d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f77d-112">Requirements</span></span>  
 <span data-ttu-id="1f77d-113">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f77d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f77d-114">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1f77d-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1f77d-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f77d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f77d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f77d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f77d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f77d-117">See Also</span></span>  
 [<span data-ttu-id="1f77d-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f77d-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
