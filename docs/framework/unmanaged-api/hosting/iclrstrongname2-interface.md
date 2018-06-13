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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432970"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="0abcf-102">ICLRStrongName2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0abcf-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="0abcf-103">Poskytuje možnost vytvořit silné názvy pomocí skupiny zabezpečení (SHA-256, SHA-384 a SHA-512) algoritmy Hash SHA-2.</span><span class="sxs-lookup"><span data-stu-id="0abcf-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0abcf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0abcf-104">Methods</span></span>  
  
|<span data-ttu-id="0abcf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0abcf-105">Method</span></span>|<span data-ttu-id="0abcf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0abcf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0abcf-107">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="0abcf-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="0abcf-108">Získá veřejný klíč z páru veřejného a privátního klíče RSA a určuje algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="0abcf-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="0abcf-109">StrongNameSignatureVerificationEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="0abcf-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="0abcf-110">Ověří podpis silně pojmenované sestavení a poskytuje mapování z klíče ECMA skutečné klíče.</span><span class="sxs-lookup"><span data-stu-id="0abcf-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0abcf-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0abcf-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0abcf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0abcf-112">Requirements</span></span>  
 <span data-ttu-id="0abcf-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0abcf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0abcf-114">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0abcf-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0abcf-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0abcf-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0abcf-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0abcf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
