---
title: "Koncový bod: Ověřování zabezpečení a počet selhání ověření za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c6b50aa00fe59d0ad23d5ca0b77c7b89f97a0d1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="262b7-102">Koncový bod: Ověřování zabezpečení a počet selhání ověření za sekundu</span><span class="sxs-lookup"><span data-stu-id="262b7-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="262b7-103">Název čítače: ověřování zabezpečení a ověřování chyb za sekundu</span><span class="sxs-lookup"><span data-stu-id="262b7-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="262b7-104">Popis</span><span class="sxs-lookup"><span data-stu-id="262b7-104">Description</span></span>  
 <span data-ttu-id="262b7-105">Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn".</span><span class="sxs-lookup"><span data-stu-id="262b7-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="262b7-106">Mezi tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="262b7-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="262b7-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="262b7-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="262b7-108">Token klienta se nezdařilo ověření (třeba chybná hesla).</span><span class="sxs-lookup"><span data-stu-id="262b7-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="262b7-109">Ověření podpisu se nezdařila (například zprávy s ní bylo neoprávněně).</span><span class="sxs-lookup"><span data-stu-id="262b7-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="262b7-110">Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="262b7-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="262b7-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="262b7-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="262b7-112">Některé elementy (například chybějící časové razítko nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="262b7-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="262b7-113">Během TLSNEGO/SPNEGO metody handshake došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="262b7-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="262b7-114">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="262b7-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="262b7-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="262b7-115">(N1-N0)/((D1-D0)/F)</span></span>
