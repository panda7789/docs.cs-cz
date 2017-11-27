---
title: "Postupy: Vytvoření vlastního správce autorizací pro službu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b8d934509940bf712ccb7463156c88540027407
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Postupy: Vytvoření vlastního správce autorizací pro službu
Infrastruktura Identity modelu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podporuje model extensible autorizace založené na deklaracích identity. Deklarace identity jsou extrahovány z tokenů a volitelně zpracovává zásady autorizace a pak umístit do <xref:System.IdentityModel.Policy.AuthorizationContext>. Správce autorizací prozkoumá deklarací identity ve <xref:System.IdentityModel.Policy.AuthorizationContext> pro autorizační rozhodnutí.  
  
 Ve výchozím nastavení, jsou provedené rozhodnutí o autorizaci <xref:System.ServiceModel.ServiceAuthorizationManager> třída; ale tato rozhodnutí mohou být přepsány vytvoření vlastní ověření správce. Vytvořit vlastní autorizace správci, vytvořte třídu, která je odvozena z <xref:System.ServiceModel.ServiceAuthorizationManager> a implementovat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda. Rozhodnutí o autorizaci, které jsou vytvářeny v <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda, která vrátí `true` když je přístup povolen a `false` když byl odepřen přístup.  
  
 Pokud rozhodnutí o autorizaci závisí na obsahu textu zprávy, použijte <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda.  
  
 Kvůli problémům s výkonem Pokud je to možné jste měli změnit návrh aplikace tak, aby rozhodnutí o autorizaci nevyžaduje přístup k tělo zprávy.  
  
 Registrace Správce autorizace pro službu lze provést v kódu nebo konfigurace.  
  
### <a name="to-create-a-custom-authorization-manager"></a>Chcete-li vytvořit vlastní autorizace manager  
  
1.  Odvození třídy z <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  Přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metoda.  
  
     Použití <xref:System.ServiceModel.OperationContext> předá do <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metoda pro autorizační rozhodnutí.  
  
     Následující příklad kódu používá <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metody k vyhledání vlastních deklarací identity `http://www.contoso.com/claims/allowedoperation` aby rozhodnutí o autorizaci.  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>K registraci manažera autorizace pomocí kódu  
  
1.  Vytvořte instanci vlastní autorizace správce a přiřaďte ho do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> vlastnost.  
  
     <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Lze přistupovat pomocí <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> vlastnost.  
  
     Následující kód například registrů `MyServiceAuthorizationManager` správce vlastní ověřování.  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>K registraci manažera autorizace pomocí konfigurace  
  
1.  Otevření konfiguračního souboru pro službu.  
  
2.  Přidat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
     K [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), přidejte `serviceAuthorizationManagerType` atribut a jeho hodnotu nastavte typ, který představuje správce autorizace.  
  
3.  Přidejte vazbu, které slouží k zabezpečení komunikace mezi klientem a službou.  
  
     Vazba, která je zvolen pro tuto komunikaci určuje deklarace identity, které jsou přidány do <xref:System.IdentityModel.Policy.AuthorizationContext>, který vlastní autorizace manager používá pro autorizační rozhodnutí. Další podrobnosti o vazby poskytované systémem najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
4.  Přidružení chování pro koncový bod služby přidáním [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu a nastavte hodnotu `behaviorConfiguration` hodnota název atributu pro atribut [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.  
  
     Další informace o konfiguraci koncového bodu služby najdete v tématu [postupy: vytvoření koncového bodu služby v konfiguraci](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
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
    >  Všimněte si, že pokud zadáte Třída serviceAuthorizationManagerType, řetězec musí obsahovat plně kvalifikovaného názvu. čárku a název sestavení, ve kterém je definovaný typ. Pokud se název sestavení, se pokusí načíst typ z System.ServiceModel.dll WCF.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje základní implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídu, která zahrnuje přepsání <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metoda. Prozkoumá ukázkový kód <xref:System.IdentityModel.Policy.AuthorizationContext> vlastní deklarace identity a vrátí `true` když prostředek pro tuto vlastní deklarace identity odpovídá hodnotě akce z <xref:System.ServiceModel.OperationContext>. Pro podrobnější implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídy najdete v tématu [zásad autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Zásady autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [Zásady autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md)
