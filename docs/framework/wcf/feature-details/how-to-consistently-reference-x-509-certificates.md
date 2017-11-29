---
title: "Postupy: Konzistentní odkazy na certifikáty X.509"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d42af919b9792fc5a5303737187be7ffef6405d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="5acaf-102">Postupy: Konzistentní odkazy na certifikáty X.509</span><span class="sxs-lookup"><span data-stu-id="5acaf-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="5acaf-103">Můžete určit certifikát několika způsoby: pomocí hodnota hash certifikátu, vystavitele a sériovým číslem nebo identifikátor klíče subjektu (identifikátor klíče subjektu).</span><span class="sxs-lookup"><span data-stu-id="5acaf-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="5acaf-104">Identifikátor klíče subjektu poskytuje jedinečnou identifikaci veřejného klíče subjektu certifikátu a často se používá při práci s XML – digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="5acaf-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="5acaf-105">Identifikátor klíče subjektu hodnota je obvykle součástí certifikátu X.509 jako *rozšíření certifikátu X.509*.</span><span class="sxs-lookup"><span data-stu-id="5acaf-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="5acaf-106">má výchozí *odkazující na styl* používající vystavitele a sériovým číslem, pokud chybí rozšíření identifikátor klíče subjektu z certifikátu.</span><span class="sxs-lookup"><span data-stu-id="5acaf-106"> has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="5acaf-107">Pokud certifikát obsahuje identifikátor klíče subjektu rozšíření, používá výchozí odkazující na styl identifikátor klíče subjektu tak, aby odkazoval na certifikát.</span><span class="sxs-lookup"><span data-stu-id="5acaf-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="5acaf-108">Pokud střední způsob prostřednictvím vývoji aplikace přepnete z použití certifikátů, které nepoužívají rozšíření identifikátor klíče subjektu certifikáty, které používají rozšíření identifikátor klíče subjektu, styl odkazující použity v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-generované zprávy také změny.</span><span class="sxs-lookup"><span data-stu-id="5acaf-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-generated messages also changes.</span></span>  
  
 <span data-ttu-id="5acaf-109">Pokud konzistentní odkazující styl se vyžaduje bez ohledu na přítomnosti rozšíření identifikátor klíče subjektu, je možné nakonfigurovat požadované odkazující styl, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5acaf-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5acaf-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5acaf-110">Example</span></span>  
 <span data-ttu-id="5acaf-111">Následující příklad vytvoří prvku vazby vlastní zabezpečení, který používá jeden konzistentní odkazující styl, název vystavitele a sériovým číslem.</span><span class="sxs-lookup"><span data-stu-id="5acaf-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5acaf-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5acaf-112">Compiling the Code</span></span>  
 <span data-ttu-id="5acaf-113">Následující obory názvů jsou nezbytné pro kompilaci kódu:</span><span class="sxs-lookup"><span data-stu-id="5acaf-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="5acaf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5acaf-114">See Also</span></span>  
 [<span data-ttu-id="5acaf-115">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="5acaf-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
