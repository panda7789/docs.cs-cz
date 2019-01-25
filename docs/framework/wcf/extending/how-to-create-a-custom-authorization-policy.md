---
title: 'Postupy: Vytvoření vlastní zásady autorizace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: ba5d8d02d0c8d5993e1b072298aadcaa5fe0fe35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705901"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>Postupy: Vytvoření vlastní zásady autorizace
Infrastruktura modelu Identity ve Windows Communication Foundation (WCF) podporuje model založený na deklaraci identity autorizace. Extrahuje z tokenů, volitelně zpracovává vlastní zásady autorizace a pak umístit do deklarace identity <xref:System.IdentityModel.Policy.AuthorizationContext> , pak se dají prozkoumat pro autorizační rozhodnutí. Vlastní zásady je možné získat deklarace identity z příchozí tokeny deklarací, aplikací. Tímto způsobem může být izolované aplikační vrstvu z podrobností na různé deklarace obsluhuje různé typy tokenů, které podporuje WCF. Toto téma ukazuje, jak implementovat vlastní zásady autorizace a tom, jak přidat tuto zásadu do kolekce zásady používané službou.  
  
### <a name="to-implement-a-custom-authorization-policy"></a>Chcete-li implementovat vlastní zásady autorizace  
  
1.  Definovat novou třídu, která je odvozena z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Implementovat jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> vlastnost generování jedinečného řetězce v konstruktoru pro třídu a vrácení tohoto řetězce při každém přístupu k vlastnosti.  
  
3.  Implementovat jen pro čtení <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> vlastnost tak, že vrací <xref:System.IdentityModel.Claims.ClaimSet> , která představuje zásad vydavatele. Může se jednat `ClaimSet` integrovaná nebo aplikace, která představuje `ClaimSet` (například `ClaimSet` vrácené statickou <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastnost.  
  
4.  Implementace <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> způsob, jak je popsáno v následujícím postupu.  
  
### <a name="to-implement-the-evaluate-method"></a>Chcete-li implementovat metodu vyhodnotit  
  
1.  Dva parametry jsou předány do této metody: instance <xref:System.IdentityModel.Policy.EvaluationContext> třídy a odkaz na objekt.  
  
2.  Pokud přidá vlastní zásady autorizace <xref:System.IdentityModel.Claims.ClaimSet> instance bez ohledu na aktuální obsah <xref:System.IdentityModel.Policy.EvaluationContext>, pak přidejte `ClaimSet` voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metodu a vrátí `true` z <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metoda. Vrací `true` označuje infrastruktury autorizace, zásady autorizace se provádí svou práci a není potřeba ji vyvolat znovu.  
  
3.  Pokud zásady autorizace pro vlastní přidá sady deklarací jenom v případě, že jsou již přítomny v určité deklarace identity `EvaluationContext`, vyhledejte tyto deklarace identit tím, že kontroluje `ClaimSet` instancí vrácených <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> vlastnost. Pokud deklarace identity jsou k dispozici, přidejte novou deklaraci nastaví voláním <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> metoda a, pokud žádné další deklarace identity sady mají být přidána, návratový `true`, označující infrastrukturu ověření, že zásady autorizace dokončí svou práci. Pokud deklarace identity nejsou k dispozici, vrátí `false`, označující, že by měla být zásady autorizace volána znovu Pokud jiné zásady autorizace přidat další deklarace identity, které mají `EvaluationContext`.  
  
4.  Ve složitějších scénářích zpracování, druhý parametr <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metoda se používá k uložení proměnné stavu, který infrastruktury autorizace předá zpět při každé následné volání <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> metodu pro konkrétní hodnocení.  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>Chcete-li určit vlastní zásady autorizace prostřednictvím konfigurace  
  
1.  Zadejte typ zásad autorizace v `policyType` atribut `add` element v `authorizationPolicies` prvek v `serviceAuthorization` elementu.  
  
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
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>Chcete-li určit vlastní zásady autorizace prostřednictvím kódu.  
  
1.  Vytvoření <xref:System.Collections.Generic.List%601> z <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Vytvoření instance zásad autorizace.  
  
3.  Přidejte do seznamu instance zásad autorizace.  
  
4.  Zopakujte kroky 2 a 3 pro každou zásadu autorizace.  
  
5.  Přiřadit verze jen pro čtení seznamu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> vlastnost.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kompletní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> implementace.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Postupy: Porovnání deklarací](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [Postupy: Vytvoření vlastního Správce autorizací pro službu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Zásady autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md)
