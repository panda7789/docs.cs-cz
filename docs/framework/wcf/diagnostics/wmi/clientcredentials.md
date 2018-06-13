---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: aa852ff82c44a3b5009dbc70e1067face44cbbe9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486373"
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ClientCredentials nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ClientCredentials má následující vlastnosti:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Certifikát X.509 klienta používá k ověření služby.  
  
### <a name="httpdigest"></a>HttpDigest  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Aktuální pověření Http Digest.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Adresa koncového bodu a vazba použitá ke kontaktování služby tokenů zabezpečení.  
  
### <a name="peer"></a>sdílené  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Pověření, které používá uzlu druhé strany ke svému ověření do dalších uzlů v mřížce.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Certifikát X.509 služby.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota, která určuje, zda pověření podporuje interaktivní vyjednávání.  
  
### <a name="username"></a>UserName  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Uživatelské jméno a heslo, které klient používá k ověření samotné služby.  
  
### <a name="windows"></a>Windows  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Přihlašovací údaje windows používá klienta ke svému ověření ke službě.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ClientCredentials>
