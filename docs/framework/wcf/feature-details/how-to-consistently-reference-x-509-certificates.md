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
# <a name="how-to-consistently-reference-x509-certificates"></a>Postupy: Konzistentní odkazy na certifikáty X.509
Certifikát můžete identifikovat několika způsoby: pomocí hodnoty hash certifikátu, vystavitele a sériového čísla nebo identifikátoru klíče subjektu (SKI). SKI poskytuje jedinečnou identifikaci veřejného klíče předmětu certifikátu a často se používá při práci s digitálním podpisem XML. Hodnota SKI je obvykle součástí certifikátu X. 509 jako *rozšíření certifikátu x. 509*. Windows Communication Foundation (WCF) má výchozí *odkaz na styl* , který používá Vystavitel a sériové číslo, pokud chybí rozšíření Ski v certifikátu. Pokud certifikát obsahuje rozšíření lyžařské, výchozí odkazování na certifikát používá lyžařské místo. Pokud středníky prostřednictvím vývoje aplikace přecházíte z použití certifikátů, které nepoužívají rozšíření SKI, k certifikátům, které používají rozšíření lyží, změní se také odkazující styl použitý ve zprávách generovaných pomocí služby WCF.  
  
 Pokud je vyžadován konzistentní styl bez ohledu na přítomnost rozšíření lyží, je možné nakonfigurovat požadovaný styl odkazování, jak je znázorněno v následujícím kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vlastní prvek vazby zabezpečení, který používá jediný jednotný styl odkazů, název vystavitele a sériové číslo.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro zkompilování kódu jsou vyžadovány následující obory názvů:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Viz také

- [Práce s certifikáty](working-with-certificates.md)
