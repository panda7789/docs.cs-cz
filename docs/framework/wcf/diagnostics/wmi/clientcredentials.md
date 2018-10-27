---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 8b6200f84f352d49cf142d9c8b97d1c2b36149b2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180897"
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
  
 Certifikát X.509 klienta používá k ověření ve službě.  
  
### <a name="httpdigest"></a>HttpDigest  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Aktuální pověření Http Digest.  
  
### <a name="issuedtoken"></a>Třídy IssuedToken  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Adresa koncového bodu a vazba použitá ke kontaktování služby tokenů zabezpečení.  
  
### <a name="peer"></a>Peer  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Přihlašovací údaje, které bude rovnocenný uzel používá ke svému ověření do jiných uzlů v mřížce.  
  
### <a name="servicecertificate"></a>serviceCertificate  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Certifikát služby X.509.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Datový typ: boolean  
  
 Přístup k typu: jen pro čtení  
  
 Logická hodnota určující, zda přihlašovací údaje, které podporuje interaktivní vyjednávání.  
  
### <a name="username"></a>UserName  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Uživatelské jméno a heslo, které klient použije ke svému ověření ke službě.  
  
### <a name="windows"></a>Windows  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Pověření systému windows používá klient ke svému ověření ke službě.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ClientCredentials>
