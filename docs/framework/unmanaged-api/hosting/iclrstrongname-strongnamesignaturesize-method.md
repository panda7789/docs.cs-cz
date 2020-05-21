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
ms.openlocfilehash: edce771b3c36f2c56637aa2a21fe524be0ae12c8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763017"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="7263d-102">ICLRStrongName::StrongNameSignatureSize – metoda</span><span class="sxs-lookup"><span data-stu-id="7263d-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="7263d-103">Vrátí velikost podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="7263d-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="7263d-104">Tato metoda je obvykle používána kompilátory k určení, kolik místa lze v souboru vyhradit při vytváření sestavení se zpožděným podpisem.</span><span class="sxs-lookup"><span data-stu-id="7263d-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7263d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7263d-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="7263d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7263d-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="7263d-107">pro Struktura typu [PublicKeyBlob –](../strong-naming/publickeyblob-structure.md) , která obsahuje veřejnou část páru klíčů sloužící k vygenerování podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="7263d-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="7263d-108">pro Velikost v bajtech `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="7263d-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="7263d-109">pro Počet bajtů vyžadovaných k uložení podpisu silného názvu.</span><span class="sxs-lookup"><span data-stu-id="7263d-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7263d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7263d-110">Return Value</span></span>  
 <span data-ttu-id="7263d-111">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="7263d-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7263d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7263d-112">Requirements</span></span>  
 <span data-ttu-id="7263d-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7263d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7263d-114">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7263d-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7263d-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7263d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7263d-116">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7263d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7263d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7263d-117">See also</span></span>

- [<span data-ttu-id="7263d-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7263d-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
