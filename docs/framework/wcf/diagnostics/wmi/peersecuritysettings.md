---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
ms.openlocfilehash: c74ee82d7aa3a23f0ee6a69185ad45857c31bb0b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087876"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda zpráva úrovni a koncovým bodem nakonfigurovaným s vazbou používají zabezpečení na úrovni přenosu.  
  
### <a name="transport"></a>Přenos  
 Datový typ: třída PeerTransportSecuritySettings  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení zabezpečení přenosu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.PeerSecuritySettings>
