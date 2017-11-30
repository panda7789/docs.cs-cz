---
title: "Služba: Počet chyb ověřování zabezpečení za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 007bc3b38ef5b635a85e4c13f9bc9a6424fc36ad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="27c35-102">Služba: Počet chyb ověřování zabezpečení za sekundu</span><span class="sxs-lookup"><span data-stu-id="27c35-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="27c35-103">Název čítače: ověřování zabezpečení a ověřování chyb za sekundu.</span><span class="sxs-lookup"><span data-stu-id="27c35-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="27c35-104">Popis</span><span class="sxs-lookup"><span data-stu-id="27c35-104">Description</span></span>  
 <span data-ttu-id="27c35-105">Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn".</span><span class="sxs-lookup"><span data-stu-id="27c35-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="27c35-106">Mezi tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="27c35-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="27c35-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="27c35-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="27c35-108">Token klienta se nezdařilo ověření (třeba chybná hesla).</span><span class="sxs-lookup"><span data-stu-id="27c35-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="27c35-109">Ověření podpisu se nezdařila (například zprávy s ní bylo neoprávněně).</span><span class="sxs-lookup"><span data-stu-id="27c35-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="27c35-110">Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="27c35-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="27c35-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="27c35-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="27c35-112">Některé elementy (například chybějící časové razítko nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="27c35-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="27c35-113">Během TLSNEGO/SPNEGO metody handshake došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="27c35-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="27c35-114">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce</span><span class="sxs-lookup"><span data-stu-id="27c35-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="27c35-115">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="27c35-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
