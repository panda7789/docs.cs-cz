---
title: '&lt;useManagedPresentation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3aeb64513401164c9c5acb24ede48c2e9aa2b4b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltusemanagedpresentationgt"></a>&lt;useManagedPresentation&gt;
Vazba element, který používá ke komunikaci s CardSpace služby tokenů zabezpečení, která podporuje CardSpace profilu WS-Trust. Tento element nemá žádný atribut a je k dispozici jako prázdný přepínač.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<useManagedPresentation >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element se používá pomocí zprostředkovatele identity pro vyjádření v svých zásad fakt, že podporuje CardSpace profilu WS-Trust. Zprostředkovatelů identity, které publikují takové výraz zásad byste měli mít problém tokeny na základě tohoto profilu CardSpace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
