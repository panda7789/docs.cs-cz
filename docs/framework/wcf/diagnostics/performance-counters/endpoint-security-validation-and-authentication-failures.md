---
title: "Koncový bod: Počet chyb ověřování zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5bd38ae0e3506397378b7c59976c6c692045054d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="38ce3-102">Koncový bod: Počet chyb ověřování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="38ce3-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="38ce3-103">Název čítače: počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="38ce3-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="38ce3-104">Popis</span><span class="sxs-lookup"><span data-stu-id="38ce3-104">Description</span></span>  
 <span data-ttu-id="38ce3-105">Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn".</span><span class="sxs-lookup"><span data-stu-id="38ce3-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="38ce3-106">Mezi tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="38ce3-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="38ce3-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="38ce3-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="38ce3-108">Token klienta se nezdařilo ověření (špatné heslo).</span><span class="sxs-lookup"><span data-stu-id="38ce3-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="38ce3-109">Ověření podpisu se nezdařilo. (zpráva s ní bylo neoprávněně).</span><span class="sxs-lookup"><span data-stu-id="38ce3-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="38ce3-110">Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="38ce3-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="38ce3-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="38ce3-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="38ce3-112">Zpráva chybí některé požadované prvky (chybějící časové razítko nebo blok šifrovaných dat).</span><span class="sxs-lookup"><span data-stu-id="38ce3-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="38ce3-113">Během TLSNEGO/SPNEGO metody handshake došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="38ce3-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
