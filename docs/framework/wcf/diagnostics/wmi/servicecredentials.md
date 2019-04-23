---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772099"
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
  
 Typ přístupu: jen pro čtení  
  
 Certifikát ověření a opatření nastavení klienta pro tuto službu.  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Aktuálně vydaného tokenu ověřování nastavení pro tuto službu.  
  
### <a name="peer"></a>Peer  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Aktuální pověření ověřování a zřizování nastavení používané koncových bodů přenosu stejné.  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje aktuální nastavení zabezpečené konverzace.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Platnost certifikátu spojeného s touto službou.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Nastavení uživatelského jména a hesla pro tuto službu.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Nastavení ověřování Windows pro tuto službu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceCredentials>
