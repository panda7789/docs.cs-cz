---
title: 'Postupy: Konzistentní odkazy na certifikáty X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: efc4fb399224de7f03c6bffb606178184de1d467
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489382"
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Postupy: Konzistentní odkazy na certifikáty X.509
Můžete určit certifikát několika způsoby: pomocí hodnota hash certifikátu, vystavitele a sériovým číslem nebo identifikátor klíče subjektu (identifikátor klíče subjektu). Identifikátor klíče subjektu poskytuje jedinečnou identifikaci veřejného klíče subjektu certifikátu a často se používá při práci s XML – digitální podpis. Identifikátor klíče subjektu hodnota je obvykle součástí certifikátu X.509 jako *rozšíření certifikátu X.509*. Windows Communication Foundation (WCF) má výchozí *odkazující na styl* používající vystavitele a sériovým číslem, pokud chybí rozšíření identifikátor klíče subjektu z certifikátu. Pokud certifikát obsahuje identifikátor klíče subjektu rozšíření, používá výchozí odkazující na styl identifikátor klíče subjektu tak, aby odkazoval na certifikát. Pokud střední způsob prostřednictvím vývoji aplikace přepnete z použití certifikátů, které nepoužívají rozšíření identifikátor klíče subjektu certifikáty, které používají rozšíření identifikátor klíče subjektu, styl odkazující použitý v zprávy generované WCF také změní.  
  
 Pokud konzistentní odkazující styl se vyžaduje bez ohledu na přítomnosti rozšíření identifikátor klíče subjektu, je možné nakonfigurovat požadované odkazující styl, jak je znázorněno v následujícím kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří prvku vazby vlastní zabezpečení, který používá jeden konzistentní odkazující styl, název vystavitele a sériovým číslem.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Následující obory názvů jsou nezbytné pro kompilaci kódu:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
