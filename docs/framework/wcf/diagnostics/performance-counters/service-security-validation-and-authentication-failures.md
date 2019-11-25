---
title: 'Služba: Počet chyb ověření zabezpečení'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 399249926bcb1383fd33f60510c2c212c6f4261c
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204584"
---
# <a name="service-security-validation-and-authentication-failures"></a>Služba: Počet chyb ověření zabezpečení
Counter name: Security Validation and Authentication Failures  
  
## <a name="description"></a>Popis  
 This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter. Such problems include:  
  
- Client token cannot be read from the message.  
  
- Client token has failed authentication (for example, bad password).  
  
- Signature verification has failed (for example, the message has been tampered).  
  
- The message is a duplicate from a previous one, which can happen during a replay attack.  
  
- A decryption failure has occurred.  
  
- Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.  
  
- Errors have occurred during TLSNEGO/SPNEGO handshake.
