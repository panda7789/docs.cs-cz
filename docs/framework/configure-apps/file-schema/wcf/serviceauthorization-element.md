---
title: <serviceAuthorization> – element
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834012"
---
# <a name="serviceauthorization-element"></a>\<serviceAuthorization> – element

Určuje nastavení, které autorizují přístup k operacím služby.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

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

Následující části popisují atributy, podřízené prvky a nadřazené prvky:

### <a name="attributes"></a>Atributy

|Atribut|Popis|  
|---------------|-----------------|  
|impersonateCallerForAllOperations|Logická hodnota, která určuje, zda všechny operace ve službě zosobňuje volajícího. Výchozí formát je `false`.<br /><br /> Když konkrétní operace služby zosobňuje volajícího, kontext vlákna je přepnut na volající kontext před spuštěním zadané služby.|  
|principalPermissionMode|Nastaví objekt zabezpečení, který se používá k provádění operací na serveru. Mezi hodnoty patří následující:<br /><br /> -   Žádné<br />- UseWindowsGroups<br />- UseAspNetRoles<br />– Vlastní<br /><br /> Výchozí hodnota je UseWindowsGroups. Hodnota je typu <xref:System.ServiceModel.Description.PrincipalPermissionMode> . Další informace o použití tohoto atributu naleznete v tématu [How to: restrict Access with a PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Řetězec, který určuje název poskytovatele rolí, který poskytuje informace o rolích pro aplikaci Windows Communication Foundation (WCF). Výchozí hodnota je prázdný řetězec.|  
|ServiceAuthorizationManagerType|Řetězec obsahující typ Správce autorizací služby. Další informace naleznete v tématu <xref:System.ServiceModel.ServiceAuthorizationManager>.|  

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Description|  
|-------------|-----------------|  
|authorizationPolicies|Obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` klíčového slova. Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec. Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací. Řízení přístupu lze na základě této aplikace udělit nebo odepřít. Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Obsahuje kolekci nastavení pro chování služby.|  

## <a name="remarks"></a>Poznámky

Tato část obsahuje prvky ovlivňující autorizaci, vlastní poskytovatele rolí a zosobnění.  
  
`principalPermissionMode`Atribut určuje skupiny uživatelů, které se mají použít při autorizaci použití chráněné metody. Výchozí hodnota je `UseWindowsGroups` a určí, že se při pokusu o přístup k prostředku prohledávají skupiny systému Windows, například správci nebo uživatelé. Můžete také určit, `UseAspNetRoles` že chcete použít vlastního poskytovatele rolí, který je nakonfigurován v rámci \<system.web> elementu, jak je znázorněno v následujícím kódu:

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
  
Následující kód ukazuje, že se `roleProviderName` používá s `principalPermissionMode` atributem:
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

Podrobný příklad použití tohoto prvku konfigurace najdete v tématu [autorizace přístupu k operacím služby](../../../wcf/samples/authorizing-access-to-service-operations.md) a [zásadám autorizace](../../../wcf/samples/authorization-policy.md).
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Autorizace přístupu k operacím služby](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Postupy: Vytvoření vlastního správce autorizace pro službu](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Zásada autorizace](../../../wcf/samples/authorization-policy.md)
