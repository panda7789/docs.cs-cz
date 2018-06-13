---
title: 'Postupy: získání certifikátu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 368401d91aa2a83110631d583660d6ccebf8d4fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491504"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="58dad-102">Postupy: získání certifikátu (WCF)</span><span class="sxs-lookup"><span data-stu-id="58dad-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="58dad-103">K používání některé Windows Communication Foundation (WCF), funkce používají certifikáty X.509, je právě nejprve získat certifikáty.</span><span class="sxs-lookup"><span data-stu-id="58dad-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="58dad-104">K získání certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="58dad-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="58dad-105">Vyberte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="58dad-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="58dad-106">Koupit certifikát od certifikační autority, jako je například VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="58dad-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="58dad-107">Nastavení certifikátu služby a mít podepsání certifikátů certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="58dad-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="58dad-108">, Windows 2000 Server, Windows 2000 Server Datacenter a systém Windows 2000 Datacenter zahrnují certifikační služby, které podporují infrastruktury veřejných klíčů (PKI).</span><span class="sxs-lookup"><span data-stu-id="58dad-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="58dad-109">V systému Windows Server 2008, použijte [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) rolí ke správě certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="58dad-109">In Windows Server 2008, use the [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="58dad-110">Nastavení certifikátu služby a provést není mít certifikáty podepsané.</span><span class="sxs-lookup"><span data-stu-id="58dad-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="58dad-111">V obou případech můžete využít, příjemce žádosti SOAP, který obsahuje certifikát X.509 musí důvěřovat certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="58dad-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="58dad-112">To znamená, že certifikát X.509 nebo vystavitele v řetězu certifikátů je v úložišti certifikátů důvěryhodných osob a zda není v úložišti nedůvěryhodné certifikáty certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="58dad-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58dad-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="58dad-113">See Also</span></span>  
 [<span data-ttu-id="58dad-114">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="58dad-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="58dad-115">Postupy: Vytváření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="58dad-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
