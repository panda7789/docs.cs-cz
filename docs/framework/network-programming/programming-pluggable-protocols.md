---
title: Programování připojitelných protokolů
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047390"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="57665-102">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="57665-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="57665-103">Abstraktní <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují základnu pro připojitelné protokoly.</span><span class="sxs-lookup"><span data-stu-id="57665-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="57665-104">Odvozením tříd specifických pro <xref:System.Net.WebRequest> <xref:System.Net.WebResponse>protokol z aplikace a , aplikace může požadovat data z internetového prostředku a číst odpověď bez určení použitého protokolu.</span><span class="sxs-lookup"><span data-stu-id="57665-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="57665-105">Před vytvořením protokolu specifické <xref:System.Net.WebRequest>, je nutné zaregistrovat jeho Create metoda.</span><span class="sxs-lookup"><span data-stu-id="57665-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="57665-106">Statickou <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> metodou registrace potomka <xref:System.Net.WebRequest> zpracování množiny požadavků na určité schéma Internetu, schématu a serveru nebo schématu, serveru a cesty.</span><span class="sxs-lookup"><span data-stu-id="57665-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="57665-107">Ve většině případů budete moci odesílat a přijímat data <xref:System.Net.WebRequest> pomocí metod a vlastností třídy.</span><span class="sxs-lookup"><span data-stu-id="57665-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="57665-108">Pokud však potřebujete získat přístup k vlastnostem specifickým pro protokol, můžete typcast a <xref:System.Net.WebRequest> pro konkrétní instanci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="57665-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="57665-109">Chcete-li využít připojitelné protokoly, potomci <xref:System.Net.WebRequest> musí poskytnout výchozí transakce požadavku a odpovědi, která nevyžaduje nastavení vlastností specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="57665-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="57665-110">Například <xref:System.Net.HttpWebRequest> třída, která implementuje třídu <xref:System.Net.WebRequest> pro `GET` PROTOKOL HTTP, <xref:System.Net.HttpWebResponse> poskytuje ve výchozím nastavení požadavek a vrací datový proud vrácený z webového serveru.</span><span class="sxs-lookup"><span data-stu-id="57665-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57665-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="57665-111">See also</span></span>

- [<span data-ttu-id="57665-112">Odvození ze žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="57665-112">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="57665-113">Odvození z odpovědi WebResponse</span><span class="sxs-lookup"><span data-stu-id="57665-113">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="57665-114">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="57665-114">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="57665-115">Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol</span><span class="sxs-lookup"><span data-stu-id="57665-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
