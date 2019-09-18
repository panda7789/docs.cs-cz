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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047390"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="fb93f-102">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="fb93f-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="fb93f-103">Abstraktní <xref:System.Net.WebRequest> a<xref:System.Net.WebResponse> třídy poskytují základ pro připojené protokoly.</span><span class="sxs-lookup"><span data-stu-id="fb93f-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="fb93f-104">Odvozením tříd specifických pro protokol od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>může aplikace požadovat data z internetového prostředku a číst odpověď bez určení používaného protokolu.</span><span class="sxs-lookup"><span data-stu-id="fb93f-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="fb93f-105">Než budete moct vytvořit konkrétní <xref:System.Net.WebRequest>protokol, musíte zaregistrovat jeho metodu create.</span><span class="sxs-lookup"><span data-stu-id="fb93f-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="fb93f-106">Použijte statickou <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> metodu pro registraci <xref:System.Net.WebRequest> následníka pro zpracování sady požadavků na konkrétní internetové schéma, na schéma a Server nebo na schéma, server a cestu.</span><span class="sxs-lookup"><span data-stu-id="fb93f-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="fb93f-107">Ve většině případů budete moci odesílat a přijímat data pomocí metod a vlastností <xref:System.Net.WebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="fb93f-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="fb93f-108">Pokud však potřebujete získat přístup k vlastnostem specifickým pro protokol, můžete přetypovat <xref:System.Net.WebRequest> na konkrétní instanci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="fb93f-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="fb93f-109">Chcete-li využít výhod protokolů pro připojení, <xref:System.Net.WebRequest> musí vaši následovníci poskytnout výchozí transakci požadavku a odpovědi, která nevyžaduje nastavení vlastností specifických pro protokol.</span><span class="sxs-lookup"><span data-stu-id="fb93f-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="fb93f-110">Například <xref:System.Net.HttpWebRequest> třída, která <xref:System.Net.WebRequest> implementuje třídu `GET` pro http, poskytuje ve výchozím nastavení požadavek a vrátí objekt <xref:System.Net.HttpWebResponse> , který obsahuje datový proud vrácený z webového serveru.</span><span class="sxs-lookup"><span data-stu-id="fb93f-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb93f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb93f-111">See also</span></span>

- [<span data-ttu-id="fb93f-112">Odvození ze žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="fb93f-112">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
- [<span data-ttu-id="fb93f-113">Odvození z odpovědi WebResponse</span><span class="sxs-lookup"><span data-stu-id="fb93f-113">Deriving from WebResponse</span></span>](deriving-from-webresponse.md)
- [<span data-ttu-id="fb93f-114">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb93f-114">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="fb93f-115">Postupy: Přetypovat a WebRequest pro přístup k vlastnostem specifickým pro protokol</span><span class="sxs-lookup"><span data-stu-id="fb93f-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
