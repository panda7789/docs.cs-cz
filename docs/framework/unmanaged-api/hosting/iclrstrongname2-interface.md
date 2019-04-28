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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf9e3d2df8f507e118b393007c3958358a830cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763721"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="5c7c4-102">ICLRStrongName2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c7c4-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="5c7c4-103">Umožňuje vytvořit silné názvy pomocí algoritmu SHA-2 skupiny Hashovacích algoritmů zabezpečení (SHA-256, SHA-384 a SHA-512).</span><span class="sxs-lookup"><span data-stu-id="5c7c4-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c7c4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5c7c4-104">Methods</span></span>  
  
|<span data-ttu-id="5c7c4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5c7c4-105">Method</span></span>|<span data-ttu-id="5c7c4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5c7c4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c7c4-107">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="5c7c4-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="5c7c4-108">Získá veřejný klíč z dvojice veřejného/soukromého klíče a určuje algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="5c7c4-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="5c7c4-109">StrongNameSignatureVerificationEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5c7c4-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="5c7c4-110">Ověří podpis sestavení se silným názvem a poskytuje mapování z klíče ECMA skutečné klíče.</span><span class="sxs-lookup"><span data-stu-id="5c7c4-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c7c4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c7c4-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c7c4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c7c4-112">Requirements</span></span>  
 <span data-ttu-id="5c7c4-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c7c4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c7c4-114">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5c7c4-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5c7c4-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c7c4-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c7c4-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c7c4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
