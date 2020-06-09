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
# <a name="how-to-obtain-a-certificate-wcf"></a>Postupy: získání certifikátu (WCF)
Chcete-li použít kteroukoli z funkcí Windows Communication Foundation (WCF), které používají certifikáty X. 509, stačí nejprve získat certifikáty.  
  
### <a name="to-obtain-an-x509-certificate"></a>Získání certifikátu X. 509  
  
1. Vyberte jednu z následujících možností:  
  
    - Zakupte certifikát od certifikační autority, jako je například VeriSign, Inc.  
  
    - Nastavte si vlastní certifikační službu a požádejte certifikační autoritu o podepsání certifikátů. Systémy Windows Server 2003, Windows 2000 Server, Windows 2000 Datacenter serveru a Windows 2000 Datacenter Server zahrnují certifikační služby, které podporují infrastrukturu veřejných klíčů (PKI). V systému Windows Server 2008 použijte roli [služby Active Directory Certificate Services](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) ke správě certifikační autority.  
  
    - Nastavte si vlastní certifikační službu a neměli byste mít podepsané certifikáty.  
  
    > [!NOTE]
    > Bez ohledu na to, jakou metodu použijete, příjemce žádosti SOAP, která obsahuje certifikát X. 509, musí důvěřovat certifikátu X. 509. To znamená, že certifikát X. 509 nebo Vystavitel v řetězu certifikátů se nachází v úložišti certifikátů Důvěryhodné osoby a certifikát X. 509 není v úložišti důvěryhodných certifikátů.  
  
## <a name="see-also"></a>Viz také

- [Práce s certifikáty](working-with-certificates.md)
- [Postupy: Vytváření dočasných certifikátů pro použití během vývoje](how-to-create-temporary-certificates-for-use-during-development.md)
