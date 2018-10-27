---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 26bd0c95f930bf7859ae6409d797afbb596844fa
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180663"
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třídu ServiceCredentials nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třídu ServiceCredentials má následující vlastnosti:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Certifikát ověření a opatření nastavení klienta pro tuto službu.  
  
### <a name="issuedtokenauthentication"></a>issuedTokenAuthentication  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Aktuálně vydaného tokenu ověřování nastavení pro tuto službu.  
  
### <a name="peer"></a>Peer  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Aktuální pověření ověřování a zřizování nastavení používané koncových bodů přenosu stejné.  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje aktuální nastavení zabezpečené konverzace.  
  
### <a name="servicecertificate"></a>serviceCertificate  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Platnost certifikátu spojeného s touto službou.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení uživatelského jména a hesla pro tuto službu.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení ověřování Windows pro tuto službu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceCredentials>
