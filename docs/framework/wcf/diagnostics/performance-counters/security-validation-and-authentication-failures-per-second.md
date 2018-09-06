---
title: Ověřování zabezpečení a počet selhání ověření za sekundu
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4836a5076401de2f7c3112b298cdadc0e0307962
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731842"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="2deee-102">Ověřování zabezpečení a počet selhání ověření za sekundu</span><span class="sxs-lookup"><span data-stu-id="2deee-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="2deee-103">Název čítače: ověřování zabezpečení a ověřování chyb za sekundu.</span><span class="sxs-lookup"><span data-stu-id="2deee-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2deee-104">Popis</span><span class="sxs-lookup"><span data-stu-id="2deee-104">Description</span></span>  
 <span data-ttu-id="2deee-105">Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno".</span><span class="sxs-lookup"><span data-stu-id="2deee-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="2deee-106">Tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="2deee-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="2deee-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="2deee-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="2deee-108">Token klienta se nezdařilo ověřování (například špatné heslo).</span><span class="sxs-lookup"><span data-stu-id="2deee-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="2deee-109">Ověření podpisu se nezdařilo (například, zpráva byla změněna).</span><span class="sxs-lookup"><span data-stu-id="2deee-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="2deee-110">Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.</span><span class="sxs-lookup"><span data-stu-id="2deee-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="2deee-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="2deee-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="2deee-112">Některé prvky (například chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="2deee-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="2deee-113">Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="2deee-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="2deee-114">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="2deee-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="2deee-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="2deee-115">(N1-N0)/((D1-D0)/F)</span></span>
