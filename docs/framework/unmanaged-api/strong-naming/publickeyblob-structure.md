---
title: "PublicKeyBlob – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PublicKeyBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: PublicKeyBlob
helpviewer_keywords: PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e273570c77b2855d942db580be95b040870a4c01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="94169-102">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="94169-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="94169-103">Představuje veřejný klíč pár veřejného a privátního klíče v binárním formátu.</span><span class="sxs-lookup"><span data-stu-id="94169-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94169-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94169-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="94169-105">Členové</span><span class="sxs-lookup"><span data-stu-id="94169-105">Members</span></span>  
  
|<span data-ttu-id="94169-106">Člen</span><span class="sxs-lookup"><span data-stu-id="94169-106">Member</span></span>|<span data-ttu-id="94169-107">Popis</span><span class="sxs-lookup"><span data-stu-id="94169-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="94169-108">Identifikátor pro algoritmus podpisu (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="94169-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="94169-109">Identifikátor pro algoritmus hash (typu `ALG_ID`, jak jsou definovány v WinCrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="94169-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="94169-110">Délka klíče v bajtech.</span><span class="sxs-lookup"><span data-stu-id="94169-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="94169-111">Proměnnou délkou bajtové pole, která obsahuje hodnotu klíče ve formátu vrácený rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="94169-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94169-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94169-112">Remarks</span></span>  
 <span data-ttu-id="94169-113">`PublicKeyBlob` Struktura používá [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)a další funkce silným názvem představují veřejný klíč pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="94169-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94169-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94169-114">Requirements</span></span>  
 <span data-ttu-id="94169-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94169-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94169-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="94169-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="94169-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94169-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94169-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94169-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94169-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="94169-119">See Also</span></span>  
 [<span data-ttu-id="94169-120">Strongnamegetpublickey – funkce</span><span class="sxs-lookup"><span data-stu-id="94169-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [<span data-ttu-id="94169-121">Strongnamesignaturegeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="94169-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [<span data-ttu-id="94169-122">Silné názvy struktury</span><span class="sxs-lookup"><span data-stu-id="94169-122">Strong Naming Structures</span></span>](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
