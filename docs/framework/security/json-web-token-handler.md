---
title: Obslužná rutina webových tokenů JSON
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 3dc76f3de714fd91d397cc240d02a1a8605fe18b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045334"
---
# <a name="json-web-token-handler"></a>Obslužná rutina webových tokenů JSON
Pomocí rozšíření obslužné rutiny webových tokenů JSON pro technologii Windows Identity Foundation můžete ve svých aplikacích vytvářet a ověřovat webové tokeny JSON (JWT). Obslužnou rutinu tokenů JWT můžete nakonfigurovat tak, aby byla zapojena do kanálu WIF stejně jako ostatní obslužné rutiny tokenů zabezpečení, ale můžete ji také používat samostatně pro ověřování tokenů v jednoduchých aplikacích. Obslužná rutina tokenů JWT je obzvlášť užitečná, pokud používáte schéma tokenů nositele podle specifikace OAuth 2.0, například při ověřování ve službě Microsoft Azure Active Directory.  
  
 Obslužná rutina tokenů JWT je k dispozici jako balíček NuGet. Další informace najdete v tématu [Stažení balíčku obslužné rutiny JSON web token](downloading-the-json-web-token-handler-package.md) .  
  
## <a name="scenarios"></a>Scénáře  
 Obslužná rutina tokenů JWT podporuje následující nejdůležitější scénáře:  
  
- **Ověření tokenu JWT v serverové aplikaci**: V tomto scénáři má společnost s názvem Litware serverovou aplikaci, která používá WIF ke zpracování žádostí o webové přihlášení. Společnost Litware chce ve své aplikaci umožnit ověřování pomocí tokenů JWT. Aplikace je aktualizována s použitím obslužné rutiny tokenů JWT a poté je konfigurace aplikace aktualizována tak, aby byla obslužná rutina tokenů JWT zařazena do kanálu WIF. Když je po provedení aktualizací přijata nová žádost do kanálu technologie WIF, je token JWT ověřen pomocí nové obslužné rutiny a dojde k úspěšnému ověření.  
  
- **Ověření tokenu JWT ve webové službě REST**: V tomto scénáři má společnost s názvem Litware webovou službu REST, která je zabezpečená Windows Azure Active Directory. Žádosti zaslané webové službě musejí být ověřeny službou Microsoft Azure AD, která po úspěšném ověření vystaví token JWT. Společnost Litware má klientskou aplikaci, která potřebuje přistupovat k webové službě. Klient zašle žádost webové službě a předloží svůj token JWT ze služby Microsoft Azure AD, který je poté ověřen webovou službu pomocí obslužné rutiny tokenů JWT. Jakmile obslužná rutina tokenů JWT token ověří, vrátí webová služba požadovaný prostředek klientovi.  
  
## <a name="features"></a>Funkce  
 Obslužná rutina tokenů JWT nabízí následující funkce:  
  
- **Ověřit token JWT**: Tokeny JWT lze snadno ověřit pomocí logiky ověřování obslužné rutiny tokenů, buď jako součást kanálu WIF aplikace, nebo je volána nezávisle na WIF.  
  
- **Vytvořit token JWT**: Obslužná rutina tokenu JWT se dá použít k vytvoření tokenů JWT pro autorizaci v navazujících službách.
