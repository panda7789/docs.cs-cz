---
title: "Ověřování v Internetu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fbf25ae866b338d2f1ac0ea11570e0d535e9137c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="internet-authentication"></a><span data-ttu-id="9be84-102">Ověřování v Internetu</span><span class="sxs-lookup"><span data-stu-id="9be84-102">Internet Authentication</span></span>
<span data-ttu-id="9be84-103"><xref:System.Net> Třídy podporují různé mechanismy ověřování klienta, včetně standardní Internet metod ověřování basic, algoritmem digest, vyjednávání protokolu NTLM a ověřování protokolu Kerberos, a také vlastních metod, které můžete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="9be84-103">The <xref:System.Net> classes support a variety of client authentication mechanisms, including the standard Internet authentication methods basic, digest, negotiate, NTLM, and Kerberos authentication, as well as custom methods that you can create.</span></span>  
  
 <span data-ttu-id="9be84-104">Pověření pro ověření jsou uložené v <xref:System.Net.NetworkCredential> a <xref:System.Net.CredentialCache> třídy, které implementují rozhraní <xref:System.Net.ICredentials> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9be84-104">Authentication credentials are stored in the <xref:System.Net.NetworkCredential> and <xref:System.Net.CredentialCache> classes, which implement the <xref:System.Net.ICredentials> interface.</span></span> <span data-ttu-id="9be84-105">Když jedna z těchto tříd je dotazován na přihlašovací údaje, vrátí instanci **NetworkCredential** třídy.</span><span class="sxs-lookup"><span data-stu-id="9be84-105">When one of these classes is queried for credentials, it returns an instance of the **NetworkCredential** class.</span></span> <span data-ttu-id="9be84-106">Spravuje proces ověřování <xref:System.Net.AuthenticationManager> třídy a proces skutečné ověřování se provádí třídou ověřování modul, který implementuje <xref:System.Net.IAuthenticationModule> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9be84-106">The authentication process is managed by the <xref:System.Net.AuthenticationManager> class, and the actual authentication process is performed by an authentication module class that implements the <xref:System.Net.IAuthenticationModule> interface.</span></span> <span data-ttu-id="9be84-107">Je nutné zaregistrovat vlastní ověřování modul s **třídě** před jeho použitím; vyjednávání moduly pro základní, algoritmus digest, protokol NTLM, a metody ověřování protokolu Kerberos je registrován ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="9be84-107">You must register a custom authentication module with the **AuthenticationManager** before it can be used; modules for the basic, digest, negotiate, NTLM, and Kerberos authentication methods are registered by default.</span></span>  
  
 <span data-ttu-id="9be84-108">**NetworkCredential** ukládá sadu přihlašovacích údajů spojených s jediný zdroj Internet identifikovaného identifikátorem URI a vrátí je v reakci na jakékoli volání <xref:System.Net.NetworkCredential.GetCredential%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9be84-108">**NetworkCredential** stores a set of credentials associated with a single Internet resource identified by a URI and returns them in response to any call to the <xref:System.Net.NetworkCredential.GetCredential%2A> method.</span></span> <span data-ttu-id="9be84-109">**NetworkCredential** třída se obvykle používá aplikace, které přístup k omezenému počtu prostředků z Internetu nebo aplikace, které používají stejnou sadu přihlašovacích údajů ve všech případech.</span><span class="sxs-lookup"><span data-stu-id="9be84-109">The **NetworkCredential** class is typically used by applications that access a limited number of Internet resources or by applications that use the same set of credentials in all cases.</span></span>  
  
 <span data-ttu-id="9be84-110">**CredentialCache** třída ukládá kolekce přihlašovací údaje pro různé webové prostředky.</span><span class="sxs-lookup"><span data-stu-id="9be84-110">The **CredentialCache** class stores a collection of credentials for various Web resources.</span></span> <span data-ttu-id="9be84-111">Když <xref:System.Net.CredentialCache.GetCredential%2A> metoda je volána, **CredentialCache** vrátí správnou sadu přihlašovacích údajů, počítáno od identifikátor URI webové prostředky a požadovaná ověřovací schéma.</span><span class="sxs-lookup"><span data-stu-id="9be84-111">When the <xref:System.Net.CredentialCache.GetCredential%2A> method is called, **CredentialCache** returns the proper set of credentials, as determined by the URI of the Web resource and the requested authentication scheme.</span></span> <span data-ttu-id="9be84-112">Aplikace, které používají různých prostředků z Internetu pomocí různých ověřovacích schémata využívat **CredentialCache** třídy, protože ukládá všechny přihlašovací údaje a poskytuje je požadovaná.</span><span class="sxs-lookup"><span data-stu-id="9be84-112">Applications that use a variety of Internet resources with different authentication schemes benefit from using the **CredentialCache** class, since it stores all the credentials and provides them as requested.</span></span>  
  
 <span data-ttu-id="9be84-113">Když internetových prostředků požaduje ověřování, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> metoda odešle <xref:System.Net.WebRequest> k **třídě** společně se žádostí pro přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="9be84-113">When an Internet resource requests authentication, the <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> method sends the <xref:System.Net.WebRequest> to the **AuthenticationManager** along with the request for credentials.</span></span> <span data-ttu-id="9be84-114">Žádost je pak ověřit následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9be84-114">The request is then authenticated according to the following process:</span></span>  
  
