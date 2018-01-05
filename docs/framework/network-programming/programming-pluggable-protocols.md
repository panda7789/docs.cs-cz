---
title: "Modulární protokoly programování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c97b64c9e042706fedabac435b8982aed65a8be4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="8693a-102">Modulární protokoly programování</span><span class="sxs-lookup"><span data-stu-id="8693a-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="8693a-103">Abstraktní <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují základ pro připojitelné protokoly.</span><span class="sxs-lookup"><span data-stu-id="8693a-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="8693a-104">Odvozené třídy specifické pro protokol z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>, můžete data žádosti z internetových prostředků a přečíst odpověď bez zadání protokol používá aplikace.</span><span class="sxs-lookup"><span data-stu-id="8693a-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="8693a-105">Před vytvořením konkrétního protokolu <xref:System.Net.WebRequest>, je nutné zaregistrovat jeho metody Create.</span><span class="sxs-lookup"><span data-stu-id="8693a-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="8693a-106">Použít statickou <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> metodu <xref:System.Net.WebRequest> k registraci <xref:System.Net.WebRequest> následné zpracování sadu požadavků na konkrétní schéma Internet, schéma a server nebo do schématu, serveru a cestu.</span><span class="sxs-lookup"><span data-stu-id="8693a-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="8693a-107">Ve většině případů bude moct posílat a přijímat data pomocí metody a vlastnosti <xref:System.Net.WebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="8693a-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="8693a-108">Ale pokud budete potřebovat přístup k vlastnosti specifické pro protokol, vám může přiřazení typu <xref:System.Net.WebRequest> ke konkrétní instanci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="8693a-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="8693a-109">Chcete využít výhod modulární protokoly, vaše <xref:System.Net.WebRequest> následníky musíte zadat výchozí požadavků a odpovědí transakci, která nevyžaduje vlastnosti specifické pro protokol nastavení.</span><span class="sxs-lookup"><span data-stu-id="8693a-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="8693a-110">Například <xref:System.Net.HttpWebRequest> třídy, které implementuje <xref:System.Net.WebRequest> třídy pro protokol HTTP, poskytuje `GET` požadavku ve výchozím nastavení a vrátí <xref:System.Net.HttpWebResponse> obsahující datový proud vrácený z webového serveru.</span><span class="sxs-lookup"><span data-stu-id="8693a-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8693a-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8693a-111">See Also</span></span>  
 [<span data-ttu-id="8693a-112">Odvození ze žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="8693a-112">Deriving from WebRequest</span></span>](../../../docs/framework/network-programming/deriving-from-webrequest.md)  
 [<span data-ttu-id="8693a-113">Odvození z odpovědi WebResponse</span><span class="sxs-lookup"><span data-stu-id="8693a-113">Deriving from WebResponse</span></span>](../../../docs/framework/network-programming/deriving-from-webresponse.md)  
 [<span data-ttu-id="8693a-114">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8693a-114">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="8693a-115">Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol</span><span class="sxs-lookup"><span data-stu-id="8693a-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
