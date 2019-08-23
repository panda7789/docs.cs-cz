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
# <a name="how-to-obtain-a-certificate-wcf"></a>Postupy: Získání certifikátu (WCF)
Chcete-li použít kteroukoli z funkcí Windows Communication Foundation (WCF), které používají certifikáty X. 509, stačí nejprve získat certifikáty.  
  
### <a name="to-obtain-an-x509-certificate"></a>Získání certifikátu X. 509  
  
1. Vyberte jednu z následujících možností:  
  
    - Zakupte certifikát od certifikační autority, jako je například VeriSign, Inc.  
  
    - Nastavte si vlastní certifikační službu a požádejte certifikační autoritu o podepsání certifikátů. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter a Windows 2000 Datacenter Server All zahrnují certifikační služby, které podporují infrastrukturu veřejných klíčů (PKI). V systému Windows Server 2008 použijte roli [služby Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) ke správě certifikační autority.  
  
    - Nastavte si vlastní certifikační službu a neměli byste mít podepsané certifikáty.  
  
    > [!NOTE]
    > Bez ohledu na to, jakou metodu použijete, příjemce žádosti SOAP, která obsahuje certifikát X. 509, musí důvěřovat certifikátu X. 509. To znamená, že certifikát X. 509 nebo Vystavitel v řetězu certifikátů se nachází v úložišti certifikátů Důvěryhodné osoby a certifikát X. 509 není v úložišti důvěryhodných certifikátů.  
  
## <a name="see-also"></a>Viz také:

- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Postupy: Vytváření dočasných certifikátů pro použití během vývoje](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
