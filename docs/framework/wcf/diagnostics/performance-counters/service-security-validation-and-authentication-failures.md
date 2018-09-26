---
title: 'Služba: Počet chyb ověřování zabezpečení'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
author: BrucePerlerMS
ms.openlocfilehash: 4c74cb1962bbc0f03ac33d8fcc7b10052bec8273
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197072"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="b5781-102">Služba: Počet chyb ověřování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5781-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="b5781-103">Název čítače: počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b5781-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="b5781-104">Popis</span><span class="sxs-lookup"><span data-stu-id="b5781-104">Description</span></span>  
 <span data-ttu-id="b5781-105">Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno".</span><span class="sxs-lookup"><span data-stu-id="b5781-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="b5781-106">Tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="b5781-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="b5781-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="b5781-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="b5781-108">Token klienta se nezdařilo ověřování (například,, chybných zadání hesla).</span><span class="sxs-lookup"><span data-stu-id="b5781-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
-   <span data-ttu-id="b5781-109">Ověření podpisu se nezdařilo (například, zpráva byla změněna).</span><span class="sxs-lookup"><span data-stu-id="b5781-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="b5781-110">Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.</span><span class="sxs-lookup"><span data-stu-id="b5781-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="b5781-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="b5781-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="b5781-112">Některé prvky (například,, chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="b5781-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="b5781-113">Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="b5781-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
