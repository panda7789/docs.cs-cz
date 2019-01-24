---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c1c4630e6191dbbe02688a4e4a9db9e18b8d36d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508412"
---
# <a name="ltallowaccountsgt"></a>&lt;allowAccounts&gt;
Obsahuje kolekci prvků konfigurace, které určují uživatelské účty pro procesy, které hostují služby Windows Communication Foundation (WCF) a jímž je udělen přístup ke službě sdílení.  
  
 \<system.serviceModel.activation>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|Přidá uživatelský účet pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě Sdílení|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) nebo [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)|Určuje nastavení konfigurace pro Net kanálu nebo služby Sdílení TCP.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
