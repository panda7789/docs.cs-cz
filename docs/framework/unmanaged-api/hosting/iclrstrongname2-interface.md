---
title: "ICLRStrongName2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName2
helpviewer_keywords: ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9e9a88f1064c888d60e363be569d06458299143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="cccb0-102">ICLRStrongName2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cccb0-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="cccb0-103">Poskytuje možnost vytvořit silné názvy pomocí skupiny zabezpečení (SHA-256, SHA-384 a SHA-512) algoritmy Hash SHA-2.</span><span class="sxs-lookup"><span data-stu-id="cccb0-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cccb0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cccb0-104">Methods</span></span>  
  
|<span data-ttu-id="cccb0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cccb0-105">Method</span></span>|<span data-ttu-id="cccb0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cccb0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cccb0-107">Strongnamegetpublickeyex – metoda</span><span class="sxs-lookup"><span data-stu-id="cccb0-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="cccb0-108">Získá veřejný klíč z páru veřejného a privátního klíče RSA a určuje algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="cccb0-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="cccb0-109">Strongnamesignatureverificationex2 – metoda</span><span class="sxs-lookup"><span data-stu-id="cccb0-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="cccb0-110">Ověří podpis silně pojmenované sestavení a poskytuje mapování z klíče ECMA skutečné klíče.</span><span class="sxs-lookup"><span data-stu-id="cccb0-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cccb0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cccb0-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cccb0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cccb0-112">Requirements</span></span>  
 <span data-ttu-id="cccb0-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cccb0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cccb0-114">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cccb0-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cccb0-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cccb0-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cccb0-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cccb0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
