---
title: 'Postupy: Vytvoření vlastní zásady autorizace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 5d5268cd2171bdccc3885cd599fdc8c277e61aa4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795712"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Postupy: Vytvoření vlastní zásady autorizace
Infrastruktura modelu identity ve službě Windows Communication Foundation (WCF) podporuje autorizační model založený na deklaracích identity. Deklarace identity se extrahují z tokenů, volitelně se zpracovávají pomocí vlastních zásad autorizace, a <xref:System.IdentityModel.Policy.AuthorizationContext> pak se umístí do služby, která se pak dá prozkoumat, aby se mohla ověřit autorizační rozhodnutí. Vlastní zásady se dají použít k transformaci deklarací z příchozích tokenů na deklarace identity, které aplikace očekává. Tímto způsobem lze vrstvu aplikace izolované z podrobností o rozdílných deklaracích, které jsou obsluhovány různými typy tokenů, které WCF podporuje. V tomto tématu se dozvíte, jak implementovat vlastní zásady autorizace a jak tyto zásady přidat do kolekce zásad používané službou.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Implementace vlastních zásad autorizace  
  
1. Definujte novou třídu, která je odvozena <xref:System.IdentityModel.Policy.IAuthorizationPolicy>z.  
  
2. Implementujte vlastnost jen <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> pro čtení vygenerováním jedinečného řetězce v konstruktoru pro třídu a vrácením tohoto řetězce vždy, když je přístup k vlastnosti.  
  
3. Implementujte vlastnost <xref:System.IdentityModel.Claims.ClaimSet> , která <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> je jen pro čtení, vrácením reprezentujícího vystavitele zásady. Může to být `ClaimSet` , který představuje aplikaci nebo `ClaimSet` integrovanou `ClaimSet` (například vrácená statickou <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastností.  
  
4. Implementujte <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metodu, jak je popsáno v následujícím postupu.  
  
### <a name="to-implement-the-evaluate-method"></a>Implementace metody Evaluate  
  
1. Do této metody jsou předány dva parametry: instance <xref:System.IdentityModel.Policy.EvaluationContext> třídy a odkaz na objekt.  
  
2. Pokud vlastní zásady autorizace přidávají <xref:System.IdentityModel.Claims.ClaimSet> instance bez ohledu na aktuální obsah rozhraní <xref:System.IdentityModel.Policy.EvaluationContext>, pak je <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> přidejte `ClaimSet` voláním metody a návratem `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metody. Při `true` návratu se znamená, že autorizační infrastruktura vykonala svoji práci a není nutné ji volat znovu.  
  
3. Pokud vlastní zásady autorizace přidávají sady deklarací identity jenom v případě `EvaluationContext`, že některé deklarace identity už v portálu existují, pak tyto deklarace `ClaimSet` vyhledáte kontrolou instancí <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> vrácených vlastností. Pokud jsou deklarace identity k dispozici, přidejte nové sady deklarací voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metody a, pokud žádné další sady deklarací nechcete přidat, vraťte `true`se, což znamená, že autorizační infrastruktura dokončila svoji práci. Pokud nejsou deklarace identity k dispozici, `false`vraťte se, aby se zásady autorizace znovu vyvolaly, pokud jiné zásady autorizace přidají `EvaluationContext`do. další sady deklarací.  
  
4. V složitějších scénářích zpracování se druhý parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody používá k uložení proměnné stavu, která se během každého následného volání <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metody vrátí do metody pro určité vyhodnocení.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Určení vlastních zásad autorizace prostřednictvím konfigurace  
  
1. Zadejte typ vlastní zásady autorizace `policyType` v atributu `add` v `authorizationPolicies` `serviceAuthorization` elementu elementu v elementu.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>  
            <add policyType="Samples.MyAuthorizationPolicy" />  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Určení vlastních zásad autorizace prostřednictvím kódu  
  
1. <xref:System.Collections.Generic.List%601> Vytvořte .<xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
  
2. Vytvořte instanci vlastních zásad autorizace.  
  
3. Přidejte do seznamu instanci zásady autorizace.  
  
4. Opakujte kroky 2 a 3 pro každou vlastní zásadu autorizace.  
  
5. Přiřaďte k <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> vlastnosti verzi seznamu určenou jen pro čtení.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kompletní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementaci.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Postupy: Porovnat deklarace identity](how-to-compare-claims.md)
- [Postupy: Vytvoření vlastního Správce autorizací pro službu](how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Zásady autorizace](../samples/authorization-policy.md)
