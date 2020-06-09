---
title: 'Postupy: získání certifikátu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: d020f3e97023d07abb572d30dd53896bfec1da46
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597017"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="884d2-102">Postupy: získání certifikátu (WCF)</span><span class="sxs-lookup"><span data-stu-id="884d2-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="884d2-103">Chcete-li použít kteroukoli z funkcí Windows Communication Foundation (WCF), které používají certifikáty X. 509, stačí nejprve získat certifikáty.</span><span class="sxs-lookup"><span data-stu-id="884d2-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="884d2-104">Získání certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="884d2-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="884d2-105">Vyberte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="884d2-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="884d2-106">Zakupte certifikát od certifikační autority, jako je například VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="884d2-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="884d2-107">Nastavte si vlastní certifikační službu a požádejte certifikační autoritu o podepsání certifikátů.</span><span class="sxs-lookup"><span data-stu-id="884d2-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="884d2-108">Systémy Windows Server 2003, Windows 2000 Server, Windows 2000 Datacenter serveru a Windows 2000 Datacenter Server zahrnují certifikační služby, které podporují infrastrukturu veřejných klíčů (PKI).</span><span class="sxs-lookup"><span data-stu-id="884d2-108">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="884d2-109">V systému Windows Server 2008 použijte roli [služby Active Directory Certificate Services](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) ke správě certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="884d2-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="884d2-110">Nastavte si vlastní certifikační službu a neměli byste mít podepsané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="884d2-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="884d2-111">Bez ohledu na to, jakou metodu použijete, příjemce žádosti SOAP, která obsahuje certifikát X. 509, musí důvěřovat certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="884d2-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="884d2-112">To znamená, že certifikát X. 509 nebo Vystavitel v řetězu certifikátů se nachází v úložišti certifikátů Důvěryhodné osoby a certifikát X. 509 není v úložišti důvěryhodných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="884d2-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="884d2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="884d2-113">See also</span></span>

- [<span data-ttu-id="884d2-114">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="884d2-114">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="884d2-115">Postupy: Vytváření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="884d2-115">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
