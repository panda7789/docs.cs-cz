---
title: 'Koncový bod: Počet chyb ověřování zabezpečení'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8c46354fac11f5f0b46ef1b5629157f6da455fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471804"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="52b79-102">Koncový bod: Počet chyb ověřování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="52b79-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="52b79-103">Název čítače: počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="52b79-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="52b79-104">Popis</span><span class="sxs-lookup"><span data-stu-id="52b79-104">Description</span></span>  
 <span data-ttu-id="52b79-105">Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn".</span><span class="sxs-lookup"><span data-stu-id="52b79-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="52b79-106">Mezi tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="52b79-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="52b79-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="52b79-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="52b79-108">Token klienta se nezdařilo ověření (špatné heslo).</span><span class="sxs-lookup"><span data-stu-id="52b79-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="52b79-109">Ověření podpisu se nezdařilo. (zpráva s ní bylo neoprávněně).</span><span class="sxs-lookup"><span data-stu-id="52b79-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="52b79-110">Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="52b79-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="52b79-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="52b79-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="52b79-112">Zpráva chybí některé požadované prvky (chybějící časové razítko nebo blok šifrovaných dat).</span><span class="sxs-lookup"><span data-stu-id="52b79-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="52b79-113">Během TLSNEGO/SPNEGO metody handshake došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="52b79-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
