---
title: 'Postupy: Vytvoření vlastního správce autorizací pro službu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: 6a168902b79bd27345c9d9e2371947cc9d64233c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156491"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Postupy: Vytvoření vlastního správce autorizací pro službu
Infrastruktura modelu identit ve Windows Communication Foundation (WCF) podporuje model extensible autorizace na základě rolí. Extrahuje z tokenů a volitelně zpracování pomocí zásad autorizace a pak umístit do deklarace identity <xref:System.IdentityModel.Policy.AuthorizationContext>. Správce autorizací prozkoumá deklarace identity v <xref:System.IdentityModel.Policy.AuthorizationContext> pro autorizační rozhodnutí.  
  
 Ve výchozím nastavení, jsou prováděny rozhodování o autorizaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídy, ale tato rozhodnutí lze přepsat tak, že vytvoříte vlastní autorizace správce. Chcete-li vytvořit vlastní autorizace správce, vytvořit třídu, která je odvozena z <xref:System.ServiceModel.ServiceAuthorizationManager> a implementovat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Rozhodování o autorizaci se provádí v <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodu, která vrací `true` když se udělí přístup k a `false` kdy byl odepřen přístup.  
  
 Pokud je rozhodnutí o autorizaci závisí na obsahu těla zprávy, použijte <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metody.  
  
 Kvůli problémům s výkonem Pokud je to možné byste měli přepracovat vaší aplikace tak, aby rozhodnutí o autorizaci nevyžaduje přístup k textu zprávy.  
  
 V kódu nebo konfigurace lze provést registraci Správce autorizace pro službu.  
  
### <a name="to-create-a-custom-authorization-manager"></a>Chcete-li vytvořit vlastní autorizace správce  
  
1.  Odvodit třídu z <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  Přepsat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.  
  
     Použití <xref:System.ServiceModel.OperationContext> , který je předán <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metodu pro autorizační rozhodnutí.  
  
     Následující příklad kódu používá <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metody k vyhledání vlastních deklarací identity `http://www.contoso.com/claims/allowedoperation` provádět rozhodnutí o autorizaci.  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>Zaregistrovat vlastní autorizace Manageru pomocí kódu  
  
1.  Vytvoření instance vlastní autorizace správce a přiřaďte ho k <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> vlastnost.  
  
     <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Lze přistupovat pomocí <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> vlastnost.  
  
     Následující kód například registrů `MyServiceAuthorizationManager` Správce autorizace.  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Zaregistrovat vlastní autorizace Manageru pomocí konfigurace  
  
1.  Otevřete konfigurační soubor služby.  
  
2.  Přidat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
     K [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), přidejte `serviceAuthorizationManagerType` atribut a nastavte její hodnotu na typ, který představuje správce autorizace.  
  
3.  Přidáte vazbu, která zajišťuje zabezpečení komunikace mezi klientem a službou.  
  
     Vazby, který je vybrán pro tuto komunikaci určuje deklarace identity, které jsou přidány do <xref:System.IdentityModel.Policy.AuthorizationContext>, který používá správce autorizace pro autorizační rozhodnutí. Další podrobnosti o vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
4.  Přidružit chování koncového bodu služby, tak, že přidáte [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element a nastavte hodnotu `behaviorConfiguration` atributu na hodnotu atributu název [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.  
  
     Další informace o konfiguraci koncového bodu služby, najdete v části [jak: Vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
     Následující ukázkový kód registruje Správce autorizace `Samples.MyServiceAuthorizationManager`.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  Všimněte si, že při zadání Třída serviceAuthorizationManagerType řetězec musí obsahovat plně kvalifikovaného názvu. čárku a název sestavení, ve kterém je typ definován. Pokud vynecháte název sestavení, se pokusí načíst typ z System.ServiceModel.dll WCF.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje základní implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídu, která zahrnuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metody. Příklad kódu zkontroluje <xref:System.IdentityModel.Policy.AuthorizationContext> vlastní deklarace identity a vrátí `true` při prostředků pro tuto vlastní deklarace identity odpovídá hodnotě akce z <xref:System.ServiceModel.OperationContext>. Pro více úplnou implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> najdete v tématu [zásad autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Zásada autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md)
