---
title: 'Postupy: Získání certifikátu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 21e9e0609ed63c4398f2df7ba718f8af17464b0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683637"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="3df94-102">Postupy: Získání certifikátu (WCF)</span><span class="sxs-lookup"><span data-stu-id="3df94-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="3df94-103">K používání některé Windows Communication Foundation (WCF) funkce, která používají certifikáty X.509, stačí nejprve získat certifikáty.</span><span class="sxs-lookup"><span data-stu-id="3df94-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="3df94-104">Získání certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="3df94-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="3df94-105">Vyberte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="3df94-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="3df94-106">Zakupte certifikát z certifikační autority, jako je například VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="3df94-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="3df94-107">Nastavení certifikátu služby a mít certifikační autoritu podepsání certifikátů.</span><span class="sxs-lookup"><span data-stu-id="3df94-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="3df94-108">, Windows 2000 Server, Windows 2000 Server Datacenter a Windows 2000 Datacenter Server zahrnují certifikační služby, které podporují infrastruktury veřejných klíčů (PKI).</span><span class="sxs-lookup"><span data-stu-id="3df94-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="3df94-109">Ve Windows serveru 2008, použijte [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) rolí ke správě certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="3df94-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="3df94-110">Nastavení certifikátu služby a proveďte není mít certifikáty podepsané.</span><span class="sxs-lookup"><span data-stu-id="3df94-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3df94-111">Podle toho, která přístup, příjemce, který obsahuje certifikát X.509 žádosti SOAP musí důvěřovat certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="3df94-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="3df94-112">To znamená, že certifikát X.509 nebo vystavitele v řetězu certifikátů je v úložišti certifikátů důvěryhodných osob a že certifikát X.509 není v úložišti nedůvěryhodné certifikáty.</span><span class="sxs-lookup"><span data-stu-id="3df94-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df94-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3df94-113">See also</span></span>

- [<span data-ttu-id="3df94-114">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="3df94-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3df94-115">Postupy: Vytváření dočasných certifikátů pro použití během vývoje.</span><span class="sxs-lookup"><span data-stu-id="3df94-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
