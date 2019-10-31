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
ms.openlocfilehash: 6c58a0726e0869178838999c6b000e0ad975f145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140615"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="037ae-102">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="037ae-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="037ae-103">Představuje v binárním formátu veřejný klíč páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="037ae-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="037ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="037ae-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="037ae-105">Členové</span><span class="sxs-lookup"><span data-stu-id="037ae-105">Members</span></span>  
  
|<span data-ttu-id="037ae-106">Člen</span><span class="sxs-lookup"><span data-stu-id="037ae-106">Member</span></span>|<span data-ttu-id="037ae-107">Popis</span><span class="sxs-lookup"><span data-stu-id="037ae-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="037ae-108">Identifikátor algoritmu podpisu (typu `ALG_ID`, jak je definován v WinCrypt. h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="037ae-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="037ae-109">Identifikátor algoritmu hash (typu `ALG_ID`, jak je definován v WinCrypt. h) veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="037ae-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="037ae-110">Délka klíče v bajtech</span><span class="sxs-lookup"><span data-stu-id="037ae-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="037ae-111">Bajtové pole s proměnlivou délkou, které obsahuje hodnotu klíče ve formátu vráceném rozhraním CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="037ae-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="037ae-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="037ae-112">Remarks</span></span>  
 <span data-ttu-id="037ae-113">`PublicKeyBlob` struktura se používá v [StrongNameGetPublicKey –](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration –](strongnamesignaturegeneration-function.md)a dalších funkcích se silným názvem, které reprezentují veřejný klíč páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="037ae-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="037ae-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="037ae-114">Requirements</span></span>  
 <span data-ttu-id="037ae-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="037ae-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="037ae-116">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="037ae-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="037ae-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="037ae-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="037ae-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="037ae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="037ae-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="037ae-119">See also</span></span>

- [<span data-ttu-id="037ae-120">StrongNameGetPublicKey – funkce</span><span class="sxs-lookup"><span data-stu-id="037ae-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="037ae-121">StrongNameSignatureGeneration – funkce</span><span class="sxs-lookup"><span data-stu-id="037ae-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