1.  <span data-ttu-id="9be84-115">**Třídě** volání <xref:System.Net.IAuthenticationModule.Authenticate%2A> metoda na všech registrovaných ověřovací moduly v pořadí, které by bylo zaregistrováno.</span><span class="sxs-lookup"><span data-stu-id="9be84-115">The **AuthenticationManager** calls the <xref:System.Net.IAuthenticationModule.Authenticate%2A> method on each of the registered authentication modules in the order they were registered.</span></span> <span data-ttu-id="9be84-116">**Třídě** používá první modul, který nevrací **null** provést proces ověřování.</span><span class="sxs-lookup"><span data-stu-id="9be84-116">The **AuthenticationManager** uses the first module that does not return **null** to carry out the authentication process.</span></span> <span data-ttu-id="9be84-117">Informace o procesu lišit v závislosti na typu zahrnutých ověřování modulu.</span><span class="sxs-lookup"><span data-stu-id="9be84-117">The details of the process vary depending on the type of authentication module involved.</span></span>  
  
2.  <span data-ttu-id="9be84-118">Po dokončení procesu ověřování modul ověřování vrátí <xref:System.Net.Authorization> k **WebRequest** obsahující informace potřebné pro přístup k Internetu prostředku.</span><span class="sxs-lookup"><span data-stu-id="9be84-118">When the authentication process is complete, the authentication module returns an <xref:System.Net.Authorization> to the **WebRequest** that contains the information needed to access the Internet resource.</span></span>  
  
 <span data-ttu-id="9be84-119">Některé schémat ověřování, můžete ověřovat uživatele bez provedení první požadavek pro prostředek.</span><span class="sxs-lookup"><span data-stu-id="9be84-119">Some authentication schemes can authenticate a user without first making a request for a resource.</span></span> <span data-ttu-id="9be84-120">Aplikace můžete ušetřit čas tím preauthenticating uživatele s hledaným prostředkem, a odstraňuje tak alespoň jeden odezvy na server.</span><span class="sxs-lookup"><span data-stu-id="9be84-120">An application can save time by preauthenticating the user with the resource, thus eliminating at least one round trip to the server.</span></span> <span data-ttu-id="9be84-121">Nebo, aby byla později rychlejšího uživateli může provádět ověřování během spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="9be84-121">Or, it can perform authentication during program startup in order to be more responsive to the user later.</span></span> <span data-ttu-id="9be84-122">Schémat ověřování, které můžete použít sadu předběžného ověření <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="9be84-122">Authentication schemes that can use preauthentication set the <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> property to **true**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be84-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9be84-123">See Also</span></span>  
 [<span data-ttu-id="9be84-124">Základní ověřování a ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="9be84-124">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [<span data-ttu-id="9be84-125">Ověřování NTLM a Kerberos</span><span class="sxs-lookup"><span data-stu-id="9be84-125">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [<span data-ttu-id="9be84-126">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="9be84-126">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
