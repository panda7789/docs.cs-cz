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
ms.openlocfilehash: 1a5e18c0cf65ee8f336b74a2d8e44fcf5af0cfef
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261775"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="8fc29-102">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="8fc29-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="8fc29-103">Představuje veřejného klíče dvojice veřejného/soukromého klíče v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="8fc29-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fc29-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="8fc29-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8fc29-105">Members</span></span>  
  
|<span data-ttu-id="8fc29-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8fc29-106">Member</span></span>|<span data-ttu-id="8fc29-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8fc29-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="8fc29-108">Identifikátor pro algoritmus podpisu (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="8fc29-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="8fc29-109">Identifikátor algoritmu hash (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="8fc29-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="8fc29-110">Délka klíče v bajtech.</span><span class="sxs-lookup"><span data-stu-id="8fc29-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="8fc29-111">Proměnné délky bajtové pole obsahující hodnotu klíče ve formátu vrácený rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="8fc29-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fc29-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fc29-112">Remarks</span></span>  
 <span data-ttu-id="8fc29-113">`PublicKeyBlob` Struktura používá [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)a další funkce silným názvem k reprezentaci veřejného klíče dvojice veřejného/soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="8fc29-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc29-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fc29-114">Requirements</span></span>  
 <span data-ttu-id="8fc29-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc29-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc29-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="8fc29-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8fc29-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fc29-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8fc29-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc29-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc29-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fc29-119">See also</span></span>
- [<span data-ttu-id="8fc29-120">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="8fc29-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="8fc29-121">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="8fc29-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
