---
title: <diagnostics> pro aktivaci
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: ac235b9a3c125cd3fe63ccd899e2ff92d4d3f31b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278445"
---
# <a name="diagnostics-for-activation"></a>\<Diagnostika > pro aktivaci
Nakonfiguruje funkce diagnostiky Windows Communication Foundation (WCF) naslouchacího procesu.  
  
 \<system.serviceModel.activation>  
\<Diagnostika >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`performanceCountersEnabled`|Logická hodnota, která určuje, zda jsou povoleny čítače výkonu pro diagnostické účely.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
