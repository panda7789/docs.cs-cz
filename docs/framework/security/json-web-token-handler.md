---
title: "Obslužná rutina webových tokenů JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a822e87f03c4fa7e1ce7449f09efd178b87cc99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="json-web-token-handler"></a><span data-ttu-id="183ef-102">Obslužná rutina webových tokenů JSON</span><span class="sxs-lookup"><span data-stu-id="183ef-102">JSON Web Token Handler</span></span>
<span data-ttu-id="183ef-103">Pomocí rozšíření obslužné rutiny webových tokenů JSON pro technologii Windows Identity Foundation můžete ve svých aplikacích vytvářet a ověřovat webové tokeny JSON (JWT).</span><span class="sxs-lookup"><span data-stu-id="183ef-103">The JSON Web Token Handler extension for Windows Identity Foundation enables you to create and validate JSON Web Tokens (JWT) in your applications.</span></span> <span data-ttu-id="183ef-104">Obslužnou rutinu tokenů JWT můžete nakonfigurovat tak, aby byla zapojena do kanálu WIF stejně jako ostatní obslužné rutiny tokenů zabezpečení, ale můžete ji také používat samostatně pro ověřování tokenů v jednoduchých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="183ef-104">The JWT Token Handler can be configured to run in the WIF pipeline like other built-in security token handlers, but it can also be used independently to perform token validation in lightweight applications.</span></span> <span data-ttu-id="183ef-105">Obslužná rutina tokenů JWT je obzvlášť užitečná, pokud používáte schéma tokenů nositele podle specifikace OAuth 2.0, například při ověřování ve službě Microsoft Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="183ef-105">The JWT Token Handler is particularly useful when using an OAuth 2.0 bearer token scheme, such as authenticating to Windows Azure Active Directory.</span></span>  
  
 <span data-ttu-id="183ef-106">Obslužná rutina tokenů JWT je k dispozici jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="183ef-106">The JWT Token Handler is available as a NuGet package.</span></span> <span data-ttu-id="183ef-107">V tématu [stažení balíčku tokenu obslužná rutina JSON webové](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="183ef-107">See [Downloading the JSON Web Token Handler Package](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) for more information.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="183ef-108">Scénáře</span><span class="sxs-lookup"><span data-stu-id="183ef-108">Scenarios</span></span>  
 <span data-ttu-id="183ef-109">Obslužná rutina tokenů JWT podporuje následující nejdůležitější scénáře:</span><span class="sxs-lookup"><span data-stu-id="183ef-109">The JWT Token Handler enables the following key scenarios:</span></span>  
  
-   <span data-ttu-id="183ef-110">**Ověřit Token JWT v aplikaci Server**: V tomto scénáři má společnost s názvem Litware server aplikace, která používá technologii WIF pro zpracování požadavků přihlašování na webu.</span><span class="sxs-lookup"><span data-stu-id="183ef-110">**Validate a JWT Token in a Server Application**: In this scenario, a company named Litware has a server application that uses WIF to handle web sign-on requests.</span></span> <span data-ttu-id="183ef-111">Společnost Litware chce ve své aplikaci umožnit ověřování pomocí tokenů JWT.</span><span class="sxs-lookup"><span data-stu-id="183ef-111">Litware wants to enable their application to use JWT tokens for authentication.</span></span> <span data-ttu-id="183ef-112">Aplikace je aktualizována s použitím obslužné rutiny tokenů JWT a poté je konfigurace aplikace aktualizována tak, aby byla obslužná rutina tokenů JWT zařazena do kanálu WIF.</span><span class="sxs-lookup"><span data-stu-id="183ef-112">The application is updated with the JWT Token Handler, and then the application configuration is updated to add the JWT Token Handler in the WIF pipeline.</span></span> <span data-ttu-id="183ef-113">Když je po provedení aktualizací přijata nová žádost do kanálu technologie WIF, je token JWT ověřen pomocí nové obslužné rutiny a dojde k úspěšnému ověření.</span><span class="sxs-lookup"><span data-stu-id="183ef-113">After the updates have been made and a new request enters the WIF pipeline, the JWT token is validated using the new handler and successful authentication occurs.</span></span>  
  
-   <span data-ttu-id="183ef-114">**Ověřit Token JWT ve webové službě REST**: V tomto scénáři má společnost s názvem Litware webové služby REST, která je zabezpečená službou Windows Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="183ef-114">**Validate a JWT Token in a REST Web Service**: In this scenario, a company named Litware has a REST web service that is secured by Windows Azure Active Directory.</span></span> <span data-ttu-id="183ef-115">Žádosti zaslané webové službě musejí být ověřeny službou Microsoft Azure AD, která po úspěšném ověření vystaví token JWT.</span><span class="sxs-lookup"><span data-stu-id="183ef-115">Requests to the web service must be authenticated by Windows Azure AD, which issues a JWT token upon successful authentication.</span></span> <span data-ttu-id="183ef-116">Společnost Litware má klientskou aplikaci, která potřebuje přistupovat k webové službě.</span><span class="sxs-lookup"><span data-stu-id="183ef-116">Litware has a client application that needs to access the web service.</span></span> <span data-ttu-id="183ef-117">Klient zašle žádost webové službě a předloží svůj token JWT ze služby Microsoft Azure AD, který je poté ověřen webovou službu pomocí obslužné rutiny tokenů JWT.</span><span class="sxs-lookup"><span data-stu-id="183ef-117">The client makes a request to the web service and presents its JWT token from Windows Azure AD, which is then validated by the web service using the JWT Token Handler.</span></span> <span data-ttu-id="183ef-118">Jakmile obslužná rutina tokenů JWT token ověří, vrátí webová služba požadovaný prostředek klientovi.</span><span class="sxs-lookup"><span data-stu-id="183ef-118">After the JWT Token Handler has validated the token, the desired resource is returned to the client by the web service.</span></span>  
  
## <a name="features"></a><span data-ttu-id="183ef-119">Funkce</span><span class="sxs-lookup"><span data-stu-id="183ef-119">Features</span></span>  
 <span data-ttu-id="183ef-120">Obslužná rutina tokenů JWT nabízí následující funkce:</span><span class="sxs-lookup"><span data-stu-id="183ef-120">The JWT Token Handler offers the following features:</span></span>  
  
-   <span data-ttu-id="183ef-121">**Ověření tokenu JWT**: tokeny JWT můžete snadno ověřit buď jako součást aplikace WIF kanálu podle logiku ověření tokenu obslužná rutina, nebo názvem nezávisle na verzi WIF</span><span class="sxs-lookup"><span data-stu-id="183ef-121">**Validate a JWT Token**: JWT tokens can be easily validated by the token handler’s validation logic, either as a part of the application’s WIF pipeline or called independently of WIF</span></span>  
  
-   <span data-ttu-id="183ef-122">**Vytvořit JWT Token**: The JWT obslužná rutina tokenu lze použít k vytvoření tokenů JWT pro autorizaci v službami pro příjem dat</span><span class="sxs-lookup"><span data-stu-id="183ef-122">**Create a JWT Token**: The JWT Token Handler can be used to create JWT tokens for authorization in downstream services</span></span>
