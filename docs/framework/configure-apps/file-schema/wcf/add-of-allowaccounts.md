---
title: "&lt;add&gt; – &lt;allowAccounts&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09ab06bb94249e79743335da1a360f6b668b1d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a>&lt;add&gt; – &lt;allowAccounts&gt;
Určuje, uživatelský účet pro procesy na tomto hostiteli [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.  
  
 \<system.serviceModel.activation >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|securityIdentifier|Řetězec, který určuje jedinečný identifikátor, který se používá k identifikaci uživatelský účet. Výchozí hodnoty jsou LocalSystem, správci, NS, LS a IIS_USRS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut k určení uživatelských účtů pro procesy, které hostují [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.|  
  
## <a name="example"></a>Příklad  
 Následující příklad konfigurace přidá pět výchozích identifikátory pro uživatelské účty do této kolekce.  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
