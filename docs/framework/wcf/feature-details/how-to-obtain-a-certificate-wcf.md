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
# <a name="how-to-obtain-a-certificate-wcf"></a>Postupy: získání certifikátu (WCF)
K používání některé Windows Communication Foundation (WCF), funkce používají certifikáty X.509, je právě nejprve získat certifikáty.  
  
### <a name="to-obtain-an-x509-certificate"></a>K získání certifikátu X.509  
  
1.  Vyberte jednu z následujících možností:  
  
    -   Koupit certifikát od certifikační autority, jako je například VeriSign, Inc.  
  
    -   Nastavení certifikátu služby a mít podepsání certifikátů certifikační autority. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter a systém Windows 2000 Datacenter zahrnují certifikační služby, které podporují infrastruktury veřejných klíčů (PKI). V systému Windows Server 2008, použijte [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) rolí ke správě certifikační autority.  
  
    -   Nastavení certifikátu služby a provést není mít certifikáty podepsané.  
  
    > [!NOTE]
    >  V obou případech můžete využít, příjemce žádosti SOAP, který obsahuje certifikát X.509 musí důvěřovat certifikátu X.509. To znamená, že certifikát X.509 nebo vystavitele v řetězu certifikátů je v úložišti certifikátů důvěryhodných osob a zda není v úložišti nedůvěryhodné certifikáty certifikátu X.509.  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Postupy: Vytváření dočasných certifikátů pro použití během vývoje](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
