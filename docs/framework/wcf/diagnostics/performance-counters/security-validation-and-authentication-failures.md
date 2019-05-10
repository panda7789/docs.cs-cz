---
title: Počet chyb ověření zabezpečení
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 0f061e1e12321dbe8034d7619830f71717ca9d1f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664980"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="7ab7b-102">Počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7ab7b-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="7ab7b-103">Název čítače: Počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7ab7b-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="7ab7b-104">Popis</span><span class="sxs-lookup"><span data-stu-id="7ab7b-104">Description</span></span>  
 <span data-ttu-id="7ab7b-105">Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno".</span><span class="sxs-lookup"><span data-stu-id="7ab7b-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="7ab7b-106">Tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="7ab7b-106">Such problems include:</span></span>  
  
- <span data-ttu-id="7ab7b-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="7ab7b-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="7ab7b-108">Token klienta se nezdařilo ověřování (například špatné heslo).</span><span class="sxs-lookup"><span data-stu-id="7ab7b-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="7ab7b-109">Ověření podpisu se nezdařilo (například, zpráva byla změněna).</span><span class="sxs-lookup"><span data-stu-id="7ab7b-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="7ab7b-110">Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.</span><span class="sxs-lookup"><span data-stu-id="7ab7b-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="7ab7b-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="7ab7b-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="7ab7b-112">Některé prvky (například chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="7ab7b-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="7ab7b-113">Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="7ab7b-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
