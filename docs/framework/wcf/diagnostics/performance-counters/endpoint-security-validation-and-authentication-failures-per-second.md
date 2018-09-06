---
title: 'Koncový bod: Ověřování zabezpečení a počet selhání ověření za sekundu'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b857a608c6b485c384956e55247b6e02c49a8564
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44040944"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="a98bd-102">Koncový bod: Ověřování zabezpečení a počet selhání ověření za sekundu</span><span class="sxs-lookup"><span data-stu-id="a98bd-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="a98bd-103">Název čítače: ověřování zabezpečení a ověřování chyb za sekundu</span><span class="sxs-lookup"><span data-stu-id="a98bd-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="a98bd-104">Popis</span><span class="sxs-lookup"><span data-stu-id="a98bd-104">Description</span></span>  
 <span data-ttu-id="a98bd-105">Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno".</span><span class="sxs-lookup"><span data-stu-id="a98bd-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="a98bd-106">Tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="a98bd-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="a98bd-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="a98bd-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="a98bd-108">Token klienta se nezdařilo ověřování (například špatné heslo).</span><span class="sxs-lookup"><span data-stu-id="a98bd-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="a98bd-109">Ověření podpisu se nezdařilo (například, zpráva byla změněna).</span><span class="sxs-lookup"><span data-stu-id="a98bd-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="a98bd-110">Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.</span><span class="sxs-lookup"><span data-stu-id="a98bd-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="a98bd-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="a98bd-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="a98bd-112">Některé prvky (například chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="a98bd-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="a98bd-113">Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="a98bd-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="a98bd-114">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="a98bd-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="a98bd-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="a98bd-115">(N1-N0)/((D1-D0)/F)</span></span>
