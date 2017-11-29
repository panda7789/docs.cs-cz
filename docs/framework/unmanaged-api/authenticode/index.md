---
title: "Authenticode (referenční dokumentace nespravovaného rozhraní API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e90a13ebf46f1891061c78435b7ba47d68de001d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="cc382-102">Authenticode (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="cc382-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="cc382-103">Podporuje modul vytvoření a ověření Authenticode XrML licence.</span><span class="sxs-lookup"><span data-stu-id="cc382-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc382-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cc382-104">In This Section</span></span>  
 [<span data-ttu-id="cc382-105">Funkce _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="cc382-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="cc382-106">Načte hodnotu hash SHA-1 veřejný klíč přidružený privátní klíč, který se používá k podepisování zadaný certifikát.</span><span class="sxs-lookup"><span data-stu-id="cc382-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="cc382-107">Funkce _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="cc382-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="cc382-108">Vypočítá silným názvem token veřejného klíče z formátu CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="cc382-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="cc382-109">Funkce _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="cc382-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="cc382-110">Převede Exponent a Modulus silný název tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="cc382-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="cc382-111">Funkce CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="cc382-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="cc382-112">Uvolní prostředky přidělené pro struktura AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="cc382-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="cc382-113">Funkce CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="cc382-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="cc382-114">Uvolní prostředky přidělené pro struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="cc382-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="cc382-115">Funkce CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="cc382-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="cc382-116">Časové značky licenci Authenticode XrML vytvořené CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="cc382-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="cc382-117">Funkce CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="cc382-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="cc382-118">Ověří platnost licence na Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="cc382-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="cc382-119">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="cc382-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="cc382-120">Definuje informace podepisující osoba Authenticode.</span><span class="sxs-lookup"><span data-stu-id="cc382-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="cc382-121">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="cc382-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="cc382-122">Definuje informace stamper čas Authenticode.</span><span class="sxs-lookup"><span data-stu-id="cc382-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc382-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc382-123">See Also</span></span>  
 [<span data-ttu-id="cc382-124">Referenční dokumentace nespravovaného rozhraní API</span><span class="sxs-lookup"><span data-stu-id="cc382-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
