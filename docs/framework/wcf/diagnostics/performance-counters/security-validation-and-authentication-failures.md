---
title: "Počet chyb ověřování zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c52b54d2be2e824de478e0ee9ec2452c57e181b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="e4f18-102">Počet chyb ověřování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e4f18-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="e4f18-103">Název čítače: počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e4f18-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="e4f18-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e4f18-104">Description</span></span>  
 <span data-ttu-id="e4f18-105">Tento čítač se navyšuje vždy, když zprávu byl odmítnut z důvodu problému zabezpečení nejsou pokryty čítač "Zabezpečení volání není oprávněn".</span><span class="sxs-lookup"><span data-stu-id="e4f18-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="e4f18-106">Mezi tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="e4f18-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="e4f18-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="e4f18-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="e4f18-108">Token klienta se nezdařilo ověření (třeba chybná hesla).</span><span class="sxs-lookup"><span data-stu-id="e4f18-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="e4f18-109">Ověření podpisu se nezdařila (například zprávy s ní bylo neoprávněně).</span><span class="sxs-lookup"><span data-stu-id="e4f18-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="e4f18-110">Zpráva je duplicitní z předchozí jeden, který může dojít při útoku formou opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="e4f18-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="e4f18-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="e4f18-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="e4f18-112">Některé elementy (například chybějící časové razítko nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="e4f18-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="e4f18-113">Během TLSNEGO/SPNEGO metody handshake došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="e4f18-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
