---
title: HTTP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: c8c799a50e5d63bbf411c338eb9e93f85a942bb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048002"
---
# <a name="http"></a><span data-ttu-id="15778-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="15778-102">HTTP</span></span>
<span data-ttu-id="15778-103">Rozhraní .NET Framework poskytuje komplexní podporu pro protokol HTTP, který tvoří většinu <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> veškerého internetového provozu s třídami a.</span><span class="sxs-lookup"><span data-stu-id="15778-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="15778-104">Tyto třídy, <xref:System.Net.WebRequest> odvozené od a <xref:System.Net.WebResponse>, jsou <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> vráceny ve výchozím nastavení vždy, když statická metoda narazí na identifikátor URI začínající "http" nebo "https".</span><span class="sxs-lookup"><span data-stu-id="15778-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="15778-105">Ve většině případů **třídy WebRequest** a **WebResponse** poskytují vše, co je nezbytné k tomu, aby požadavek, ale pokud potřebujete přístup k funkcím specifickým pro protokol HTTP vystavených jako vlastnosti, můžete tyto třídy přetypovat na **HttpWebRequest** nebo **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="15778-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="15778-106">**HttpWebRequest** a **HttpWebResponse** zapouzdřují standardní transakci požadavku a odpovědi HTTP a poskytují přístup ke společným hlavičkám HTTP.</span><span class="sxs-lookup"><span data-stu-id="15778-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="15778-107">Tyto třídy také podporují většinu funkcí protokolu HTTP 1.1, včetně pipeliningu, odesílání a přijímání dat v blocích, ověřování, předběžnéověřování, šifrování, podporu proxy serveru, ověření certifikátu serveru a správy připojení.</span><span class="sxs-lookup"><span data-stu-id="15778-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="15778-108">Vlastní záhlaví a záhlaví, která nejsou poskytována prostřednictvím vlastností, mohou být uložena v vlastnosti **Záhlaví** a přístupná k nim.</span><span class="sxs-lookup"><span data-stu-id="15778-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="15778-109">**HttpWebRequest** je výchozí třída používaná **webovou aplikací A** před předáním identifikátoru URI metodě **WebRequest.Create** nemusí být registrována.</span><span class="sxs-lookup"><span data-stu-id="15778-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="15778-110">Aplikaci můžete automaticky sledovat přesměrování HTTP nastavením vlastnosti <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> na **hodnotu true** (výchozí).</span><span class="sxs-lookup"><span data-stu-id="15778-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="15778-111">Aplikace přesměruje požadavky a <xref:System.Net.HttpWebResponse.ResponseUri%2A> vlastnost **HttpWebResponse** bude obsahovat skutečný webový prostředek, který odpověděl na požadavek.</span><span class="sxs-lookup"><span data-stu-id="15778-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="15778-112">Pokud nastavíte **AllowAutoRedirect** na **false**, aplikace musí být schopen zpracovat přesměrování jako chyby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="15778-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="15778-113">Aplikace obdrží chyby protokolu <xref:System.Net.WebException> HTTP <xref:System.Net.WebException.Status%2A> zachycením a s nastavenou na <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="15778-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="15778-114">Vlastnost <xref:System.Net.WebException.Response%2A> obsahuje **webovou odezvu** odeslanou serverem a označuje skutečnou chybu PROTOKOLU HTTP, která byla zjištěna.</span><span class="sxs-lookup"><span data-stu-id="15778-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15778-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="15778-115">See also</span></span>

- [<span data-ttu-id="15778-116">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="15778-116">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="15778-117">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="15778-117">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="15778-118">Postupy: Přístup k vlastnostem specifickým pro HTTP</span><span class="sxs-lookup"><span data-stu-id="15778-118">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
