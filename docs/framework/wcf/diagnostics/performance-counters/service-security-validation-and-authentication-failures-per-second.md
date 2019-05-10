---
title: 'Služba: Ověřování zabezpečení a počet selhání ověření za sekundu'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 2caebed85a28004ef038beee7d07c05a23da53c0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613683"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="c836a-102">Služba: Ověřování zabezpečení a počet selhání ověření za sekundu</span><span class="sxs-lookup"><span data-stu-id="c836a-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="c836a-103">Název čítače: Ověřování zabezpečení a počet selhání ověření za sekundu.</span><span class="sxs-lookup"><span data-stu-id="c836a-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c836a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c836a-104">Description</span></span>  
 <span data-ttu-id="c836a-105">Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno".</span><span class="sxs-lookup"><span data-stu-id="c836a-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="c836a-106">Tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="c836a-106">Such problems include:</span></span>  
  
- <span data-ttu-id="c836a-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="c836a-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="c836a-108">Token klienta se nezdařilo ověřování (například špatné heslo).</span><span class="sxs-lookup"><span data-stu-id="c836a-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="c836a-109">Ověření podpisu se nezdařilo (například, zpráva byla změněna).</span><span class="sxs-lookup"><span data-stu-id="c836a-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="c836a-110">Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.</span><span class="sxs-lookup"><span data-stu-id="c836a-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="c836a-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="c836a-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="c836a-112">Některé prvky (například chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="c836a-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="c836a-113">Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="c836a-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="c836a-114">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce</span><span class="sxs-lookup"><span data-stu-id="c836a-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="c836a-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c836a-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
