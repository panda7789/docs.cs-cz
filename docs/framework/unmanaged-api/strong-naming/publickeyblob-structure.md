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
ms.openlocfilehash: e66196e2bd2cb326ca3f5badc67bcf8d81e5fc3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799171"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="18b0c-102">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="18b0c-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="18b0c-103">Představuje v binárním formátu veřejný klíč páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="18b0c-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18b0c-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="18b0c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="18b0c-105">Members</span></span>  
  
|<span data-ttu-id="18b0c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="18b0c-106">Member</span></span>|<span data-ttu-id="18b0c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="18b0c-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="18b0c-108">Identifikátor algoritmu podpisu (typu `ALG_ID`, jak je definován v Wincrypt. h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="18b0c-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="18b0c-109">Identifikátor algoritmu hash (typu `ALG_ID`, jak je definován v Wincrypt. h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="18b0c-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="18b0c-110">Délka klíče v bajtech</span><span class="sxs-lookup"><span data-stu-id="18b0c-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="18b0c-111">Bajtové pole s proměnlivou délkou, které obsahuje hodnotu klíče ve formátu vráceném rozhraním CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="18b0c-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18b0c-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18b0c-112">Remarks</span></span>  
 <span data-ttu-id="18b0c-113">Strukturu používá StrongNameGetPublicKey –, [StrongNameSignatureGeneration –](strongnamesignaturegeneration-function.md)a další funkce se silným názvem, které reprezentují veřejný klíč páru veřejného a privátního klíče. [](strongnamegetpublickey-function.md) `PublicKeyBlob`</span><span class="sxs-lookup"><span data-stu-id="18b0c-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b0c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18b0c-114">Requirements</span></span>  
 <span data-ttu-id="18b0c-115">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18b0c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b0c-116">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="18b0c-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="18b0c-117">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="18b0c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18b0c-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18b0c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b0c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18b0c-119">See also</span></span>

- [<span data-ttu-id="18b0c-120">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="18b0c-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="18b0c-121">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="18b0c-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
