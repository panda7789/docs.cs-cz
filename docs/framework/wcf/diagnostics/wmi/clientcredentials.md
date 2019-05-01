---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963969"
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
  
 Typ přístupu: jen pro čtení  
  
 Certifikát X.509 klienta používá k ověření ve službě.  
  
### <a name="httpdigest"></a>HttpDigest  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Aktuální pověření Http Digest.  
  
### <a name="issuedtoken"></a>Třídy IssuedToken  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Adresa koncového bodu a vazba použitá ke kontaktování služby tokenů zabezpečení.  
  
### <a name="peer"></a>Peer  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Přihlašovací údaje, které bude rovnocenný uzel používá ke svému ověření do jiných uzlů v mřížce.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Certifikát služby X.509.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Logická hodnota určující, zda přihlašovací údaje, které podporuje interaktivní vyjednávání.  
  
### <a name="username"></a>UserName  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Uživatelské jméno a heslo, které klient použije ke svému ověření ke službě.  
  
### <a name="windows"></a>Windows  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Pověření systému windows používá klient ke svému ověření ke službě.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ClientCredentials>
