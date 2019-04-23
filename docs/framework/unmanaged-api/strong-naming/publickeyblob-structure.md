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
ms.openlocfilehash: 1a361e04b6f8f39ec0083471d8cb47d5a29376c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214816"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="83b3e-102">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="83b3e-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="83b3e-103">Představuje veřejného klíče dvojice veřejného/soukromého klíče v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="83b3e-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83b3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83b3e-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="83b3e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="83b3e-105">Members</span></span>  
  
|<span data-ttu-id="83b3e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="83b3e-106">Member</span></span>|<span data-ttu-id="83b3e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="83b3e-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="83b3e-108">Identifikátor pro algoritmus podpisu (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="83b3e-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="83b3e-109">Identifikátor algoritmu hash (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="83b3e-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="83b3e-110">Délka klíče v bajtech.</span><span class="sxs-lookup"><span data-stu-id="83b3e-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="83b3e-111">Proměnné délky bajtové pole obsahující hodnotu klíče ve formátu vrácený rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="83b3e-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83b3e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83b3e-112">Remarks</span></span>  
 <span data-ttu-id="83b3e-113">`PublicKeyBlob` Struktura používá [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)a další funkce silným názvem k reprezentaci veřejného klíče dvojice veřejného/soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="83b3e-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83b3e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83b3e-114">Requirements</span></span>  
 <span data-ttu-id="83b3e-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83b3e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83b3e-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="83b3e-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="83b3e-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83b3e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83b3e-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83b3e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b3e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83b3e-119">See also</span></span>

- [<span data-ttu-id="83b3e-120">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="83b3e-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="83b3e-121">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="83b3e-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
