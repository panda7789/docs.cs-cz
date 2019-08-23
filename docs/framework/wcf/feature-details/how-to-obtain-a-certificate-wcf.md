---
title: 'Postupy: Získání certifikátu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: e720a6742506f6270fda65de12f510c2a6224873
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929195"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="5487d-102">Postupy: Získání certifikátu (WCF)</span><span class="sxs-lookup"><span data-stu-id="5487d-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="5487d-103">Chcete-li použít kteroukoli z funkcí Windows Communication Foundation (WCF), které používají certifikáty X. 509, stačí nejprve získat certifikáty.</span><span class="sxs-lookup"><span data-stu-id="5487d-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="5487d-104">Získání certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="5487d-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="5487d-105">Vyberte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="5487d-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="5487d-106">Zakupte certifikát od certifikační autority, jako je například VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="5487d-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="5487d-107">Nastavte si vlastní certifikační službu a požádejte certifikační autoritu o podepsání certifikátů.</span><span class="sxs-lookup"><span data-stu-id="5487d-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="5487d-108">, Windows 2000 Server, Windows 2000 Server Datacenter a Windows 2000 Datacenter Server All zahrnují certifikační služby, které podporují infrastrukturu veřejných klíčů (PKI).</span><span class="sxs-lookup"><span data-stu-id="5487d-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="5487d-109">V systému Windows Server 2008 použijte roli [služby Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) ke správě certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="5487d-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="5487d-110">Nastavte si vlastní certifikační službu a neměli byste mít podepsané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="5487d-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5487d-111">Bez ohledu na to, jakou metodu použijete, příjemce žádosti SOAP, která obsahuje certifikát X. 509, musí důvěřovat certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="5487d-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="5487d-112">To znamená, že certifikát X. 509 nebo Vystavitel v řetězu certifikátů se nachází v úložišti certifikátů Důvěryhodné osoby a certifikát X. 509 není v úložišti důvěryhodných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="5487d-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5487d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5487d-113">See also</span></span>

- [<span data-ttu-id="5487d-114">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="5487d-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5487d-115">Postupy: Vytváření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="5487d-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
