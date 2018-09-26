---
title: Počet chyb ověřování zabezpečení
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
author: BrucePerlerMS
ms.openlocfilehash: d13e94800d71c6f567c6aab61974e42b1a3f1706
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198186"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="706b0-102">Počet chyb ověřování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="706b0-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="706b0-103">Název čítače: počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="706b0-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="706b0-104">Popis</span><span class="sxs-lookup"><span data-stu-id="706b0-104">Description</span></span>  
 <span data-ttu-id="706b0-105">Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno".</span><span class="sxs-lookup"><span data-stu-id="706b0-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="706b0-106">Tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="706b0-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="706b0-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="706b0-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="706b0-108">Token klienta se nezdařilo ověřování (například špatné heslo).</span><span class="sxs-lookup"><span data-stu-id="706b0-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="706b0-109">Ověření podpisu se nezdařilo (například, zpráva byla změněna).</span><span class="sxs-lookup"><span data-stu-id="706b0-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="706b0-110">Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.</span><span class="sxs-lookup"><span data-stu-id="706b0-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="706b0-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="706b0-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="706b0-112">Některé prvky (například chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="706b0-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="706b0-113">Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="706b0-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
