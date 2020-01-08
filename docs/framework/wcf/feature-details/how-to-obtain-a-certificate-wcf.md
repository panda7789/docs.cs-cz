---
title: 'Postupy: získání certifikátu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 485741f98c4a120669eafe85d3a3810374f61378
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347144"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="33889-102">Postupy: získání certifikátu (WCF)</span><span class="sxs-lookup"><span data-stu-id="33889-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="33889-103">Chcete-li použít kteroukoli z funkcí Windows Communication Foundation (WCF), které používají certifikáty X. 509, stačí nejprve získat certifikáty.</span><span class="sxs-lookup"><span data-stu-id="33889-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="33889-104">Získání certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="33889-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="33889-105">Vyberte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="33889-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="33889-106">Zakupte certifikát od certifikační autority, jako je například VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="33889-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="33889-107">Nastavte si vlastní certifikační službu a požádejte certifikační autoritu o podepsání certifikátů.</span><span class="sxs-lookup"><span data-stu-id="33889-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="33889-108">Systémy Windows Server 2003, Windows 2000 Server, Windows 2000 Datacenter serveru a Windows 2000 Datacenter Server zahrnují certifikační služby, které podporují infrastrukturu veřejných klíčů (PKI).</span><span class="sxs-lookup"><span data-stu-id="33889-108">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="33889-109">V systému Windows Server 2008 použijte roli [služby Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) ke správě certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="33889-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="33889-110">Nastavte si vlastní certifikační službu a neměli byste mít podepsané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="33889-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="33889-111">Bez ohledu na to, jakou metodu použijete, příjemce žádosti SOAP, která obsahuje certifikát X. 509, musí důvěřovat certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="33889-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="33889-112">To znamená, že certifikát X. 509 nebo Vystavitel v řetězu certifikátů se nachází v úložišti certifikátů Důvěryhodné osoby a certifikát X. 509 není v úložišti důvěryhodných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="33889-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33889-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33889-113">See also</span></span>

- [<span data-ttu-id="33889-114">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="33889-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="33889-115">Postupy: Vytváření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="33889-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
