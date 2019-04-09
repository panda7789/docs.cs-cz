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
ms.openlocfilehash: d14eb426c8e142f56d9f024dcbf37a1d2d78664d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072338"
---
# <a name="programming-pluggable-protocols"></a><span data-ttu-id="15319-102">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="15319-102">Programming Pluggable Protocols</span></span>
<span data-ttu-id="15319-103">Abstraktní <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují základ pro připojitelné protokoly.</span><span class="sxs-lookup"><span data-stu-id="15319-103">The abstract <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide the base for pluggable protocols.</span></span> <span data-ttu-id="15319-104">Odvozené třídy pro konkrétní z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>, můžete data žádosti z internetového zdroji a čtení odpovědi bez zadání protokolu používá aplikace.</span><span class="sxs-lookup"><span data-stu-id="15319-104">By deriving protocol-specific classes from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, an application can request data from an Internet resource and read the response without specifying the protocol being used.</span></span>  
  
 <span data-ttu-id="15319-105">Než budete moct vytvořit protokol konkrétní <xref:System.Net.WebRequest>, je nutné zaregistrovat jeho metody Create.</span><span class="sxs-lookup"><span data-stu-id="15319-105">Before you can create a protocol-specific <xref:System.Net.WebRequest>, you must register its Create method.</span></span> <span data-ttu-id="15319-106">Použití statické <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> metoda <xref:System.Net.WebRequest> k registraci <xref:System.Net.WebRequest> následné zpracování sady požadavků na konkrétní schéma Internet, schéma a server nebo do schématu, server a cestu.</span><span class="sxs-lookup"><span data-stu-id="15319-106">Use the static <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> method of <xref:System.Net.WebRequest> to register a <xref:System.Net.WebRequest> descendant to handle a set of requests to a particular Internet scheme, to a scheme and server, or to a scheme, server, and path.</span></span>  
  
 <span data-ttu-id="15319-107">Ve většině případů budete moct posílat a přijímat data pomocí metod a vlastností <xref:System.Net.WebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="15319-107">In most cases you will be able to send and receive data using the methods and properties of the <xref:System.Net.WebRequest> class.</span></span> <span data-ttu-id="15319-108">Ale pokud potřebujete přístup k vlastnostem specifickým pro protokol, můžete přetypovat <xref:System.Net.WebRequest> k určité instanci odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="15319-108">However, if you need to access protocol-specific properties, you can typecast a <xref:System.Net.WebRequest> to a specific derived-class instance.</span></span>  
  
 <span data-ttu-id="15319-109">Abyste mohli využívat připojitelných protokolů, vaše <xref:System.Net.WebRequest> následníků musí poskytovat výchozí transakce požadavků a odpovědí, který nevyžaduje konkrétní nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="15319-109">To take advantage of pluggable protocols, your <xref:System.Net.WebRequest> descendants must provide a default request-and-response transaction that does not require protocol-specific properties to be set.</span></span> <span data-ttu-id="15319-110">Například <xref:System.Net.HttpWebRequest> třídy, která implementuje <xref:System.Net.WebRequest> třídy pro protokol HTTP, poskytuje `GET` žádost ve výchozím nastavení a vrátí <xref:System.Net.HttpWebResponse> datový proud vrácený z webového serveru, který obsahuje.</span><span class="sxs-lookup"><span data-stu-id="15319-110">For example, the <xref:System.Net.HttpWebRequest> class, which implements the <xref:System.Net.WebRequest> class for HTTP, provides a `GET` request by default and returns an <xref:System.Net.HttpWebResponse> that contains the stream returned from the Web server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15319-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15319-111">See also</span></span>

- [<span data-ttu-id="15319-112">Odvození ze žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="15319-112">Deriving from WebRequest</span></span>](../../../docs/framework/network-programming/deriving-from-webrequest.md)
- [<span data-ttu-id="15319-113">Odvození z odpovědi WebResponse</span><span class="sxs-lookup"><span data-stu-id="15319-113">Deriving from WebResponse</span></span>](../../../docs/framework/network-programming/deriving-from-webresponse.md)
- [<span data-ttu-id="15319-114">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15319-114">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="15319-115">Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol</span><span class="sxs-lookup"><span data-stu-id="15319-115">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
