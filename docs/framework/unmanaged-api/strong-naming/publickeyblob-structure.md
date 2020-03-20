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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176952"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="6ae32-102">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="6ae32-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="6ae32-103">Představuje v binárním formátu veřejný klíč dvojice veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="6ae32-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ae32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ae32-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="6ae32-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6ae32-105">Members</span></span>  
  
|<span data-ttu-id="6ae32-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6ae32-106">Member</span></span>|<span data-ttu-id="6ae32-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6ae32-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="6ae32-108">Identifikátor podpisového algoritmu (typu `ALG_ID`, jak je definován ve wincrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="6ae32-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="6ae32-109">Identifikátor algoritmu hash (typu `ALG_ID`, jak je definován ve wincrypt.h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="6ae32-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="6ae32-110">Délka klíče v bajtů.</span><span class="sxs-lookup"><span data-stu-id="6ae32-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="6ae32-111">Pole bajtů s proměnnou délkou, které obsahuje hodnotu klíče ve formátu vráceném rozhraním CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="6ae32-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ae32-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ae32-112">Remarks</span></span>  
 <span data-ttu-id="6ae32-113">Struktura `PublicKeyBlob` je používána [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)a další funkce silného názvu představují veřejný klíč dvojice veřejného a soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="6ae32-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ae32-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ae32-114">Requirements</span></span>  
 <span data-ttu-id="6ae32-115">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ae32-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ae32-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6ae32-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6ae32-117">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ae32-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ae32-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ae32-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae32-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ae32-119">See also</span></span>

- [<span data-ttu-id="6ae32-120">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="6ae32-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="6ae32-121">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="6ae32-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
