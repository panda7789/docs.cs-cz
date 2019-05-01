---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963004"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída PeerSecuritySettings nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída PeerSecuritySettings má následující vlastnosti:  
  
### <a name="mode"></a>Režim  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda zpráva úrovni a koncovým bodem nakonfigurovaným s vazbou používají zabezpečení na úrovni přenosu.  
  
### <a name="transport"></a>Přenos  
 Datový typ: PeerTransportSecuritySettings  
  
 Typ přístupu: jen pro čtení  
  
 Nastavení zabezpečení přenosu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.PeerSecuritySettings>
