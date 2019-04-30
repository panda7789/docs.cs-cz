---
title: Obslužná rutina webových tokenů JSON
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 27c01a3d0ce0f2891b00ad28526d4753b9be4ce0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790127"
---
# <a name="json-web-token-handler"></a>Obslužná rutina webových tokenů JSON
Pomocí rozšíření obslužné rutiny webových tokenů JSON pro technologii Windows Identity Foundation můžete ve svých aplikacích vytvářet a ověřovat webové tokeny JSON (JWT). Obslužnou rutinu tokenů JWT můžete nakonfigurovat tak, aby byla zapojena do kanálu WIF stejně jako ostatní obslužné rutiny tokenů zabezpečení, ale můžete ji také používat samostatně pro ověřování tokenů v jednoduchých aplikacích. Obslužná rutina tokenů JWT je obzvlášť užitečná, pokud používáte schéma tokenů nositele podle specifikace OAuth 2.0, například při ověřování ve službě Microsoft Azure Active Directory.  
  
 Obslužná rutina tokenů JWT je k dispozici jako balíček NuGet. Zobrazit [stahování JSON Web Token obslužná rutina balíček](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) Další informace.  
  
## <a name="scenarios"></a>Scénáře  
 Obslužná rutina tokenů JWT podporuje následující nejdůležitější scénáře:  
  
- **Ověřit Token JWT v serverové aplikaci**: V tomto scénáři má společnost s názvem Litware serverovou aplikaci, která pomocí technologie WIF zpracovávat webové žádosti o přihlášení. Společnost Litware chce ve své aplikaci umožnit ověřování pomocí tokenů JWT. Aplikace je aktualizována s použitím obslužné rutiny tokenů JWT a poté je konfigurace aplikace aktualizována tak, aby byla obslužná rutina tokenů JWT zařazena do kanálu WIF. Když je po provedení aktualizací přijata nová žádost do kanálu technologie WIF, je token JWT ověřen pomocí nové obslužné rutiny a dojde k úspěšnému ověření.  
  
- **Ověření tokenu JWT ve webové službě REST**: V tomto scénáři má společnost s názvem Litware webovou službu REST, která je zabezpečena pomocí služby Windows Azure Active Directory. Žádosti zaslané webové službě musejí být ověřeny službou Microsoft Azure AD, která po úspěšném ověření vystaví token JWT. Společnost Litware má klientskou aplikaci, která potřebuje přistupovat k webové službě. Klient zašle žádost webové službě a předloží svůj token JWT ze služby Microsoft Azure AD, který je poté ověřen webovou službu pomocí obslužné rutiny tokenů JWT. Jakmile obslužná rutina tokenů JWT token ověří, vrátí webová služba požadovaný prostředek klientovi.  
  
## <a name="features"></a>Funkce  
 Obslužná rutina tokenů JWT nabízí následující funkce:  
  
- **Ověření tokenu JWT**: Tokenů JWT můžete snadno ověřit logiku ověřování tokenu obslužné rutiny, buď jako součást kanálu WIF aplikace nebo ji volat nezávisle na technologii WIF  
  
- **Vytvořit token JWT Token**: Obslužná rutina tokenů JWT je možné vytvářet tokeny JWT pro autorizaci v navazujících službách
