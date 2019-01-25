---
title: 'Postupy: Konzistentní odkazy na certifikáty X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: 2468faabfbca57e7d905a592b6743c43cb2ccd56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731969"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="dad61-102">Postupy: Konzistentní odkazy na certifikáty X.509</span><span class="sxs-lookup"><span data-stu-id="dad61-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="dad61-103">Můžete určit certifikát v několika ohledech: hodnota hash certifikátu, vystavitele a sériovým číslem nebo identifikátor klíče subjektu (identifikátor klíče subjektu).</span><span class="sxs-lookup"><span data-stu-id="dad61-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="dad61-104">Identifikátor klíče subjektu poskytuje jedinečnou identifikaci veřejného klíče subjektu certifikátu a často se používá při práci s XML – digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="dad61-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="dad61-105">Identifikátor klíče subjektu hodnota je obvykle součástí certifikátu X.509 jako *rozšíření certifikátu X.509*.</span><span class="sxs-lookup"><span data-stu-id="dad61-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="dad61-106">Windows Communication Foundation (WCF) má výchozí *odkazující na styl* , která používá vystavitele a sériovým číslem, pokud chybí rozšíření identifikátor klíče subjektu z certifikátu.</span><span class="sxs-lookup"><span data-stu-id="dad61-106">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="dad61-107">Pokud certifikát obsahuje vlastnost extension identifikátor klíče subjektu, používá výchozí odkazující na styl identifikátor klíče subjektu tak, aby odkazoval na certifikát.</span><span class="sxs-lookup"><span data-stu-id="dad61-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="dad61-108">Pokud uprostřed způsob prostřednictvím vývoji aplikace přepnou od používání certifikátů, které nepoužívají identifikátor klíče subjektu rozšíření na certifikátech, které používají rozšíření identifikátor klíče subjektu, odkazující styl použitý v zprávy WCF vygenerované také změní.</span><span class="sxs-lookup"><span data-stu-id="dad61-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="dad61-109">Pokud v jednotném stylu odkazující se vyžaduje bez ohledu na přítomnost identifikátor klíče subjektu rozšíření, je možné nakonfigurovat požadované odkazující styl, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="dad61-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dad61-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dad61-110">Example</span></span>  
 <span data-ttu-id="dad61-111">Následující příklad vytvoří vlastní bezpečnostní element vazby, který používá jediný konzistentní odkazující styl, název vystavitele a sériové číslo.</span><span class="sxs-lookup"><span data-stu-id="dad61-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dad61-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dad61-112">Compiling the Code</span></span>  
 <span data-ttu-id="dad61-113">Pro zkompilování kódu se vyžaduje následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="dad61-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="dad61-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dad61-114">See also</span></span>
- [<span data-ttu-id="dad61-115">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="dad61-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
