---
title: 'Postupy: Vytvoření vlastní zásady autorizace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 0bacf874e09aca82b2f2685a146612cdef0673db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Postupy: Vytvoření vlastní zásady autorizace
Infrastruktura modelu Identity ve Windows Communication Foundation (WCF) podporuje ověřování na základě deklarace identity na modelu. Deklarace identity jsou extrahovány z tokenů, volitelně zpracovává vlastní zásady autorizace a pak umístit do <xref:System.IdentityModel.Policy.AuthorizationContext> , pak může být prověřen pro autorizační rozhodnutí. Vlastní zásadu lze použít na transformaci deklarací od příchozí tokeny do očekávaného aplikaci deklarací identity. Tímto způsobem může být aplikační vrstvu izolované od podrobnosti o různé deklarace obsloužených různé typy tokenů, které podporuje WCF. Toto téma ukazuje, jak implementovat vlastní zásady autorizace a postup přidání ke kolekci zásady, které používá služba pro tuto zásadu.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Chcete-li implementovat vlastní zásady autorizace  
  
1.  Zadejte novou třídu odvozenou od <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Implementace jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> vlastnost generování jedinečného řetězce v konstruktoru pro třídu a vrácení tento řetězec je o přístup k vlastnosti.  
  
3.  Implementace jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> vlastnost vrácením <xref:System.IdentityModel.Claims.ClaimSet> představující vystavitele zásad. To může být `ClaimSet` nebo integrované aplikace, která představuje `ClaimSet` (například `ClaimSet` vrácený statických <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastnost.  
  
4.  Implementace <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda, jak je popsáno v následujícím postupu.  
  
### <a name="to-implement-the-evaluate-method"></a>Chcete-li implementovat metodu hodnocení  
  
1.  Jsou dva parametry předané této metodě: instance <xref:System.IdentityModel.Policy.EvaluationContext> třídy a odkaz na objekt.  
  
2.  Pokud zásady autorizace pro vlastní přidá <xref:System.IdentityModel.Claims.ClaimSet> instance bez ohledu na aktuální obsah <xref:System.IdentityModel.Policy.EvaluationContext>, poté přidat každý `ClaimSet` voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metoda a vraťte se `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metoda. Vrácení `true` označuje infrastruktury autorizace, že zásady autorizace byla provedena svou práci a nemusí být volán znovu.  
  
3.  Pokud zásady autorizace pro vlastní přidá sad deklarací identit jenom v případě, že jsou již přítomny v určité deklarace identity `EvaluationContext`, vyhledejte těchto deklarací identity tak, že prověří `ClaimSet` instancí vrácených funkcí <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> vlastnost. Pokud jsou v něm deklarace identity, přidejte novou deklaraci nastaví voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metoda a, pokud žádné další deklarace identity sady mají být přidána, návratový `true`, naznačuje infrastruktury autorizace, zásady autorizace byla dokončena svou práci. Pokud deklarace identity nejsou, vrátí `false`, indikující, že zásady autorizace by se měla volat znovu Pokud jiné zásady autorizace přidat více deklarací identity, které mají `EvaluationContext`.  
  
4.  Ve složitějších scénářích zpracování, druhý parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda se používá k ukládání stavu proměnné, která infrastruktury autorizace předá zpět při každém následných volání <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda konkrétní zkušební verze.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Chcete-li určit vlastní zásady autorizace prostřednictvím konfigurace  
  
1.  Zadejte typ zásad autorizace v `policyType` atribut `add` element v `authorizationPolicies` element v `serviceAuthorization` elementu.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>         
            <add policyType="Samples.MyAuthorizationPolicy"  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Chcete-li určit vlastní zásady autorizace prostřednictvím kódu  
  
1.  Vytvoření <xref:System.Collections.Generic.List%601> z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Vytvoření instance zásad autorizace.  
  
3.  Přidejte do seznamu instance zásad autorizace.  
  
4.  Opakujte kroky 2 a 3 pro každý vlastní zásady autorizace.  
  
5.  Přiřadit pouze ke čtení verzi v seznamu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> vlastnost.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplná <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementace.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Postupy: Porovnávání deklarací identity](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [Postupy: Vytvoření vlastního správce autorizace pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Zásady autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md)
