---
title: 'Služba: Počet chyb ověření zabezpečení'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998306"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="0e36d-102">Služba: Počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0e36d-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="0e36d-103">Název čítače: Počet chyb ověření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0e36d-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="0e36d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="0e36d-104">Description</span></span>  
 <span data-ttu-id="0e36d-105">Tento čítač se zvyšuje vždy, když zpráva byl odmítnut z důvodu problému zabezpečení se nevztahuje čítač "Zabezpečení volání Neautorizováno".</span><span class="sxs-lookup"><span data-stu-id="0e36d-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="0e36d-106">Tyto problémy patří:</span><span class="sxs-lookup"><span data-stu-id="0e36d-106">Such problems include:</span></span>  
  
- <span data-ttu-id="0e36d-107">Token klienta nelze číst ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="0e36d-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="0e36d-108">Token klienta se nezdařilo ověřování (například,, chybných zadání hesla).</span><span class="sxs-lookup"><span data-stu-id="0e36d-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
- <span data-ttu-id="0e36d-109">Ověření podpisu se nezdařilo (například, zpráva byla změněna).</span><span class="sxs-lookup"><span data-stu-id="0e36d-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
- <span data-ttu-id="0e36d-110">Zprávu je duplicitní v předchozím histogramem, což může dojít během opětovného přehrání útoku.</span><span class="sxs-lookup"><span data-stu-id="0e36d-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="0e36d-111">Došlo k selhání dešifrování.</span><span class="sxs-lookup"><span data-stu-id="0e36d-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="0e36d-112">Některé prvky (například,, chybějící časového razítka nebo šifrovaná data blokovat) chybí požadované ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="0e36d-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="0e36d-113">Při vyjednávání metodou handshake TLSNEGO/SPNEGO došlo k chybám.</span><span class="sxs-lookup"><span data-stu-id="0e36d-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
