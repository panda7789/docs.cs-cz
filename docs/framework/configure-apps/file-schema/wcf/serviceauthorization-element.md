---
title: Element &lt;serviceAuthorization&gt;
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: 6c69d10eb2f6cdf4546dd5895d196723417f5494
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146001"
---
# <a name="ltserviceauthorizationgt-element"></a>Element &lt;serviceAuthorization&gt;
Určuje nastavení, které povolují přístup k operacím služby  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<serviceAuthorization >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
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
|ImpersonateCallerForAllOperations|Logická hodnota určující, pokud všechny operace služby zosobňují volajícího. Výchozí hodnota je `false`.<br /><br /> Když konkrétní operaci služby zosobňuje volajícího, kontext vlákna přepnutí na kontext volající před provedením zadaná služba.|  
|PrincipalPermissionMode|Nastaví objekt zabezpečení použitý k provádění operací na serveru. Následující hodnoty:<br /><br /> -Žádný<br />-UseWindowsGroups<br />-UseAspNetRoles<br />– Vlastní<br /><br /> Výchozí hodnota je UseWindowsGroups. Hodnota je typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Další informace o použití tohoto atributu naleznete v tématu [jak: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Řetězec určující název poskytovatele rolí, který poskytuje informace o rolích pro aplikace Windows Communication Foundation (WCF). Výchozí hodnota je prázdný řetězec.|  
|Třída ServiceAuthorizationManagerType|Řetězec obsahující typ správce autorizace služby. Další informace naleznete v tématu <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|authorizationPolicies|Obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` – klíčové slovo. Každá zásada autorizace obsahuje jediný vyžaduje `policyType` atribut, který není řetězec. Atribut určuje zásadu autorizace, který umožňuje transformovat jednu sadu vstupních deklarací identity do jiné sady deklarací identity. Může být povolen nebo odepřen řízení přístupu na základě. Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Obsahuje kolekci nastavení pro chování služby.|  
  
## <a name="remarks"></a>Poznámky  
 Tato část obsahuje prvky, které by to ovlivnilo autorizace, vlastní roli zprostředkovatele a zosobnění.  
  
 `principalPermissionMode` Atribut určuje skupiny uživatelů při použití chráněné metody ověřování. Výchozí hodnota je `UseWindowsGroups` a určuje, že skupin Windows, jako je například "Administrators" nebo "Uživatelé," se vyhledávají identitu při pokusu o přístup k prostředku. Můžete také určit `UseAspNetRoles` používat vlastní role poskytovatele, který je nakonfigurovaný pod \<system.web > element, jak je znázorněno v následujícím kódu.  
  
```xml  
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
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
  <!-- Other configuration code not shown. -->
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
  
 Podrobný příklad použití tento prvek konfigurace, najdete v části [autorizace přístupu k operacím služby](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Autorizace přístupu k operacím služby](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Postupy: Vytvoření vlastního Správce autorizací pro službu](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Zásady autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md)
