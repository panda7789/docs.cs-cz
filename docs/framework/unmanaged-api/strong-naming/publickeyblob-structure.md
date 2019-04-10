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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214816"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="0e76a-102">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="0e76a-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="0e76a-103">Představuje veřejného klíče dvojice veřejného/soukromého klíče v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="0e76a-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e76a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e76a-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="0e76a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0e76a-105">Members</span></span>  
  
|<span data-ttu-id="0e76a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0e76a-106">Member</span></span>|<span data-ttu-id="0e76a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0e76a-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="0e76a-108">Identifikátor pro algoritmus podpisu (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="0e76a-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="0e76a-109">Identifikátor algoritmu hash (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="0e76a-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="0e76a-110">Délka klíče v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0e76a-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="0e76a-111">Proměnné délky bajtové pole obsahující hodnotu klíče ve formátu vrácený rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="0e76a-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e76a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e76a-112">Remarks</span></span>  
 <span data-ttu-id="0e76a-113">`PublicKeyBlob` Struktura používá [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)a další funkce silným názvem k reprezentaci veřejného klíče dvojice veřejného/soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="0e76a-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e76a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e76a-114">Requirements</span></span>  
 <span data-ttu-id="0e76a-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e76a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e76a-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0e76a-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0e76a-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e76a-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0e76a-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0e76a-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e76a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e76a-119">See also</span></span>

- [<span data-ttu-id="0e76a-120">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="0e76a-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="0e76a-121">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="0e76a-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
