---
title: ICLRStrongName2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: 9715369f4cf1b2a7078be14a2fc597f735ab6fd3
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763160"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="2bf12-102">ICLRStrongName2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bf12-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="2bf12-103">Poskytuje možnost vytvářet silné názvy pomocí skupiny SHA-2 algoritmů Secure Hash (SHA-256, SHA-384 a SHA-512).</span><span class="sxs-lookup"><span data-stu-id="2bf12-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bf12-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2bf12-104">Methods</span></span>  
  
|<span data-ttu-id="2bf12-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2bf12-105">Method</span></span>|<span data-ttu-id="2bf12-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2bf12-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bf12-107">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="2bf12-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="2bf12-108">Získá veřejný klíč z páru veřejného a privátního klíče a určí algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="2bf12-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="2bf12-109">StrongNameSignatureVerificationEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2bf12-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="2bf12-110">Ověří podpis silně pojmenovaného sestavení a poskytuje mapování z klíče ECMA na skutečný klíč.</span><span class="sxs-lookup"><span data-stu-id="2bf12-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bf12-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bf12-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bf12-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bf12-112">Requirements</span></span>  
 <span data-ttu-id="2bf12-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bf12-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bf12-114">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="2bf12-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2bf12-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2bf12-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bf12-116">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bf12-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
