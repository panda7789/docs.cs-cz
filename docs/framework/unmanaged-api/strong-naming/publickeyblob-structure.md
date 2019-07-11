---
title: PublicKeyBlob – struktura
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75ba3fd634b108c996e848f48000ffcd0600b00c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774580"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="7c55d-102">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="7c55d-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="7c55d-103">Představuje veřejného klíče dvojice veřejného/soukromého klíče v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="7c55d-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c55d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c55d-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="7c55d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7c55d-105">Members</span></span>  
  
|<span data-ttu-id="7c55d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7c55d-106">Member</span></span>|<span data-ttu-id="7c55d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7c55d-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="7c55d-108">Identifikátor pro algoritmus podpisu (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="7c55d-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="7c55d-109">Identifikátor algoritmu hash (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="7c55d-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="7c55d-110">Délka klíče v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7c55d-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="7c55d-111">Proměnné délky bajtové pole obsahující hodnotu klíče ve formátu vrácený rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="7c55d-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c55d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c55d-112">Remarks</span></span>  
 <span data-ttu-id="7c55d-113">`PublicKeyBlob` Struktura používá [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)a další funkce silným názvem k reprezentaci veřejného klíče dvojice veřejného/soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="7c55d-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c55d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c55d-114">Requirements</span></span>  
 <span data-ttu-id="7c55d-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c55d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c55d-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="7c55d-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7c55d-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c55d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c55d-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c55d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c55d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c55d-119">See also</span></span>

- [<span data-ttu-id="7c55d-120">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="7c55d-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="7c55d-121">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="7c55d-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
