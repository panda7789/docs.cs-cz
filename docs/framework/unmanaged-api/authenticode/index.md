---
title: Authenticode (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 1b8b2222950c75f7f9d2ec2704f722087645cd7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132455"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="c9a04-102">Authenticode (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="c9a04-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="c9a04-103">Podporuje modul pro vytváření a ověřování licencí Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c9a04-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9a04-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c9a04-104">In This Section</span></span>  
 [<span data-ttu-id="c9a04-105">Funkce _AxlGetIssuerPublicKeyHash</span><span class="sxs-lookup"><span data-stu-id="c9a04-105">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="c9a04-106">Načte hodnotu hash SHA-1 veřejného klíče přidruženého k privátnímu klíči, který se používá k podepsání zadaného certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c9a04-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="c9a04-107">Funkce _AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="c9a04-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="c9a04-108">Vypočítá token veřejného klíče se silným názvem z formátu PublicKeyBlob – CSP.</span><span class="sxs-lookup"><span data-stu-id="c9a04-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="c9a04-109">Funkce _AxlRSAKeyValueToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="c9a04-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="c9a04-110">Převede zbytek a exponent na token veřejného klíče silného názvu.</span><span class="sxs-lookup"><span data-stu-id="c9a04-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="c9a04-111">Funkce CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="c9a04-111">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="c9a04-112">Uvolní prostředky přidělené pro strukturu AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="c9a04-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="c9a04-113">Funkce CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="c9a04-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="c9a04-114">Uvolní prostředky přidělené pro strukturu AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="c9a04-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="c9a04-115">Funkce CertTimestampAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="c9a04-115">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="c9a04-116">Tato časová razítka mají licenci na technologii Authenticode vytvořenou pomocí CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="c9a04-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="c9a04-117">Funkce CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="c9a04-117">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="c9a04-118">Ověřuje platnost licence na technologii Authenticode pro technologii Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c9a04-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="c9a04-119">Struktura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="c9a04-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="c9a04-120">Definuje přihlašovací údaje Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c9a04-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="c9a04-121">Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="c9a04-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="c9a04-122">Definuje informace o časovém razítku technologie Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c9a04-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a04-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9a04-123">See also</span></span>

- [<span data-ttu-id="c9a04-124">Referenční informace o nespravovaném rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c9a04-124">Unmanaged API Reference</span></span>](../index.md)
