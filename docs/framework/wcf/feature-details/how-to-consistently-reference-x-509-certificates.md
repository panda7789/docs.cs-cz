---
title: 'Postupy: Konzistentní odkazy na certifikáty X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: c13dd5ebb18df62ce64fc74da53f3f5a2e8cadb7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599084"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="3dcc4-102">Postupy: Konzistentní odkazy na certifikáty X.509</span><span class="sxs-lookup"><span data-stu-id="3dcc4-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="3dcc4-103">Certifikát můžete identifikovat několika způsoby: pomocí hodnoty hash certifikátu, vystavitele a sériového čísla nebo identifikátoru klíče subjektu (SKI).</span><span class="sxs-lookup"><span data-stu-id="3dcc4-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="3dcc4-104">SKI poskytuje jedinečnou identifikaci veřejného klíče předmětu certifikátu a často se používá při práci s digitálním podpisem XML.</span><span class="sxs-lookup"><span data-stu-id="3dcc4-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="3dcc4-105">Hodnota SKI je obvykle součástí certifikátu X. 509 jako *rozšíření certifikátu x. 509*.</span><span class="sxs-lookup"><span data-stu-id="3dcc4-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="3dcc4-106">Windows Communication Foundation (WCF) má výchozí *odkaz na styl* , který používá Vystavitel a sériové číslo, pokud chybí rozšíření Ski v certifikátu.</span><span class="sxs-lookup"><span data-stu-id="3dcc4-106">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="3dcc4-107">Pokud certifikát obsahuje rozšíření lyžařské, výchozí odkazování na certifikát používá lyžařské místo.</span><span class="sxs-lookup"><span data-stu-id="3dcc4-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="3dcc4-108">Pokud středníky prostřednictvím vývoje aplikace přecházíte z použití certifikátů, které nepoužívají rozšíření SKI, k certifikátům, které používají rozšíření lyží, změní se také odkazující styl použitý ve zprávách generovaných pomocí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="3dcc4-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="3dcc4-109">Pokud je vyžadován konzistentní styl bez ohledu na přítomnost rozšíření lyží, je možné nakonfigurovat požadovaný styl odkazování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3dcc4-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dcc4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="3dcc4-110">Example</span></span>  
 <span data-ttu-id="3dcc4-111">Následující příklad vytvoří vlastní prvek vazby zabezpečení, který používá jediný jednotný styl odkazů, název vystavitele a sériové číslo.</span><span class="sxs-lookup"><span data-stu-id="3dcc4-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3dcc4-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3dcc4-112">Compiling the Code</span></span>  
 <span data-ttu-id="3dcc4-113">Pro zkompilování kódu jsou vyžadovány následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="3dcc4-113">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="3dcc4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dcc4-114">See also</span></span>

- [<span data-ttu-id="3dcc4-115">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="3dcc4-115">Working with Certificates</span></span>](working-with-certificates.md)
