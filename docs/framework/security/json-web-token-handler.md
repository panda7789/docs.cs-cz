---
title: Obslužná rutina webových tokenů JSON
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 27c01a3d0ce0f2891b00ad28526d4753b9be4ce0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="json-web-token-handler"></a>Obslužná rutina webových tokenů JSON
Pomocí rozšíření obslužné rutiny webových tokenů JSON pro technologii Windows Identity Foundation můžete ve svých aplikacích vytvářet a ověřovat webové tokeny JSON (JWT). Obslužnou rutinu tokenů JWT můžete nakonfigurovat tak, aby byla zapojena do kanálu WIF stejně jako ostatní obslužné rutiny tokenů zabezpečení, ale můžete ji také používat samostatně pro ověřování tokenů v jednoduchých aplikacích. Obslužná rutina tokenů JWT je obzvlášť užitečná, pokud používáte schéma tokenů nositele podle specifikace OAuth 2.0, například při ověřování ve službě Microsoft Azure Active Directory.  
  
 Obslužná rutina tokenů JWT je k dispozici jako balíček NuGet. V tématu [stažení balíčku tokenu obslužná rutina JSON webové](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) Další informace.  
  
## <a name="scenarios"></a>Scénáře  
 Obslužná rutina tokenů JWT podporuje následující nejdůležitější scénáře:  
  
-   **Ověřit Token JWT v aplikaci Server**: V tomto scénáři má společnost s názvem Litware server aplikace, která používá technologii WIF pro zpracování požadavků přihlašování na webu. Společnost Litware chce ve své aplikaci umožnit ověřování pomocí tokenů JWT. Aplikace je aktualizována s použitím obslužné rutiny tokenů JWT a poté je konfigurace aplikace aktualizována tak, aby byla obslužná rutina tokenů JWT zařazena do kanálu WIF. Když je po provedení aktualizací přijata nová žádost do kanálu technologie WIF, je token JWT ověřen pomocí nové obslužné rutiny a dojde k úspěšnému ověření.  
  
-   **Ověřit Token JWT ve webové službě REST**: V tomto scénáři má společnost s názvem Litware webové služby REST, která je zabezpečená službou Windows Azure Active Directory. Žádosti zaslané webové službě musejí být ověřeny službou Microsoft Azure AD, která po úspěšném ověření vystaví token JWT. Společnost Litware má klientskou aplikaci, která potřebuje přistupovat k webové službě. Klient zašle žádost webové službě a předloží svůj token JWT ze služby Microsoft Azure AD, který je poté ověřen webovou službu pomocí obslužné rutiny tokenů JWT. Jakmile obslužná rutina tokenů JWT token ověří, vrátí webová služba požadovaný prostředek klientovi.  
  
## <a name="features"></a>Funkce  
 Obslužná rutina tokenů JWT nabízí následující funkce:  
  
-   **Ověření tokenu JWT**: tokeny JWT můžete snadno ověřit buď jako součást aplikace WIF kanálu podle logiku ověření tokenu obslužná rutina, nebo názvem nezávisle na verzi WIF  
  
-   **Vytvořit JWT Token**: The JWT obslužná rutina tokenu lze použít k vytvoření tokenů JWT pro autorizaci v službami pro příjem dat
