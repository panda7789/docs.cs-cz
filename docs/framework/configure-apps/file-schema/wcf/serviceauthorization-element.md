---
title: Element &lt;serviceAuthorization&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc04552b9b2ecd85a520ed16ae9a6ee0dfc98a46
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthorizationgt-element"></a>Element &lt;serviceAuthorization&gt;
Určuje nastavení, které zajistí autorizaci přístupu k operacím služby  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<serviceAuthorization >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceAuthorization  
     impersonateCallerForAllOperations="Boolean"  
      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"  
      roleProviderName="String"  
      serviceAuthorizationManagerType="String" />  
      <authorizationPolicies>  
         <add policyType="String" />  
      </authorizationPolicies>  
</serviceAuthorization>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|impersonateCallerForAllOperations|Logická hodnota, která určuje, pokud všechny operace ve službě zosobnit volající. Výchozí hodnota je `false`.<br /><br /> Pokud konkrétní operaci služby zosobňuje volající, kontext přístup z více vláken je přepnout do kontextu volající před provedením zadaná služba.|  
|principalPermissionMode|Nastaví objekt se používá k provádění operací na serveru. Následující hodnoty:<br /><br /> -None<br />-UseWindowsGroups<br />-UseAspNetRoles<br />-Vlastní<br /><br /> Výchozí hodnota je UseWindowsGroups. Hodnota je typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Další informace o použití tohoto atributu naleznete v části [postupy: omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Řetězec, který určuje název zprostředkovatele rolí, která poskytuje informace o rolích pro aplikaci Windows Communication Foundation (WCF). Výchozí hodnota je prázdný řetězec.|  
|Třída ServiceAuthorizationManagerType|Řetězec obsahující typ Správce autorizací služby. Další informace naleznete v tématu <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|authorizationPolicies|Obsahuje kolekci typů zásad autorizace, které lze přidat pomocí `add` – klíčové slovo. Každá zásada autorizace obsahuje jediný požadované `policyType` atribut, který obsahuje řetězec. Atribut určuje zásad autorizace, která umožňuje transformace jednu sadu vstupních deklarací identity na jinou sadu deklarací identity. Řízení přístupu může být povolen nebo odepřen, na základě. Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Obsahuje kolekci nastavení pro chování služby.|  
  
## <a name="remarks"></a>Poznámky  
 Tato část obsahuje prvky, které mají vliv na ověřování, vlastní roli zprostředkovatele a zosobnění.  
  
 `principalPermissionMode` Atribut určuje skupiny uživatelů pro použití při použití chráněná metoda autorizace. Výchozí hodnota je `UseWindowsGroups` a určuje skupiny systému Windows, jako je například "Administrators" nebo "Uživatelé," se vyhledávají identity pokusu o přístup k prostředku. Můžete také zadat `UseAspNetRoles` používat vlastní roli zprostředkovatele, který je nakonfigurovaný pod \<system.web > elementu, jak je znázorněno v následujícím kódu.  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 Následující kód ukazuje `roleProviderName` použít s `principalPermissionMode` atribut.  
  
```xml  
<behaviors>  
   <behavior name="ServiceBehaviour">  
     <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                           roleProviderName ="SqlProvider" />  
   </behavior>   
<!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
 Podrobný příklad použití tohoto elementu konfigurace najdete v tématu [autorizace přístupu k operacím služby](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Autorizace přístupu k operacím služby](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Postupy: vytvoření vlastního Správce autorizací pro službu](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Postupy: omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Zásady autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md)
