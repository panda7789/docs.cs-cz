---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 18100ac36b5116c2373171ff795fc23b75bbd6f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572117"
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
