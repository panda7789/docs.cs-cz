---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 58b372f26fee7dc180d75731fd4855db569c87c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484517"
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
  
 Jestli úroveň zprávy a koncový bod nakonfigurovaná pomocí této vazby používá zabezpečení na úrovni přenosu.  
  
### <a name="transport"></a>Přenos  
 Datový typ: třída PeerTransportSecuritySettings  
  
 Přístup k typu: jen pro čtení  
  
 Nastavení zabezpečení přenosu.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.PeerSecuritySettings>
