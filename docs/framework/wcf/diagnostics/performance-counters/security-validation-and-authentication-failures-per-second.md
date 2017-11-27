---
title: "Ověřování zabezpečení a počet selhání ověření za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 39ddfd18caae33e7ac2b905488bdfe4a8c9dc520
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="4b9af-102">Ověřování zabezpečení a počet selhání ověření za sekundu</span><span class="sxs-lookup"><span data-stu-id="4b9af-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="4b9af-103">Název čítače: ověřování zabezpečení a ověřování chyb za sekundu.</span><span class="sxs-lookup"><span data-stu-id="4b9af-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4b9af-104">Popis</span><span class="sxs-lookup"><span data-stu-id="4b9af-104">Description</span></span>  
 <span data-ttu-id="4b9af-105">Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn".</span><span class="sxs-lookup"><span data-stu-id="4b9af-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="4b9af-106">Mezi tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="4b9af-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="4b9af-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b9af-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="4b9af-108">Token klienta se nezdařilo ověření (třeba chybná hesla).</span><span class="sxs-lookup"><span data-stu-id="4b9af-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="4b9af-109">Ověření podpisu se nezdařila (například zprávy s ní bylo neoprávněně).</span><span class="sxs-lookup"><span data-stu-id="4b9af-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="4b9af-110">Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="4b9af-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="4b9af-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="4b9af-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="4b9af-112">Některé elementy (například chybějící časové razítko nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="4b9af-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="4b9af-113">Během TLSNEGO/SPNEGO metody handshake došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="4b9af-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="4b9af-114">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="4b9af-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="4b9af-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="4b9af-115">(N1-N0)/((D1-D0)/F)</span></span>
