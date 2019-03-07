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
ms.openlocfilehash: 78829d647e8d5467a628bc9ba5bb877a5f13b6de
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474485"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="45271-102">ICLRStrongName::StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="45271-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="45271-103">Vrátí velikost položky podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="45271-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="45271-104">Tato metoda se obvykle používá kompilátory, chcete-li určit, kolik místa vyhradit v souboru při vytváření sestavení se zpožděným podpisem.</span><span class="sxs-lookup"><span data-stu-id="45271-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45271-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45271-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="45271-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="45271-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="45271-107">[in] Strukturu typu [publickeyblob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) obsahující veřejnou část páru klíčů podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="45271-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="45271-108">[in] Velikost v bajtech, z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="45271-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="45271-109">[in] Počet bajtů vyžadovaných k uložení podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="45271-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45271-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="45271-110">Return Value</span></span>  
 <span data-ttu-id="45271-111">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="45271-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45271-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45271-112">Requirements</span></span>  
 <span data-ttu-id="45271-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45271-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45271-114">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="45271-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="45271-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45271-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45271-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45271-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45271-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45271-117">See also</span></span>
- [<span data-ttu-id="45271-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45271-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
