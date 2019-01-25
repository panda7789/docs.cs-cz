---
title: 'Postupy: Získání certifikátu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: cefea47d77fef9a59234584b02b03dca4cd99ebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709439"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Postupy: Získání certifikátu (WCF)
K používání některé Windows Communication Foundation (WCF) funkce, která používají certifikáty X.509, stačí nejprve získat certifikáty.  
  
### <a name="to-obtain-an-x509-certificate"></a>Získání certifikátu X.509  
  
1.  Vyberte jednu z následujících možností:  
  
    -   Zakupte certifikát z certifikační autority, jako je například VeriSign, Inc.  
  
    -   Nastavení certifikátu služby a mít certifikační autoritu podepsání certifikátů. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter a Windows 2000 Datacenter Server zahrnují certifikační služby, které podporují infrastruktury veřejných klíčů (PKI). Ve Windows serveru 2008, použijte [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) rolí ke správě certifikační autority.  
  
    -   Nastavení certifikátu služby a proveďte není mít certifikáty podepsané.  
  
    > [!NOTE]
    >  Podle toho, která přístup, příjemce, který obsahuje certifikát X.509 žádosti SOAP musí důvěřovat certifikátu X.509. To znamená, že certifikát X.509 nebo vystavitele v řetězu certifikátů je v úložišti certifikátů důvěryhodných osob a že certifikát X.509 není v úložišti nedůvěryhodné certifikáty.  
  
## <a name="see-also"></a>Viz také:
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Postupy: Vytváření dočasných certifikátů pro použití během vývoje.](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
