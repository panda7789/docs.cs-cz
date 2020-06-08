---
title: HTTP
description: Přečtěte si o komplexní podpoře HTTP, kterou .NET Framework poskytuje, pomocí tříd HttpWebRequest a HttpWebResponse.
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
ms.openlocfilehash: ffb7a5d027ef7691d03caf0ac45d4a3dd9bdb652
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502415"
---
# <a name="http"></a><span data-ttu-id="c28ab-103">HTTP</span><span class="sxs-lookup"><span data-stu-id="c28ab-103">HTTP</span></span>
<span data-ttu-id="c28ab-104">.NET Framework poskytuje komplexní podporu protokolu HTTP, která tvoří většinu všech internetových přenosů s <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> třídami a.</span><span class="sxs-lookup"><span data-stu-id="c28ab-104">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="c28ab-105">Tyto třídy, které jsou odvozeny z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> , jsou ve výchozím nastavení vráceny pokaždé, když statická metoda <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> zjistí identifikátor URI začínající řetězcem "http" nebo "https".</span><span class="sxs-lookup"><span data-stu-id="c28ab-105">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="c28ab-106">Ve většině případů třídy **WebRequest** a **WebResponse** poskytují vše potřebné k provedení požadavku, ale pokud potřebujete přístup k funkcím specifickým pro protokol HTTP, které jsou vystaveny jako vlastnosti, můžete tyto třídy přetypovat na **HttpWebRequest** nebo **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="c28ab-106">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="c28ab-107">**HttpWebRequest** a **HttpWebResponse** zapouzdřují standardní transakce požadavků a odpovědí HTTP a poskytují přístup k běžným hlavičkám http.</span><span class="sxs-lookup"><span data-stu-id="c28ab-107">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="c28ab-108">Tyto třídy také podporují většinu funkcí protokolu HTTP 1,1, včetně přesměrování, odesílání a přijímání dat v blocích, ověřování, předběžném ověřování, šifrování, podpora proxy serveru, ověřování certifikátů serveru a správu připojení.</span><span class="sxs-lookup"><span data-stu-id="c28ab-108">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="c28ab-109">Vlastní hlavičky a hlavičky neposkytované prostřednictvím vlastností lze ukládat v a získávat prostřednictvím vlastnosti **Headers** .</span><span class="sxs-lookup"><span data-stu-id="c28ab-109">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="c28ab-110">**HttpWebRequest** je výchozí třída, kterou používá **WebRequest** a není nutné ji registrovat předtím, než můžete předat identifikátor URI metodě **WebRequest. Create** .</span><span class="sxs-lookup"><span data-stu-id="c28ab-110">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="c28ab-111">Aplikaci můžete nastavit tak, aby se automaticky sledovala přesměrování HTTP nastavením <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> vlastnosti na **hodnotu true** (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c28ab-111">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="c28ab-112">Aplikace bude přesměrovat požadavky a <xref:System.Net.HttpWebResponse.ResponseUri%2A> vlastnost **HttpWebResponse** bude obsahovat skutečný webový prostředek, který odpověděl na požadavek.</span><span class="sxs-lookup"><span data-stu-id="c28ab-112">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="c28ab-113">Pokud nastavíte **AllowAutoRedirect** na **false**, aplikace musí být schopná zpracovat přesměrování jako chyby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c28ab-113">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="c28ab-114">Aplikace dostávají chyby protokolu HTTP zachycením <xref:System.Net.WebException> s <xref:System.Net.WebException.Status%2A> nastavením na <xref:System.Net.WebExceptionStatus> .</span><span class="sxs-lookup"><span data-stu-id="c28ab-114">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="c28ab-115"><xref:System.Net.WebException.Response%2A>Vlastnost obsahuje **WebResponse** odeslanou serverem a indikuje, že došlo k skutečné chybě HTTP.</span><span class="sxs-lookup"><span data-stu-id="c28ab-115">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c28ab-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c28ab-116">See also</span></span>

- [<span data-ttu-id="c28ab-117">Přístup k internetu přes proxy server</span><span class="sxs-lookup"><span data-stu-id="c28ab-117">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="c28ab-118">Použití aplikačních protokolů</span><span class="sxs-lookup"><span data-stu-id="c28ab-118">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="c28ab-119">Postupy: Přístup k vlastnostem specifickým pro HTTP</span><span class="sxs-lookup"><span data-stu-id="c28ab-119">How to: Access HTTP-Specific Properties</span></span>](how-to-access-http-specific-properties.md)
