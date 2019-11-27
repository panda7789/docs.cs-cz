---
title: PNRP ve vývoji aplikací
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428203"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="c3739-102">PNRP ve vývoji aplikací</span><span class="sxs-lookup"><span data-stu-id="c3739-102">PNRP in Application Development</span></span>
<span data-ttu-id="c3739-103">V systému Windows Vista mohou síťové aplikace získat přístup k funkcím pro publikování a rozlišení názvů prostřednictvím zjednodušeného rozhraní API (PNRP Application Programming Interface).</span><span class="sxs-lookup"><span data-stu-id="c3739-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="c3739-104">Implementace protokolu PNRP (Peer Name Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="c3739-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="c3739-105">Díky zjednodušenému rozhraní API pro PNRP nejsou cloudy explicitně určeny k registraci názvů a adres; komponenta PNRP automaticky určuje vhodné cloudy pro připojení a adresy pro publikování v rámci cloudů.</span><span class="sxs-lookup"><span data-stu-id="c3739-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="c3739-106">Pro vysoce zjednodušené rozlišení názvů PNRP v systému Windows Vista jsou nyní názvy PNRP integrovány do funkce getaddrinfo () Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="c3739-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="c3739-107">Pokud chcete použít protokol PNRP k překladu názvu na adresu IPv6, můžou aplikace pomocí funkce getaddrinfo () přeložit plně kvalifikovaný název domény (FQDN) name.prnp.net, ve kterém je název název partnerského zařízení, který se řeší.</span><span class="sxs-lookup"><span data-stu-id="c3739-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="c3739-108">Doména pnrp.net je vyhrazená doména v systému Windows Vista pro překlad názvů PNRP.</span><span class="sxs-lookup"><span data-stu-id="c3739-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="c3739-109">Předávání zpráv mezi aplikacemi PeerToPeer se pořád zpracovává základními architekturami, jako jsou PeerChannel a WCF [Velká data a streamování](../wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="c3739-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3739-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3739-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
